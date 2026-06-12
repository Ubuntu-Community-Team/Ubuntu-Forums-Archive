---
title: "GNOME Shell Installation on Ubuntu 10.10 Maverick"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2010-10-11
Let this be the thread for GNOME Shell Installation stuff on Maverick. I update this first post whenever there's something noteworthy about the subject.

This thread is only for discussing GNOME Shell installation on Maverick.

See the [GNOME Shell Testing thread]("http://ubuntuforums.org/showthread.php?t=1476241") on Meerkat Testing and Discussion forum for your reference.

**Installing GNOME Shell from the Ubuntu Repository**

An easy way of installing GNOME Shell is by using the version in the repository. However, this is relatively outdated. To do this, simply install the gnome-shell package from the Ubuntu Software Center.

**Installing GNOME Shell from Source**

The following steps are expected to work when there's no existing ~/gnome-shell folder
[LIST=1]
[*][Remove La Files]("http://live.gnome.org/GnomeShell/RemovingLaFiles")
[*]Install Dependencies
```
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libpam-dev libgcrypt-dev libtasn1-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev libxklavier16 libxklavier-dev xserver-xephyr python-dev libpulse-dev libjasper-dev jhbuild libgtop2-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libusb-1.0-0-dev gperf
```
[*][Build from Source]("http://live.gnome.org/GnomeShell/#Building")
[/LIST]


**Running GNOME Shell**

If you built it from source, follow [these instructions]("http://live.gnome.org/GnomeShell#Running")

If you installed it from a repository, just run ```
gnome-shell --replace
```

---

### Post by Riffer on 2010-10-11
I really like Gnome Shell but a few things are just driving me up the wall.  For one can you (and how do you) change the side panel (?) in the Activity window?  I would like to add things to the app list (add system apps).  It also would be nice to have a Favorite section to the side panel to save a couple of clicks.  

I also find it frustrating that while in the Activity window that I can't open a new desktop(?) and select it to open a new app, without it going to full size and I have to go back to the Activity window to add the app.

Is there some way or plans afoot to have tabs or some sort of indicator on the top panel for whats in the different desktops and to be able to click that tab to switch.  Yes I know there are keyboard shortcuts to switch windows but it would be nice to see what are in the other windows.

Sorry if I didn't get the terminology correct.  And if these issues have been discussed before I can't find it, I've googled for hours.  I really do like the new interface.  It seems to me to be very intuitive (to me anyway) and I suspect as it becomes mature and others start to add to it this shell will become awesome.

---

### Post by omskates on 2010-10-13
Wersdaluv, Thanks for the tutorial but if I want to just try the snapshot can I not just add the repo ```
http://ppa.launchpad.net/ricotz/staging/ubuntu maverick main  
```
and
 ```
sudo apt-get update 
```

then

 ```
sudo apt-get install gnome-shell 
```

and

 ```
gnome-shell --replace 
```

then change it as my default WM in /desktop/gnome/session/required_components/windowmanager ??

So if I were to rather follow your build tutorial instead I'll have Gnome Shell permanently which will update with development, am I correct?  Thanks in advance:)

---

### Post by omskates on 2010-10-14
After executing ```
/bin/bash gnome-shell-build-setup.sh 
``` I have Success in installing jhbuild and writing ~/.jhbuildrc but Terminal says "PATH does not contain /home/****/bin" (where **** is my username), "it is recommended that you add that."  Should I move ~/.jhbuildrc to that home path?

After executing ```
jhbuild build
``` Terminal complained that I needed to install jhbuild first LOL :) So installed that and continued with the build process.

Error during phase build of gtk3 so will try to rebuild later.

---

### Post by omskates on 2010-10-14
OK, so I went ahead and opened another terminal and did a ```
jhbuild build gtk3
``` which succeeded.  Returning to the original terminal I chose to ignore the Error and continue.  The build was successful and I have Gnome Shell running:):)

---

### Post by f_padia on 2010-10-14
Ok i've been trying to follow the instructions in post #1 and it kept coming up with errors at a couple of stages, so I tried ignoring the errors and 'giving up on module'. But then the Install step wouldnt work.

So then I tried the jhbuild build gtk3 step suggested above and I still get an error:

/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.20.51-system.20100908 internal error, aborting at ../../bfd/merge.c line 876 in _bfd_merged_section_offset

/usr/bin/ld: Please report this bug.

collect2: ld returned 1 exit status
make[4]: *** [libgdk-x11-3.0.la] Error 1
make[4]: Leaving directory `/home/faheem/gnome-shell/source/gtk3/gdk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/faheem/gnome-shell/source/gtk3/gdk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/faheem/gnome-shell/source/gtk3/gdk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/faheem/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/8]
any ideas? :(

---

### Post by f_padia on 2010-10-14
ok tried running jhbuild build gtk3 again and it worked!

now i try to run make install and that fails! 

make[1]: Entering directory `/home/faheem/gnome-shell/source/gnome-shell/src'
  GEN    stamp-st-marshal.h
/bin/bash: line 2: --prefix=_st_marshal: command not found
make[1]: *** [stamp-st-marshal.h] Error 127
make[1]: Leaving directory `/home/faheem/gnome-shell/source/gnome-shell/src'
make: *** [install-recursive] Error 1

help please.

---

### Post by omskates on 2010-10-14
At the "Build from source" Link posted in post #1 I actually used the instructions for Running as seen there and they worked fine.  They give 3 options, I used the 3rd option to use gnome-shell permanently in my case.

---

### Post by f_padia on 2010-10-14
Thing is i've tried running gnome-shell by installing it from synaptic manager and it keeps crashing then I have to restart X to get back to working OS. thats why I tried to build it from source. So i dont want to run permanently if its going to crash instantly.

---

### Post by omskates on 2010-10-14
OK so in that case after success in building you would: 

>  Running gnome-shell replacing the panel

This approach is best when trying out the GNOME Shell and wanting to see its full potential.

```
cd ~/gnome-shell/source/gnome-shell/src
./gnome-shell --replace
```

When gnome-shell exits (you can kill it with Control-C in the terminal in which you started it), gnome-panel and metacity are restarted. (The script hardcodes /usr/bin/metacity and /usr/bin/gnome-panel, if that doesn't work in your setup, please make the script smarter and submit a patch.) 

I think you could add that in startup scripts.

---

### Post by omskates on 2010-10-14
While running Gnome-Shell next to the Activities button, is the name of the currently used application; well when I'm not running any apps for some reason File-Manager is appearing there, even though I don't have Nautilus open. Since closing apps from that panel feature isn't working "File-Manager" just sits there on the panel looking ugly LOL.

---

### Post by f_padia on 2010-10-15
> **omskates said:**
> OK so in that case after success in building you would: 



I think you could add that in startup scripts.

gnome-shell --replace from alt+F2 crashes the comp. and ./gnome-shell --replace doesnt work... 'No such file or directory'... confused

---

### Post by wersdaluv on 2010-10-17
> **f_padia said:**
> gnome-shell --replace from alt+F2 crashes the comp. and ./gnome-shell --replace doesnt work... 'No such file or directory'... confused
I updated the first post :)

---

### Post by wersdaluv on 2010-10-18
I noticed that the version from the repo is much faster than the one installed from source. Do you also experience this?

---

### Post by XanTrax on 2010-10-19
You should add these following packages to your list of dependencies as the gnome-shell-build-setup.sh script tells you to download them:

```

xserver-xephyr python-dev libjasper-dev

```

As well as 

```

jhbuild

```



> **f_padia said:**
> ok tried running jhbuild build gtk3 again and it worked!

now i try to run make install and that fails! 

make[1]: Entering directory `/home/faheem/gnome-shell/source/gnome-shell/src'
  GEN    stamp-st-marshal.h
/bin/bash: line 2: --prefix=_st_marshal: command not found
make[1]: *** [stamp-st-marshal.h] Error 127
make[1]: Leaving directory `/home/faheem/gnome-shell/source/gnome-shell/src'
make: *** [install-recursive] Error 1

help please.

Why did you run make install?  You shouldnt have even ran configure which leads me to believe you never read the instructions on [http://live.gnome.org/GnomeShell/#Building](http://live.gnome.org/GnomeShell/#Building)

---

### Post by david stevenson on 2010-10-22
I had an error "no package libcanberra"
I installed libcanberra_dev and libcanberra_gtk_dev and it got further.
But now  at:
 CCLD   test-theme
/home/david/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_main_context_invoke'
/home/david/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_signal_accumulator_first_wins'
Looks like I have some more .la files so time to remove them and start again.......

Update - more errors, then gave up at can not find jsapi.h
So deleted all and tried apt-get install gnome-shell
That works and installs 2.31.5 which is not that old.....

---

### Post by wersdaluv on 2010-11-15
updated [first post]("http://ubuntuforums.org/showpost.php?p=9951257&postcount=1") to add new dependencies when building from source

---

### Post by FlyingIsFun1217 on 2010-11-15
I'm also trying to compile, and I'm having no problems whatsoever until I get to [26/28]. The following occurs:

> 
CCLD   gnome-settings-daemon
gnome_settings_daemon-main.o: In function `main':
/home/user/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon/main.c:274: undefined reference to `notify_init'
collect2: ld returned 1 exit status
make[3]: *** [gnome-settings-daemon] Error 1
make[3]: Leaving directory `/home/user/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/user/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/gnome-shell/source/gnome-settings-daemon'
make: *** [all] Error 2
*** Error during phase build of gnome-settings-daemon: ########## Error running make   *** [26/28]


I can't figure this one out; I've deleted the .la files, and cleaned and rebuilt once, but every time I get the same error.

FlyingIsFun1217

---

### Post by arindom on 2010-11-16
> **FlyingIsFun1217 said:**
> I'm also trying to compile, and I'm having no problems whatsoever until I get to [26/28]. The following occurs:



I can't figure this one out; I've deleted the .la files, and cleaned and rebuilt once, but every time I get the same error.

FlyingIsFun1217

Same problem for me too. Got stuck at 26/28. Two days back when I compiled it worked that time. 

Is this due to some dependency issue? May be I am missing something.

---

### Post by amato on 2010-11-16
> **arindom said:**
> Same problem for me too. Got stuck at 26/28. Two days back when I compiled it worked that time. 

Is this due to some dependency issue? May be I am missing something.

me too, any idea to fix-it? :(

---

### Post by wersdaluv on 2010-11-16
**FlyingIsFun1217** and **arindom**
It now requires a newer version of libnotify that's not in the repository.

To install the new version of libnotify, run this
```
cd ~/bin
./jhbuild shell
cd ~/gnome-shell/source
git clone git://git.gnome.org/libnotify
cd ./libnotify
./autogen.sh --prefix $HOME/gnome-shell/install/
make && make install
```

---

### Post by arindom on 2010-11-16
> **wersdaluv said:**
> **FlyingIsFun1217** and **arindom**
It now requires a newer version of libnotify that's not in the repository.

To install the new version of libnotify, run this
```
cd ~/bin
./jhbuild shell
cd ~/gnome-shell/source
git clone git://git.gnome.org/libnotify
cd ./libnotify
./autogen.sh --prefix $HOME/gnome-shell/install/
make && make install
```

Many thanks wersdaluv for your help. Trying this now. Will update here about the result. 

I have to compile it from fresh, because removing the *.la files or simple jhbuild didn't work. Same error reproduced. Even option [6] didn't work.

---

### Post by arindom on 2010-11-16
> **arindom said:**
> Many thanks wersdaluv for your help. Trying this now. Will update here about the result. 

I have to compile it from fresh, because removing the *.la files or simple jhbuild didn't work. Same error reproduced. Even option [6] didn't work.

No, it didn't work for me. After installing libnotify as suggested above, I tried the following :

```

$ rm -rf ~/gnome-shell/install
$ jhbuild build -afc

```

Same Error :
```

~/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon/main.c:274: undefined reference to `notify_init'

```

---

### Post by arindom on 2010-11-16
> **arindom said:**
> No, it didn't work for me. After installing libnotify as suggested above, I tried the following :

```

$ rm -rf ~/gnome-shell/install
$ jhbuild build -afc

```

Same Error :
```

~/gnome-shell/source/gnome-settings-daemon/gnome-settings-daemon/main.c:274: undefined reference to `notify_init'

```

My mistake. It solved the issue now.

Not sure that changing the *make install* in the libnotify install command to *sudo make install* did the trick or not, but after I made the change in another terminal and run option 6, I was able to see the "Success" step.

Thanks again to wersdalu, for helping on this.

---

### Post by kvant on 2010-11-16
My build faled, I've removed the gnome-shell directory.

My question: Did removing la files upset my system in any way or is everything cool concering all my other programs etc.? :)

Thanks!

---

### Post by FlyingIsFun1217 on 2010-11-16
I haven't tried sudo make install, but with the directions given for the new libnotify, I get the same error as arindom described.

FlyingIsFun1217

---

### Post by arindom on 2010-11-16
Although I was able to complete the compilation, I can not run gnome-shell. Here is the error detail :

```

 JS ERROR: !!!   Exception was: Error: Bad method name "Gdk.Window.get_device_position"
    JS ERROR: !!!     lineNumber = '43'
    JS ERROR: !!!     fileName = '/home/arindom/gnome-shell/source/gnome-shell/js/ui/environment.js'
    JS ERROR: !!!     stack = 'Error("Bad method name \"Gdk.Window.get_device_position\"")@:0
_blockMethod("Gdk.Window.get_device_position","global.get_pointer","gjs's handling of Gdk.ModifierType is broken. See bug 597292.")@/home/arindom/gnome-shell/source/gnome-shell/js/ui/environment.js:43
init()@/home/arindom/gnome-shell/source/gnome-shell/js/ui/environment.js:94
start()@/home/arindom/gnome-shell/source/gnome-shell/js/ui/main.js:87
@<main>:1
'
    JS ERROR: !!!     message = 'Bad method name "Gdk.Window.get_device_position"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Bad method name "Gdk.Window.get_device_position"


```

---

### Post by md1512 on 2010-11-16
> **arindom said:**
> Although I was able to complete the compilation, I can not run gnome-shell. Here is the error detail :

```

 JS ERROR: !!!   Exception was: Error: Bad method name "Gdk.Window.get_device_position"
    JS ERROR: !!!     lineNumber = '43'
    JS ERROR: !!!     fileName = '/home/arindom/gnome-shell/source/gnome-shell/js/ui/environment.js'
    JS ERROR: !!!     stack = 'Error("Bad method name \"Gdk.Window.get_device_position\"")@:0
_blockMethod("Gdk.Window.get_device_position","global.get_pointer","gjs's handling of Gdk.ModifierType is broken. See bug 597292.")@/home/arindom/gnome-shell/source/gnome-shell/js/ui/environment.js:43
init()@/home/arindom/gnome-shell/source/gnome-shell/js/ui/environment.js:94
start()@/home/arindom/gnome-shell/source/gnome-shell/js/ui/main.js:87
@<main>:1
'
    JS ERROR: !!!     message = 'Bad method name "Gdk.Window.get_device_position"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Bad method name "Gdk.Window.get_device_position"


```
I have the same problem but on Lucid Lynx

---

### Post by criball on 2010-11-16
Ok, solved it! You must build gtk3

```
jhbuild build gtk3
```

---

### Post by FlyingIsFun1217 on 2010-11-16
Building gtk3 first seems to do the trick for me, although doing the "make install" step from the first post throws another error with an outdated version (I can't remember the package off-hand). Using gnome-shell works just fine though.

FlyingIsFun1217

---

### Post by arindom on 2010-11-16
> **criball said:**
> Ok, solved it! You must build gtk3

```
jhbuild build gtk3
```

Thanks criball for the steps.

It's working for me too.

---

### Post by SAKO2008 on 2010-11-18
I get an error:

```
Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
configure.in:399: warning: macro `AM_PATH_LIBGCRYPT' not found in library
Running autoconf...
configure.in:399: error: possibly undefined macro: AM_PATH_LIBGCRYPT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
*** Error during phase configure of gnome-keyring: ########## Errore nell'eseguire ./autogen.sh --prefix /home/fabio/gnome-shell/install --libdir '/home/fabio/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [29/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to clean
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
scelta: 

```
how can I fix this?

---

### Post by wersdaluv on 2010-11-18
> **wersdaluv said:**
> Let this be the thread for GNOME Shell Installation stuff on Maverick. I update this first post whenever there's something noteworthy about the subject.

This thread is only for discussing GNOME Shell installation on Maverick.

See the [GNOME Shell Testing thread]("http://ubuntuforums.org/showthread.php?t=1476241") on Meerkat Testing and Discussion forum for your reference.

**Installing GNOME Shell from the Ubuntu Repository**

An easy way of installing GNOME Shell is by using the version in the repository. However, this is relatively outdated. To do this, simply install the gnome-shell package from the Ubuntu Software Center.

**Installing GNOME Shell from Source**

The following steps are expected to work when there's no existing ~/gnome-shell folder
[LIST=1]
[*][Remove La Files]("http://live.gnome.org/GnomeShell/RemovingLaFiles")
[*]Install Dependencies
```
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libxklavier libpam-dev libgcrypt-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev
```
[*][Build from Source]("http://live.gnome.org/GnomeShell/#Building")
[/LIST]

**Installing the new UI (only works if you installed from source)**

After installing GNOME Shell on ~/gnome-shell, run these commands:
```
cd ~/gnome-shell/source/gnome-shell
git checkout -b overview-relayout origin/overview-relayout
make install
```

**Running GNOME Shell**

If you built it from source, follow [these instructions]("http://live.gnome.org/GnomeShell#Running")

If you installed it from a repository, just run ```
gnome-shell --replace
```
Updated first post again for new dependencies. Install them if you're getting new errors.

---

### Post by frogknowledge on 2010-11-19
How do you fix this??

I get an error:

Code:
Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
configure.in:399: warning: macro `AM_PATH_LIBGCRYPT' not found in library
Running autoconf...
configure.in:399: error: possibly undefined macro: AM_PATH_LIBGCRYPT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
*** Error during phase configure of gnome-keyring: ########## Errore nell'eseguire ./autogen.sh --prefix /home/fabio/gnome-shell/install --libdir '/home/fabio/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [29/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to clean
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
scelta:
how can I fix this?

---

### Post by wersdaluv on 2010-11-19
> **frogknowledge said:**
> How do you fix this??

I get an error:

Code:
Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
configure.in:399: warning: macro `AM_PATH_LIBGCRYPT' not found in library
Running autoconf...
configure.in:399: error: possibly undefined macro: AM_PATH_LIBGCRYPT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
*** Error during phase configure of gnome-keyring: ########## Errore nell'eseguire ./autogen.sh --prefix /home/fabio/gnome-shell/install --libdir '/home/fabio/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [29/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to clean
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
scelta:
how can I fix this?
Try
```
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libxklavier libpam-dev libgcrypt-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev

```

---

### Post by alphonce on 2010-11-19
> **frogknowledge said:**
> How do you fix this??

I get an error:

Code:
Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
configure.in:399: warning: macro `AM_PATH_LIBGCRYPT' not found in library
Running autoconf...
configure.in:399: error: possibly undefined macro: AM_PATH_LIBGCRYPT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
*** Error during phase configure of gnome-keyring: ########## Errore nell'eseguire ./autogen.sh --prefix /home/fabio/gnome-shell/install --libdir '/home/fabio/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [29/33]

  [1] Rerun phase configure
  [2] Ignore error and continue to clean
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
scelta:
how can I fix this?

I'm getting the same, looking in to it now, post if progress =)

---

### Post by alphonce on 2010-11-19
> **wersdaluv said:**
> Try
```
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libxklavier libpam-dev libgcrypt-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev

```

add libtasn1-dev to that and you're set =)

---

### Post by frogknowledge on 2010-11-19
So I tried the other code WERSDALUV, and this is what I got?


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libpam0g-dev' instead of 'libpam-dev'
Note, selecting 'libgcrypt11-dev' instead of 'libgcrypt-dev'
E: Unable to locate package libxklavier

---

### Post by wersdaluv on 2010-11-19
> **frogknowledge said:**
> So I tried the other code WERSDALUV, and this is what I got?


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libpam0g-dev' instead of 'libpam-dev'
Note, selecting 'libgcrypt11-dev' instead of 'libgcrypt-dev'
E: Unable to locate package libxklavier
I think, it's what **alphonce** said. Also install libtasn1-dev :)

---

### Post by frogknowledge on 2010-11-19
Yea I installed libtasn1-dev no problem got the same error installing. Not sure what I did wrong
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libxklavier libpam-dev libgcrypt-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev

---

### Post by markuskalb on 2010-11-24
> **frogknowledge said:**
> Yea I installed libtasn1-dev no problem got the same error installing. Not sure what I did wrong
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libxklavier libpam-dev libgcrypt-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev

My Ubuntu 10.10 only offers libxklavier16 and libxklavier-dev as possible packages.

---

### Post by markuskalb on 2010-11-24
Hi 

i get the attached error while doing "jhbuild build" the odd part is that the the gtk3+ make before the libgnomekbd runs without troubles and inside the gtk3+ is also one .c file that use's GTK_PIXELS without having a problem. 

As this is a kbd (=keyboard) compile stuff i wonder if it might be connected to the fact that i hda to install libxklavier16 because there is no libxklavier? 

```


*** Erstellung läuft libgnomekbd *** [1/1]
make  
make  all-recursive
make[1]: Betrete Verzeichnis '/home/mk/gnome-shell/source/libgnomekbd'
Making all in libgnomekbd
make[2]: Betrete Verzeichnis '/home/mk/gnome-shell/source/libgnomekbd/libgnomekbd'
  GEN    gkbd-indicator-marshal.h
  GEN    gkbd-indicator-marshal.c
  GEN    gkbd-keyboard-drawing-marshal.h
  GEN    gkbd-keyboard-drawing-marshal.c
make  all-am
make[3]: Betrete Verzeichnis '/home/mk/gnome-shell/source/libgnomekbd/libgnomekbd'
  CC     libgnomekbd_la-gkbd-desktop-config.lo
  CC     libgnomekbd_la-gkbd-keyboard-config.lo
  CC     libgnomekbd_la-gkbd-util.lo
  CCLD   libgnomekbd.la
  CC     libgnomekbdui_la-gkbd-indicator-config.lo
  CC     libgnomekbdui_la-gkbd-indicator.lo
  CC     libgnomekbdui_la-gkbd-status.lo
  CC     libgnomekbdui_la-gkbd-indicator-marshal.lo
  CC     libgnomekbdui_la-gkbd-indicator-plugin-manager.lo
  CC     libgnomekbdui_la-gkbd-keyboard-drawing-marshal.lo
  CC     libgnomekbdui_la-gkbd-keyboard-drawing.lo
gkbd-keyboard-drawing.c: In function ‘gkbd_keyboard_drawing_draw_page’:
gkbd-keyboard-drawing.c:2387: error: ‘GTK_PIXELS’ undeclared (first use in this function)
gkbd-keyboard-drawing.c:2387: error: (Each undeclared identifier is reported only once
gkbd-keyboard-drawing.c:2387: error: for each function it appears in.)
gkbd-keyboard-drawing.c: In function ‘gkbd_keyboard_drawing_new_dialog’:
gkbd-keyboard-drawing.c:2565: warning: implicit declaration of function ‘xkl_xkb_config_native_prepare’
gkbd-keyboard-drawing.c:2569: warning: implicit declaration of function ‘xkl_xkb_config_native_cleanup’
make[3]: *** [libgnomekbdui_la-gkbd-keyboard-drawing.lo] Fehler 1
make[3]: Verlasse Verzeichnis '/home/mk/gnome-shell/source/libgnomekbd/libgnomekbd'
make[2]: *** [all] Fehler 2
make[2]: Verlasse Verzeichnis '/home/mk/gnome-shell/source/libgnomekbd/libgnomekbd'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/mk/gnome-shell/source/libgnomekbd'
make: *** [all] Fehler 2
*** Fehler während Phase build von libgnomekbd: ########## Fehler beim Ausführen von make   *** [1/1]


```

---

### Post by jon.reeve on 2010-12-04
Any knowledgeable and charitable people out there who would be willing to put together a .deb of the latest snapshot for i386? That would be so awesome, and I bet would save hundreds of computing-hours for those of us non-devs who just want to try it out, and don't need to examine the source. Not to mention, many of us are having difficulty compiling it, and it takes so long to compile...

---

### Post by Harry33 on 2010-12-04
Newest gnome-shell (2.91.3) is based on GTK+3 and gnome3-desktop plus with dependencies on libgjs0b and xulrunner-2.0-mozjs.
Not a good idea to install this on Maverick.

But, then again, there are no working PPA's for Natty either.

Update:
Now Micah Gersten is going to upgrade gnome-shell_2.91.3 in to Nattys repos.

---

### Post by pat_96 on 2010-12-23
I'm sorry, is there someone that can help me with this problem?
 
```
configure: error: Package requirements (gio-2.0 >= 2.25.9
                                 gio-unix-2.0 dbus-glib-1
                                 gtk+-3.0 >= 2.91.7
                                 mutter-plugins >= 2.91.4
                                 gjs-internals-1.0 >= 0.7
				 libgnome-menu gstreamer-0.10 gstreamer-base-0.10 xfixes gconf-2.0
                                 gdk-x11-3.0
				 clutter-x11-1.0 >= 1.5.8
				 clutter-glx-1.0 >= 1.5.8
                                 libstartup-notification-1.0
                                 gobject-introspection-1.0 >= 0.6.11
				 libcanberra) were not met:

Requested 'mutter-plugins >= 2.91.4' but version of mutter-plugins is 2.91.3

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MUTTER_PLUGIN_CFLAGS
and MUTTER_PLUGIN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
*** Error during phase configure of gnome-shell: ########## Errore nell'eseguire ./autogen.sh --prefix /home/patrick/gnome-shell/install --libdir '/home/patrick/gnome-shell/install/lib'  --disable-static --disable-gtk-doc  *** [30/33]

```
How can i fix this error? Thanks :)

---

### Post by Harry33 on 2010-12-23
> **pat_96 said:**
> I'm sorry, is there someone that can help me with this problem?
...
```
configure: error: Package requirements (gio-2.0 >= 2.25.9
...
                                 mutter-plugins >= 2.91.4
...

Requested 'mutter-plugins >= 2.91.4' but version of mutter-plugins is 2.91.3


```
How can i fix this error? Thanks :)

Seems you have too old mutter version (2.91.3). Newer is needed (2.91.4).

---

### Post by pat_96 on 2010-12-23
I've just added ricotz's PPA and choosed in synaptic to install the proposed-updates... It works!!!

---

### Post by Buying_Some_Time on 2011-02-11
Hello, I've successfully built my gnome shell but, when I try to start it I get this error: 

```
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: Log level 16: Accessibility: org.a11y.atspi  schema not found. Are you sure that at-spi or at-spi2 is installed on  your system?
Window manager warning: Log level 16: Accessibility: invalid module path (NULL)
Window manager warning: Log level 16: Accessibility: error loading the  atk-bridge. Although the accessibility on the system is enabled and  clutter accessibility is also enabled, accessibility support on GNOME  Shell will not work
      JS LOG: GNOME Shell started at Fri Feb 11 2011 10:21:20 GMT-0500 (EST)
gnome-power-manager: error while loading shared libraries:  libcanberra-gtk3.so.0: cannot open shared object file: No such file or  directory
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:11324): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:11347): WARNING **: Unknown option --since=2010-12-13T15:21:26.982142Z
Window manager warning: Log level 8: meta_window_raise: assertion `!window->override_redirect' failed
Window manager warning: Log level 8: meta_window_focus: assertion  `!window->override_redirect' failed
```Anyone know how to fix  this? 

Thanks!

I used the JHbuild btw.

---

### Post by wersdaluv on 2011-02-13
For those people who built Shell from source recently, if you can't run it, this will do the trick: 

```
rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so
```

---

### Post by wersdaluv on 2011-03-06
> **wersdaluv said:**
> Let this be the thread for GNOME Shell Installation stuff on Maverick. I update this first post whenever there's something noteworthy about the subject.

This thread is only for discussing GNOME Shell installation on Maverick.

See the [GNOME Shell Testing thread]("http://ubuntuforums.org/showthread.php?t=1476241") on Meerkat Testing and Discussion forum for your reference.

**Installing GNOME Shell from the Ubuntu Repository**

An easy way of installing GNOME Shell is by using the version in the repository. However, this is relatively outdated. To do this, simply install the gnome-shell package from the Ubuntu Software Center.

**Installing GNOME Shell from Source**

The following steps are expected to work when there's no existing ~/gnome-shell folder
[LIST=1]
[*][Remove La Files]("http://live.gnome.org/GnomeShell/RemovingLaFiles")
[*]Install Dependencies
```
sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xulrunner-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils autopoint libvorbis-dev libpam-dev libgcrypt-dev libtasn1-dev libtasn1-3-bin libgnome-keyring-dev libupower-glib-dev libxklavier16 libxklavier-dev xserver-xephyr python-dev libpulse-dev libjasper-dev jhbuild libgtop2-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev libcups2-dev libusb-1.0-0-dev
```
[*][Build from Source]("http://live.gnome.org/GnomeShell/#Building")
[/LIST]


**Running GNOME Shell**

If you built it from source, follow [these instructions]("http://live.gnome.org/GnomeShell#Running")

If you installed it from a repository, just run ```
gnome-shell --replace
```

*edited to add dependencies

---

### Post by rvchari on 2011-05-29
to the first post....
```
$ sudo tee /etc/apt/apt.conf.d/90removela <<< 'DPkg { Post-Invoke { "find /usr/lib*/ -name "*.la" -delete 2> /dev/null || true"; }; };'
```

is the above command line a one time use after compilation / build or i have to use everytime i update my system?

may sound a silly question but still i would like to confirm.

---

