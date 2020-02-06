# Automated download from Pluralsight with `pluradl.py`

You can download whole courses from a number of tutorial sites with the CLI tool `youtube-dl`, however, in this Git I have provided an Python script, `pluradl.py`,  for automated download of a **whole sequence of Pluralsight courses** (of your choice) at once using `youtube-dl` as a subprocess. Below I give an example of how to use the `pluradl.py` script with a Pluralsight account to get videos from an arbitrary large list of courses at their site.

**You can get a free 1 month trial to Pluralsight by signing up for free to [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/)**

### Requirements
* [Python 3](https://www.python.org/) (as system default)
* [youtube-dl](https://ytdl-org.github.io/youtube-dl/)

**Note:** The system default Python version need to be 3.2+ for this method to work out. Especially macOS users will experience HTTP 403 error when loggin due to the system default version of 2.7.

## Installation of youtube-dl

##### For **macOS/UNIX**
With [`apt-get`](https://packages.ubuntu.com/eoan/youtube-dl)  in Ubuntu:

```bash
sudo apt-get install youtube-dl
```

With [`brew`](https://brew.sh/)  for macOS:

```bash
brew install youtube-dl
```

With [`npm`](https://www.npmjs.com/):

```bash
npm install youtube-dl
```

With [`pacman`](https://www.archlinux.org/packages/community/any/youtube-dl/) in Arch Linux

```
sudo pacman -S youtube-dl
```

Or you can use `curl`/`wget`:

```bash
sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
```
```bash
sudo wget https://yt-dl.org/downloads/latest/youtube-dl -O /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
```

##### For Windows

Just download the `exe`-file from the link below and [put the `exe` in your _PATH_](https://gist.github.com/jesperorb/836cb398e4bb8dc149902d68d3711295).

Or download with `npm` like above.

[Source: youtube-dl download](https://ytdl-org.github.io/youtube-dl/download.html)

## Usage

### Download from **Pluralsight** with `pluradl.py`
After installation of youtube-dl (thus is avaiable in the environment) make sure that [`courselist.txt`](https://github.com/rojter-tech/pluradl.py/blob/master/courselist.txt) is in the same directory as [`pluradl.py`](https://github.com/rojter-tech/pluradl.py/blob/master/pluradl.py) with the course ID's of your choice **listed row by row**. Example files and scripts is provided in [Scripts](https://github.com/rojter-tech/pluradl.py/tree/master/Scripts). The course ID can be found via the course URL from the Pluralsight website, e.g [https://app.pluralsight.com/library/courses/c-sharp-fundamentals-with-visual-studio-2015/table-of-contents](https://app.pluralsight.com/library/courses/c-sharp-fundamentals-with-visual-studio-2015/table-of-contents) where the ID is "c-sharp-fundamentals-with-visual-studio-2015".

Run the script in your terminal to download all the videos from all the courses in [`courselist.txt`](https://github.com/rojter-tech/pluradl.py/blob/master/courselist.txt). The videos will be automatically placed in course specific folders and named by playlist order number. Substitute the example credentials with your own and supply courselist.txt with your desired courses ...

```bash
$ python pluradl.py
Enter you Pluralsight credentials
Enter username: youremail@example.com
Enter password (will not be displayed)
: yourPassword
```

... with `courselist.txt` available at the same path

courselist.txt
```notepad
c-sharp-fundamentals-with-visual-studio-2015
csharp-nulls-working
csharp-best-practices-collections-generics
object-oriented-programming-fundamentals-csharp
using-csharp-interfaces
linq-fundamentals-csharp-6
.
.
.
```

For automation, the script can be executed along with Pluralsight username and password

```bash
python pluradl.py "myusername@mymail.com" "myPassword"
```

### Example output

![Directory tree of pluradl.py root](https://raw.githubusercontent.com/rojter-tech/pluradl.py/master/Image/example_output_tree.png)

# IMPORTANT
The argument `SLEEP_INTERVAL = 150` parameter used in the [`pluradl.py`](https://github.com/rojter-tech/pluradl.py/blob/master/pluradl.py) script is important. It means that the program will wait at least 150s (2.5 minutes) before it downloads the next video. If you don't use this flag _Pluralsight_ will ban you because you are doing too many requests under a short period of time.

>We have blocked your account because our security systems have flagged your Pluralsight account for an unusual amount activity. This does mean a high volume of requests that are in the realm of a request every 10-30 seconds for a prolonged period of time. Please note that this high volume of activity is in violation of our terms of service [https://www.pluralsight.com/terms].
