---
title: "Problem with installing package"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by samitekken on 2012-02-10
Hi everybody.

i have Ubuntu 11.10 and i'm trying to learn how to install a package, which is in this case "MPlayer-1.0rc4.tar.bz2"
I know you'd say use ubuntu software center to get Mplayer, but it's not about Mplayer, and as i said, it's about learning how to install a package using the terminal, so please help me out.

I followed these steps :
To exctract the file :
```
tar xjfv MPlayer-1.0rc4.tar.bz2
```

so far, it was ok, files were exctracted to a folder named MPlayer-1.0rc4

then when i tried to use the following command:
```
./configure
```

```
root@samitekken-P31-ES3G:/home/samitekken/Downloads# ./configure
``` i got this error message :

```
bash: ./configure: No such file or directory
```

And About The README File that came with the package :

```

______________________
STEP0: Getting MPlayer
~~~~~~~~~~~~~~~~~~~~~~

Official releases and Subversion snapshots, as well as binary codec packages
and a number of different skins for the GUI are available from the download
section of our homepage at

  http://www.mplayerhq.hu/dload.html

MPlayer has builtin support for the most common audio and video formats. For a
few formats no native decoder exists and external binary codecs are required
to handle them. Examples are newer RealVideo variants and a variety of rare
formats. However, binary codecs are NOT required in this day and age, they are
strictly optional.

Please note that binary codecs only work on the processor architecture they
were compiled for. Choose the correct package for your processor. No other
package is necessary.

The GUI needs at least one skin and codec packages add support for some more
video and audio formats. MPlayer does not come with any of these by default,
you have to download and install them separately.

You can also get MPlayer via Subversion. Issue the following commands to get
the latest sources:

  svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

A directory named 'mplayer' will be created. It will include all necessary
FFmpeg libraries, you don't need to get them separately as was the case in
the past. You can later update your sources by saying

  svn update

from within that directory.


_______________________________
STEP1: Installing Binary Codecs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unpack the codecs archives and put the contents in a directory where MPlayer
will find them. The default directory is /usr/local/lib/codecs/ (it used to be
/usr/local/lib/win32 in the past, this also works) but you can change that to
something else by passing the '--codecsdir' option to './configure'.


__________________________
STEP2: Configuring MPlayer
~~~~~~~~~~~~~~~~~~~~~~~~~~

MPlayer can be adapted to all kinds of needs and hardware environments. Run

  ./configure

to configure MPlayer with the default options. GUI support has to be enabled
separately, run

  ./configure --enable-gui

if you want to use the GUI.

If something does not work as expected, try

  ./configure --help

to see the available options and select what you need.

The configure script prints a summary of enabled and disabled options. If you
have something installed that configure fails to detect, check the file
config.log for errors and reasons for the failure. Repeat this step until
you are satisfied with the enabled feature set.


________________________
STEP3: Compiling MPlayer
~~~~~~~~~~~~~~~~~~~~~~~~

Now you can start the compilation by typing

  make

You can install MPlayer with

  make install

provided that you have write permission in the installation directory.

If all went well, you can run MPlayer by typing 'mplayer'. A help screen with a
summary of the most common options and keyboard shortcuts should be displayed.

If you get 'unable to load shared library' or similar errors, run
'ldd ./mplayer' to check which libraries fail and go back to STEP 3 to fix it.
Sometimes running 'ldconfig' is enough to fix the problem.

______________________________________
STEP4: Choose an onscreen display font
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can use any TrueType font installed on your system. Just pass '-font
/path/to/font.ttf' on the command line or add 'font=/path/to/font.ttf' to
your configuration file. The manual page has more details. Alternatively
you can create a symbolic link from either ~/.mplayer/subfont.ttf or
/usr/local/share/mplayer/subfont.ttf to your TrueType font.


____________________________
STEP5: Installing a GUI skin
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unpack the archive and put the contents in /usr/local/share/mplayer/skins/ or
~/.mplayer/skins/. MPlayer will use the skin in the subdirectory named default
of /usr/local/share/mplayer/skins/ or ~/.mplayer/skins/ unless told otherwise
via the '-skin' switch. You should therefore rename your skin subdirectory or
make a suitable symbolic link.


__________________
STEP6: Let's play!
~~~~~~~~~~~~~~~~~~

That's it for the moment. To start playing movies, open a command line and try

  mplayer <moviefile>

or for the GUI

  gmplayer <moviefile>

gmplayer is a symbolic link to mplayer created by 'make install'.
Without <moviefile>, gmplayer will start with the GUI filepicker.

To play a VCD track or a DVD title, try:

  mplayer vcd://2 -cdrom-device /dev/hdc
  mplayer dvd://1 -alang en -slang hu -dvd-device /dev/hdd

See 'mplayer -help' and 'man mplayer' for further options.

'mplayer -vo help' will show you the available video output drivers. Experiment
with the '-vo' switch to see which one gives you the best performance.
If you get jerky playback or no sound, experiment with the '-ao' switch (see
'-ao help') to choose between different audio drivers. Note that jerky playback
is caused by buggy audio drivers or a slow processor and video card. With a
good audio and video driver combination, one can play DVDs and 720x576 MPEG-4
files smoothly on a Celeron 366. Slower systems may need the '-framedrop'
option.

Questions you may have are probably answered in the rest of the documentation.
The places to start reading are the man page, DOCS/HTML/en/index.html and
DOCS/HTML/en/faq.html. If you find a bug, please report it, but first read
DOCS/HTML/en/bugreports.html.
```

So, Please Help Me get this To Work.

---

### Post by nothingspecial on 2012-02-10
You are not in the extracted mplayer directory. You are in your Downloads directory.

---

### Post by samitekken on 2012-02-10
> **nothingspecial said:**
> You are not in the extracted mplayer directory. You are in your Downloads directory.
yes i thought about that, but when i tried to get in the directory of mplayer, i get the same message
```
bash: cd/home/samitekken/downloads/MPlayer-1.0rc4: No such file or directory
```
even the file directory is there, it exist, i excracted it, and i can see it.

---

### Post by cortman on 2012-02-10
> **samitekken said:**
> yes i thought about that, but when i tried to get in the directory of mplayer, i get the same message
```
bash: cd/home/samitekken/downloads/MPlayer-1.0rc4: No such file or directory
```
even the file directory is there, it exist, i excracted it, and i can see it.

The "downloads" folder name is "Downloads"- capital D. The shell is case-sensitive.

```
cd /home/samitekken/Downloads/MPlayer-1.0rc4
```

Also don't know if it's a typo or not, but there was no space between "cd" and the path.

---

### Post by samitekken on 2012-02-10
it's ok now, it was my mistake, i was not doing it right.
when i tried to get into the directory of Mplayer i used ```
cd /MPlayer-1.0rc4
```
i figured out i shouldn't put "/"
now it worked
Thank you.

---

### Post by samitekken on 2012-02-10
> **cortman said:**
> The "downloads" folder name is "Downloads"- capital D. The shell is case-sensitive.

```
cd /home/samitekken/Downloads/MPlayer-1.0rc4
```Also don't know if it's a typo or not, but there was no space between "cd" and the path.

yes, i used capital "D"
and all worked fine
Thanks cortman.

---

