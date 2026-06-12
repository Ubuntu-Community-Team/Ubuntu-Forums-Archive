---
title: "Determined to install a tar.gz file!"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by Youbuntoo44 on 2008-10-07
OH MY FREAKING GOD! All posts I've seen on forums are sooo useless, ALL I have ever gotten is Error or Directory not found or Authentication Denied or Term denied..... I am DETERMINED to install Xautoclick sometime this week maybe? I need insanely easy steps on how to install it, like if you need to type anything in, I need to know. "Go to your installed directory" is not useful..... TIA

---

### Post by nomind111 on 2008-10-07
dude i know what you mean, its driving me crazy, "go to your madwifi source directory" and type...it seems to obviouse that to new beginners those inbetween steps need to be explained.  best of luck to you.

---

### Post by Youbuntoo44 on 2008-10-07
Thank you, hope you can succeed!

---

### Post by christianvaldes on 2008-10-07
What package are you trying to install?
What error are you getting?

---

### Post by Youbuntoo44 on 2008-10-07
I am trying to install "Xautoclick" and the filename is xautoclick-0.19-src.tar.gz and I am getting multiple errors, I am basically totally lost.

---

### Post by christianvaldes on 2008-10-07
what command are you running?
post errors please

---

### Post by christianvaldes on 2008-10-07
Seems like development on this project was abandoned 2 years ago.

---

### Post by Pumalite on 2008-10-07
1. anytime you download a .tar.gz or whatever, just save it to the desktop, its just easier.

2. extract the files by right clicking and hitting "extract here" which will extract it to the desktop.

3. open a terminal window by going to Applications>Accessories>Terminal

4. type "cd Desktop" and make sure to capitalize the D

5. now type "ls" (thats a lowercase LS just for clarity's sake)

6. this should give you a list of all the directories on the desktop, find the one you want, it should be the name of whatever program you're trying to install, but make sure you don't pick the .tar, you want the one you extracted, which will be the same thing without the extension. Highlight and copy the name.

7. Now type "cd" and paste what you just copied after it (remembering the space between cd and the file name)

8. Now type ./configure to automatically configure the program. if it stops in the middle and says it needs a package, copy the name of the package, go to the synaptic package manager (system>administration>synaptic package manager) and do a search for that package. anything that looks the same with -dev on the end is also necessary, get it to. once you've got everything checked, click apply.

9. now back in the terminal (if you closed it, you'll have to navigate back to the directory again, using steps 4-7) type ./configure again

10. repeat steps 8-9 until all the packages necessary have been installed and the configuration completes.

11. Now type "make" to compile the code

12, now "make install" to install it

---

### Post by Youbuntoo44 on 2008-10-07
I am using bash, my errors are short and simple like "authentication denied" or "directory not found" or cp: missing destination file operand after `/home/giles/xautoclick/xautoclick-0.19-src.tar.gz'

---

### Post by christianvaldes on 2008-10-07
where did you put the package?

tar xvf package
this will extract the folder

the change directory into the folder

run theses commands

./configure
make
make install

---

### Post by Youbuntoo44 on 2008-10-07
Thank you! Most helpful guide yet.... but at the end....

giles@playroom:~/Desktop/xautoclick-0.19-src$ make
make: Nothing to be done for `all'.
giles@playroom:~/Desktop/xautoclick-0.19-src$ make install
Installing to /usr/local
if test ! -d /usr/local/bin ; then mkdir -p /usr/local/bin ; fi
if test ! -d /usr/local/man/man1 ; then mkdir -p /usr/local/man/man1 ; fi
mkdir: cannot create directory `/usr/local/man/man1': Permission denied
make: *** [install] Error 1
giles@playroom:~/Desktop/xautoclick-0.19-src$ 


Huh?

---

### Post by mick222 on 2008-10-07
> **Pumalite said:**
> 1. anytime you download a .tar.gz or whatever, just save it to the desktop, its just easier.

2. extract the files by right clicking and hitting "extract here" which will extract it to the desktop.

3. open a terminal window by going to Applications>Accessories>Terminal

4. type "cd Desktop" and make sure to capitalize the D

5. now type "ls" (thats a lowercase LS just for clarity's sake)

6. this should give you a list of all the directories on the desktop, find the one you want, it should be the name of whatever program you're trying to install, but make sure you don't pick the .tar, you want the one you extracted, which will be the same thing without the extension. Highlight and copy the name.

7. Now type "cd" and paste what you just copied after it (remembering the space between cd and the file name)

8. Now type ./configure to automatically configure the program. if it stops in the middle and says it needs a package, copy the name of the package, go to the synaptic package manager (system>administration>synaptic package manager) and do a search for that package. anything that looks the same with -dev on the end is also necessary, get it to. once you've got everything checked, click apply.

9. now back in the terminal (if you closed it, you'll have to navigate back to the directory again, using steps 4-7) type ./configure again

10. repeat steps 8-9 until all the packages necessary have been installed and the configuration completes.

11. Now type "make" to compile the code

12, now "make install" to install it

great explanation thx

---

### Post by christianvaldes on 2008-10-07
Well I get the same thing when running...

make

This confuses me because its like nothing was compiled.

The make install will work if you run this...

sudo make install

---

### Post by Youbuntoo44 on 2008-10-07
No error, but it's not installed, I don't know where it is.

---

### Post by christianvaldes on 2008-10-07
I think there is something wrong with the program.
I would not rack my brain on it.
When the make command is run does not look like anything is compiled.
I did the same on my system hear to get it installed and I don't see it anywhere.

The developer seems to have abandoned the project in 2006.

May I ask why you need it up and running.

I would infer that there is another solution.

---

### Post by Youbuntoo44 on 2008-10-07
can somebody tell me what do do after this? It takes like NO time at all to do 'sudo make install' and It's not installed anywhere.

---

### Post by haydnc on 2008-10-07
If the project was abandoned in 2006 as Christian says then it could be that you'll never get it running (or at least running properly) under your current OS.

Can you tell us what it is you need it for so we can suggest an alternative option that might work for you?

---

### Post by christianvaldes on 2008-10-07
run this...

sudo apt-get install xorg-dev

then run this in the directory of the source code files

make clean
make
sudo make install

this will get farther then we have been

---

### Post by Youbuntoo44 on 2008-10-07
I would like to install the program "Xautoclick" because "Kautoclick" wasn't very good.

---

### Post by christianvaldes on 2008-10-07
> **christianvaldes said:**
> run this...

sudo apt-get install xorg-dev

then run this in the directory of the source code files

make clean
make
sudo make install

this will get farther then we have been

this worked 
thou I have no clue what this program does
even after reading the description I still don't get it

---

### Post by Youbuntoo44 on 2008-10-07
giles@playroom:~/Desktop/xautoclick-0.19-src$ make clean
rm -f *.o gautoclick gautoclick2 qtautoclick aautoclick cautoclick guigtk2.c
rm -rf .deps
giles@playroom:~/Desktop/xautoclick-0.19-src$ make
make: Nothing to be done for `all'.
giles@playroom:~/Desktop/xautoclick-0.19-src$ make install
Installing to /usr/local
if test ! -d /usr/local/bin ; then mkdir -p /usr/local/bin ; fi
if test ! -d /usr/local/man/man1 ; then mkdir -p /usr/local/man/man1 ; fi
cp xautoclick.1 /usr/local/man/man1
cp: cannot create regular file `/usr/local/man/man1/xautoclick.1': Permission denied
make: *** [install] Error 1
giles@playroom:~/Desktop/xautoclick-0.19-src$ sudo make install
[sudo] password for giles: 
Installing to /usr/local
if test ! -d /usr/local/bin ; then mkdir -p /usr/local/bin ; fi
if test ! -d /usr/local/man/man1 ; then mkdir -p /usr/local/man/man1 ; fi
cp xautoclick.1 /usr/local/man/man1
giles@playroom:~/Desktop/xautoclick-0.19-src$ 

Is my new error,

---

### Post by christianvaldes on 2008-10-07
did you install this...

sudo apt-get install xorg-dev

---

### Post by Youbuntoo44 on 2008-10-07
Yes I did

---

### Post by Youbuntoo44 on 2008-10-07
giles@playroom:~/Desktop/xautoclick-0.19-src$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libdmx-dev libexpat1-dev libfontconfig1-dev libfontenc-dev
  libfreetype6-dev libfs-dev libice-dev libpixman-1-dev libpthread-stubs0
  libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxaw-headers
  libxaw7-dev libxcb-xlib0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxevie-dev libxext-dev libxfixes-dev
  libxfont-dev libxft-dev libxi-dev libxinerama-dev libxkbfile-dev
  libxkbui-dev libxkbui1 libxmu-dev libxmu-headers libxmuu-dev libxpm-dev
  libxrandr-dev libxrender-dev libxres-dev libxss-dev libxt-dev libxtrap-dev
  libxtst-dev libxv-dev libxvmc-dev libxxf86dga-dev libxxf86misc-dev
  libxxf86vm-dev linux-libc-dev x11proto-bigreqs-dev x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-dmx-dev x11proto-evie-dev
  x11proto-fixes-dev x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev
  x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev
  x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xserver-xorg-dev xtrans-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev libdmx-dev libexpat1-dev libfontconfig1-dev libfontenc-dev
  libfreetype6-dev libfs-dev libice-dev libpixman-1-dev libpthread-stubs0
  libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxaw-headers
  libxaw7-dev libxcb-xlib0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxevie-dev libxext-dev libxfixes-dev
  libxfont-dev libxft-dev libxi-dev libxinerama-dev libxkbfile-dev
  libxkbui-dev libxkbui1 libxmu-dev libxmu-headers libxmuu-dev libxpm-dev
  libxrandr-dev libxrender-dev libxres-dev libxss-dev libxt-dev libxtrap-dev
  libxtst-dev libxv-dev libxvmc-dev libxxf86dga-dev libxxf86misc-dev
  libxxf86vm-dev linux-libc-dev x11proto-bigreqs-dev x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-dmx-dev x11proto-evie-dev
  x11proto-fixes-dev x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev
  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev
  x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev
  x11proto-xf86bigfont-dev x11proto-xf86dga-dev x11proto-xf86dri-dev
  x11proto-xf86misc-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev
  xorg-dev xserver-xorg-dev xtrans-dev zlib1g-dev
0 upgraded, 80 newly installed, 0 to remove and 1 not upgraded.
Need to get 10.6MB of archives.
After this operation, 41.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-core-dev 7.0.11-1 [88.9kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxau-dev 1:1.0.3-2 [15.6kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libpthread-stubs0 0.1-2 [2812B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libpthread-stubs0-dev 0.1-2 [3090B]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxdmcp-dev 1:1.0.2-2 [20.0kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxcb1-dev 1.1-1ubuntu1 [67.0kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxcb-xlib0-dev 1.1-1ubuntu1 [14.8kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-input-dev 1.4.2-1 [15.6kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-kb-dev 1.0.3-2ubuntu1 [27.0kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main xtrans-dev 1.0.4-1 [70.5kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libx11-dev 2:1.1.3-1ubuntu2 [1686kB]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-dmx-dev 1:2.2.2-4ubuntu1 [6706B]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libdmx-dev 1:1.0.2-2build1 [33.2kB]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-proposed/main linux-libc-dev 2.6.24-21.42 [698kB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main zlib1g-dev 1:1.2.3.3.dfsg-7ubuntu1 [160kB]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libfontenc-dev 1:1.0.4-2 [19.9kB]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-fonts-dev 2.0.2-5ubuntu1 [12.2kB]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libfs-dev 2:1.0.0-4ubuntu2 [28.2kB]
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libice-dev 2:1.0.4-1 [56.0kB]   
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libsm-dev 2:1.0.3-1 [24.3kB]    
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xext-dev 7.0.2-5ubuntu1 [42.2kB]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxext-dev 2:1.0.3-2build1 [81.6kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxmu-headers 2:1.0.4-1 [21.1kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxt-dev 1:1.0.5-3 [482kB]     
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxmu-dev 2:1.0.4-1 [55.2kB]   
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxpm-dev 1:3.5.7-1 [45.9kB]   
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxaw-headers 2:1.0.4-1 [69.5kB]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-fixes-dev 1:4.0-2ubuntu1 [6172B]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxfixes-dev 1:4.0.3-2 [12.1kB]
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-composite-dev 1:0.4-2 [12.4kB]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxcomposite-dev 1:0.4.0-1 [14.3kB]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-render-dev 2:0.9.3-2 [7096B]
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxrender-dev 1:0.9.4-1 [28.5kB]
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxcursor-dev 1:1.1.9-1 [31.0kB]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-damage-dev 1:1.1.0-2build1 [9292B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxdamage-dev 1:1.1.1-3 [9682B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-evie-dev 1:1.0.2-4ubuntu1 [4622B]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxevie-dev 1:1.0.2-2 [10.2kB] 
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main libfreetype6-dev 2.3.5-1ubuntu4.8.04.1 [663kB]
Get:41 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxfont-dev 1:1.3.1-2 [272kB]  
Get:42 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libexpat1-dev 2.0.1-0ubuntu1 [134kB]
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libfontconfig1-dev 2.5.0-2ubuntu3 [572kB]
Get:44 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxft-dev 2.1.12-2ubuntu5 [60.8kB]
Get:45 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxi-dev 2:1.1.3-1 [69.3kB]    
Get:46 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]
Get:47 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxinerama-dev 2:1.0.2-1build1 [10.9kB]
Get:48 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxkbfile-dev 1:1.0.4-1 [81.5kB]
Get:49 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxkbui1 1:1.0.2-2 [8810B]     
Get:50 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxkbui-dev 1:1.0.2-2 [9032B]  
Get:51 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-randr-dev 1.2.1-2 [28.6kB]
Get:52 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxrandr-dev 2:1.2.2-1 [27.8kB]
Get:53 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-resource-dev 1.0.2-4ubuntu1 [3994B]
Get:54 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxres-dev 2:1.0.3-1 [11.7kB]  
Get:55 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-scrnsaver-dev 1.1.0.0-1 [5204B]
Get:56 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxss-dev 1:1.1.2-1 [15.9kB]   
Get:57 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-trap-dev 3.4.3-5ubuntu1 [16.2kB]
Get:58 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxtrap-dev 2:1.0.0-4build1 [16.3kB]
Get:59 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-record-dev 1.13.2-4ubuntu1 [6022B]
Get:60 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxtst-dev 2:1.0.3-1 [14.8kB]  
Get:61 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-video-dev 2.2.2-4ubuntu1 [9838B]
Get:62 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxv-dev 2:1.0.3-1ubuntu1 [36.2kB]
Get:63 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxvmc-dev 2:1.0.4-2ubuntu1 [18.9kB]
Get:64 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xf86dga-dev 2.0.3-1 [9770B]
Get:65 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxxf86dga-dev 2:1.0.2-1 [20.8kB]
Get:66 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xf86misc-dev 0.9.2-4ubuntu1 [5614B]
Get:67 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxxf86misc-dev 1:1.0.1-2 [9594B]
Get:68 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xf86vidmode-dev 2.2.2-4ubuntu1 [6596B]
Get:69 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxxf86vm-dev 1:1.0.1-2 [14.1kB]
Get:70 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-bigreqs-dev 1:1.0.2-4ubuntu1 [3998B]
Get:71 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-fontcache-dev 0.1.2-4ubuntu1 [4592B]
Get:72 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xcmisc-dev 1.1.2-4ubuntu1 [3726B]
Get:73 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xf86bigfont-dev 1.1.2-4ubuntu1 [4526B]
Get:74 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-xf86dri-dev 2.0.3-4ubuntu1 [5796B]
Get:75 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libpixman-1-dev 0.10.0-0ubuntu1 [86.1kB]
Get:76 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxaw7-dev 2:1.0.4-1 [213kB]   
Get:77 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libxmuu-dev 2:1.0.4-1 [12.8kB]  
Get:78 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main x11proto-gl-dev 1.4.9-1 [31.3kB]
Get:79 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main xserver-xorg-dev 2:1.4.1~git20080131-1ubuntu9.2 [695kB]
Get:80 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main xorg-dev 1:7.3+10ubuntu10.2 [1420B]
Fetched 10.6MB in 10s (988kB/s)                                                
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 126906 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.11-1_all.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-2_i386.deb) ...
Selecting previously deselected package libpthread-stubs0.
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.1-2_i386.deb) ...
Selecting previously deselected package libpthread-stubs0-dev.
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.1-2_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package libxcb1-dev.
Unpacking libxcb1-dev (from .../libxcb1-dev_1.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxcb-xlib0-dev.
Unpacking libxcb-xlib0-dev (from .../libxcb-xlib0-dev_1.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.2-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.4-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.3-1ubuntu2_i386.deb) ...
Selecting previously deselected package x11proto-dmx-dev.
Unpacking x11proto-dmx-dev (from .../x11proto-dmx-dev_1%3a2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libdmx-dev.
Unpacking libdmx-dev (from .../libdmx-dev_1%3a1.0.2-2build1_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-21.42_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-7ubuntu1_i386.deb) ...
Selecting previously deselected package libfontenc-dev.
Unpacking libfontenc-dev (from .../libfontenc-dev_1%3a1.0.4-2_i386.deb) ...
Selecting previously deselected package x11proto-fonts-dev.
Unpacking x11proto-fonts-dev (from .../x11proto-fonts-dev_2.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package libfs-dev.
Unpacking libfs-dev (from .../libfs-dev_2%3a1.0.0-4ubuntu2_i386.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.4-1_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.3-1_i386.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-2build1_i386.deb) ...
Selecting previously deselected package libxmu-headers.
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.0.4-1_all.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.5-3_i386.deb) ...
Selecting previously deselected package libxmu-dev.
Unpacking libxmu-dev (from .../libxmu-dev_2%3a1.0.4-1_i386.deb) ...
Selecting previously deselected package libxpm-dev.
Unpacking libxpm-dev (from .../libxpm-dev_1%3a3.5.7-1_i386.deb) ...
Selecting previously deselected package libxaw-headers.
Unpacking libxaw-headers (from .../libxaw-headers_2%3a1.0.4-1_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-2ubuntu1_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.3-2_i386.deb) ...
Selecting previously deselected package x11proto-composite-dev.
Unpacking x11proto-composite-dev (from .../x11proto-composite-dev_1%3a0.4-2_all.deb) ...
Selecting previously deselected package libxcomposite-dev.
Unpacking libxcomposite-dev (from .../libxcomposite-dev_1%3a0.4.0-1_i386.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.3-2_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.4-1_i386.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.9-1_i386.deb) ...
Selecting previously deselected package x11proto-damage-dev.
Unpacking x11proto-damage-dev (from .../x11proto-damage-dev_1%3a1.1.0-2build1_all.deb) ...
Selecting previously deselected package libxdamage-dev.
Unpacking libxdamage-dev (from .../libxdamage-dev_1%3a1.1.1-3_i386.deb) ...
Selecting previously deselected package x11proto-evie-dev.
Unpacking x11proto-evie-dev (from .../x11proto-evie-dev_1%3a1.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxevie-dev.
Unpacking libxevie-dev (from .../libxevie-dev_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.3.5-1ubuntu4.8.04.1_i386.deb) ...
Selecting previously deselected package libxfont-dev.
Unpacking libxfont-dev (from .../libxfont-dev_1%3a1.3.1-2_i386.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_2.0.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.5.0-2ubuntu3_i386.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-2ubuntu5_i386.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.3-1_i386.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.2-1build1_i386.deb) ...
Selecting previously deselected package libxkbfile-dev.
Unpacking libxkbfile-dev (from .../libxkbfile-dev_1%3a1.0.4-1_i386.deb) ...
Selecting previously deselected package libxkbui1.
Unpacking libxkbui1 (from .../libxkbui1_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package libxkbui-dev.
Unpacking libxkbui-dev (from .../libxkbui-dev_1%3a1.0.2-2_i386.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-2_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.2.2-1_i386.deb) ...
Selecting previously deselected package x11proto-resource-dev.
Unpacking x11proto-resource-dev (from .../x11proto-resource-dev_1.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxres-dev.
Unpacking libxres-dev (from .../libxres-dev_2%3a1.0.3-1_i386.deb) ...
Selecting previously deselected package x11proto-scrnsaver-dev.
Unpacking x11proto-scrnsaver-dev (from .../x11proto-scrnsaver-dev_1.1.0.0-1_all.deb) ...
Selecting previously deselected package libxss-dev.
Unpacking libxss-dev (from .../libxss-dev_1%3a1.1.2-1_i386.deb) ...
Selecting previously deselected package x11proto-trap-dev.
Unpacking x11proto-trap-dev (from .../x11proto-trap-dev_3.4.3-5ubuntu1_all.deb) ...
Selecting previously deselected package libxtrap-dev.
Unpacking libxtrap-dev (from .../libxtrap-dev_2%3a1.0.0-4build1_i386.deb) ...
Selecting previously deselected package x11proto-record-dev.
Unpacking x11proto-record-dev (from .../x11proto-record-dev_1.13.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxtst-dev.
Unpacking libxtst-dev (from .../libxtst-dev_2%3a1.0.3-1_i386.deb) ...
Selecting previously deselected package x11proto-video-dev.
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxv-dev.
Unpacking libxv-dev (from .../libxv-dev_2%3a1.0.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxvmc-dev.
Unpacking libxvmc-dev (from .../libxvmc-dev_2%3a1.0.4-2ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-xf86dga-dev.
Unpacking x11proto-xf86dga-dev (from .../x11proto-xf86dga-dev_2.0.3-1_all.deb) ...
Selecting previously deselected package libxxf86dga-dev.
Unpacking libxxf86dga-dev (from .../libxxf86dga-dev_2%3a1.0.2-1_i386.deb) ...
Selecting previously deselected package x11proto-xf86misc-dev.
Unpacking x11proto-xf86misc-dev (from .../x11proto-xf86misc-dev_0.9.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86misc-dev.
Unpacking libxxf86misc-dev (from .../libxxf86misc-dev_1%3a1.0.1-2_i386.deb) ...
Selecting previously deselected package x11proto-xf86vidmode-dev.
Unpacking x11proto-xf86vidmode-dev (from .../x11proto-xf86vidmode-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86vm-dev.
Unpacking libxxf86vm-dev (from .../libxxf86vm-dev_1%3a1.0.1-2_i386.deb) ...
Selecting previously deselected package x11proto-bigreqs-dev.
Unpacking x11proto-bigreqs-dev (from .../x11proto-bigreqs-dev_1%3a1.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fontcache-dev.
Unpacking x11proto-fontcache-dev (from .../x11proto-fontcache-dev_0.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xcmisc-dev.
Unpacking x11proto-xcmisc-dev (from .../x11proto-xcmisc-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xf86bigfont-dev.
Unpacking x11proto-xf86bigfont-dev (from .../x11proto-xf86bigfont-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xf86dri-dev.
Unpacking x11proto-xf86dri-dev (from .../x11proto-xf86dri-dev_2.0.3-4ubuntu1_all.deb) ...
Selecting previously deselected package libpixman-1-dev.
Unpacking libpixman-1-dev (from .../libpixman-1-dev_0.10.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libxaw7-dev.
Unpacking libxaw7-dev (from .../libxaw7-dev_2%3a1.0.4-1_i386.deb) ...
Selecting previously deselected package libxmuu-dev.
Unpacking libxmuu-dev (from .../libxmuu-dev_2%3a1.0.4-1_i386.deb) ...
Selecting previously deselected package x11proto-gl-dev.
Unpacking x11proto-gl-dev (from .../x11proto-gl-dev_1.4.9-1_all.deb) ...
Selecting previously deselected package xserver-xorg-dev.
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.4.1~git20080131-1ubuntu9.2_i386.deb) ...
Selecting previously deselected package xorg-dev.
Unpacking xorg-dev (from .../xorg-dev_1%3a7.3+10ubuntu10.2_all.deb) ...
Setting up x11proto-core-dev (7.0.11-1) ...
Setting up libxau-dev (1:1.0.3-2) ...
Setting up libpthread-stubs0 (0.1-2) ...
Setting up libpthread-stubs0-dev (0.1-2) ...
Setting up libxdmcp-dev (1:1.0.2-2) ...
Setting up libxcb1-dev (1.1-1ubuntu1) ...
Setting up libxcb-xlib0-dev (1.1-1ubuntu1) ...
Setting up x11proto-input-dev (1.4.2-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.4-1) ...
Setting up libx11-dev (2:1.1.3-1ubuntu2) ...
Setting up x11proto-dmx-dev (1:2.2.2-4ubuntu1) ...
Setting up libdmx-dev (1:1.0.2-2build1) ...
Setting up linux-libc-dev (2.6.24-21.42) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Setting up libfontenc-dev (1:1.0.4-2) ...
Setting up x11proto-fonts-dev (2.0.2-5ubuntu1) ...
Setting up libfs-dev (2:1.0.0-4ubuntu2) ...
Setting up libice-dev (2:1.0.4-1) ...
Setting up libsm-dev (2:1.0.3-1) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up libxext-dev (2:1.0.3-2build1) ...
Setting up libxmu-headers (2:1.0.4-1) ...
Setting up libxt-dev (1:1.0.5-3) ...
Setting up libxmu-dev (2:1.0.4-1) ...
Setting up libxpm-dev (1:3.5.7-1) ...
Setting up libxaw-headers (2:1.0.4-1) ...
Setting up x11proto-fixes-dev (1:4.0-2ubuntu1) ...
Setting up libxfixes-dev (1:4.0.3-2) ...
Setting up x11proto-composite-dev (1:0.4-2) ...
Setting up libxcomposite-dev (1:0.4.0-1) ...
Setting up x11proto-render-dev (2:0.9.3-2) ...
Setting up libxrender-dev (1:0.9.4-1) ...
Setting up libxcursor-dev (1:1.1.9-1) ...
Setting up x11proto-damage-dev (1:1.1.0-2build1) ...
Setting up libxdamage-dev (1:1.1.1-3) ...
Setting up x11proto-evie-dev (1:1.0.2-4ubuntu1) ...
Setting up libxevie-dev (1:1.0.2-2) ...
Setting up libfreetype6-dev (2.3.5-1ubuntu4.8.04.1) ...

Setting up libxfont-dev (1:1.3.1-2) ...
Setting up libexpat1-dev (2.0.1-0ubuntu1) ...

Setting up libfontconfig1-dev (2.5.0-2ubuntu3) ...

Setting up libxft-dev (2.1.12-2ubuntu5) ...
Setting up libxi-dev (2:1.1.3-1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up libxinerama-dev (2:1.0.2-1build1) ...
Setting up libxkbfile-dev (1:1.0.4-1) ...
Setting up libxkbui1 (1:1.0.2-2) ...

Setting up libxkbui-dev (1:1.0.2-2) ...
Setting up x11proto-randr-dev (1.2.1-2) ...
Setting up libxrandr-dev (2:1.2.2-1) ...
Setting up x11proto-resource-dev (1.0.2-4ubuntu1) ...
Setting up libxres-dev (2:1.0.3-1) ...
Setting up x11proto-scrnsaver-dev (1.1.0.0-1) ...
Setting up libxss-dev (1:1.1.2-1) ...
Setting up x11proto-trap-dev (3.4.3-5ubuntu1) ...
Setting up libxtrap-dev (2:1.0.0-4build1) ...
Setting up x11proto-record-dev (1.13.2-4ubuntu1) ...
Setting up libxtst-dev (2:1.0.3-1) ...
Setting up x11proto-video-dev (2.2.2-4ubuntu1) ...
Setting up libxv-dev (2:1.0.3-1ubuntu1) ...
Setting up libxvmc-dev (2:1.0.4-2ubuntu1) ...
Setting up x11proto-xf86dga-dev (2.0.3-1) ...
Setting up libxxf86dga-dev (2:1.0.2-1) ...
Setting up x11proto-xf86misc-dev (0.9.2-4ubuntu1) ...
Setting up libxxf86misc-dev (1:1.0.1-2) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-4ubuntu1) ...
Setting up libxxf86vm-dev (1:1.0.1-2) ...
Setting up x11proto-bigreqs-dev (1:1.0.2-4ubuntu1) ...
Setting up x11proto-fontcache-dev (0.1.2-4ubuntu1) ...
Setting up x11proto-xcmisc-dev (1.1.2-4ubuntu1) ...
Setting up x11proto-xf86bigfont-dev (1.1.2-4ubuntu1) ...
Setting up x11proto-xf86dri-dev (2.0.3-4ubuntu1) ...
Setting up libpixman-1-dev (0.10.0-0ubuntu1) ...
Setting up libxaw7-dev (2:1.0.4-1) ...
Setting up libxmuu-dev (2:1.0.4-1) ...
Setting up x11proto-gl-dev (1.4.9-1) ...
Setting up xserver-xorg-dev (2:1.4.1~git20080131-1ubuntu9.2) ...
Setting up xorg-dev (1:7.3+10ubuntu10.2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
giles@playroom:~/Desktop/xautoclick-0.19-src$ make clean
rm -f *.o gautoclick gautoclick2 qtautoclick aautoclick cautoclick guigtk2.c
rm -rf .deps
giles@playroom:~/Desktop/xautoclick-0.19-src$ make
make: Nothing to be done for `all'.
giles@playroom:~/Desktop/xautoclick-0.19-src$ sudo make install
Installing to /usr/local
if test ! -d /usr/local/bin ; then mkdir -p /usr/local/bin ; fi
if test ! -d /usr/local/man/man1 ; then mkdir -p /usr/local/man/man1 ; fi
cp xautoclick.1 /usr/local/man/man1
giles@playroom:~/Desktop/xautoclick-0.19-src$

---

### Post by christianvaldes on 2008-10-07
run this...

make clean
./configure
make
sudo make install

---

### Post by Youbuntoo44 on 2008-10-07
Okay that did all good. But I have the feeling it is installed, but it's not in my applications list. Where could I find it?

giles@playroom:~/Desktop/xautoclick-0.19-src$ make
__BUILD_ASCII__=yes make -C . aautoclick
make[1]: Entering directory `/home/giles/Desktop/xautoclick-0.19-src'
gcc -c -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   main.c -o main.o  
mkdir -p .deps
gcc -MM -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   main.c 1>.deps/main.d
gcc -c -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   osdep.c -o osdep.o  
mkdir -p .deps
gcc -MM -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   osdep.c 1>.deps/osdep.d
gcc -c -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   guiascii.c -o guiascii.o  
mkdir -p .deps
gcc -MM -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   guiascii.c 1>.deps/guiascii.d
gcc -o aautoclick main.o osdep.o  guiascii.o  -lm  -L/usr/lib -lX11 -lXext -lXtst
make[1]: Leaving directory `/home/giles/Desktop/xautoclick-0.19-src'
__BUILD_COMMANDLINE__=yes make -C . cautoclick
make[1]: Entering directory `/home/giles/Desktop/xautoclick-0.19-src'
gcc -c -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   guicommandline.c -o guicommandline.o  
mkdir -p .deps
gcc -MM -O4 -DHAVE_INTTYPES_H  -DHAVE_MALLOC_H -DHAVE_UNISTD_H   guicommandline.c 1>.deps/guicommandline.d
gcc -o cautoclick main.o osdep.o  guicommandline.o  -lm  -L/usr/lib -lX11 -lXext -lXtst
make[1]: Leaving directory `/home/giles/Desktop/xautoclick-0.19-src'
giles@playroom:~/Desktop/xautoclick-0.19-src$ sudo make install
__BUILD_ASCII__=yes make -C . aautoclick
make[1]: Entering directory `/home/giles/Desktop/xautoclick-0.19-src'
make[1]: `aautoclick' is up to date.
make[1]: Leaving directory `/home/giles/Desktop/xautoclick-0.19-src'
__BUILD_COMMANDLINE__=yes make -C . cautoclick
make[1]: Entering directory `/home/giles/Desktop/xautoclick-0.19-src'
make[1]: `cautoclick' is up to date.
make[1]: Leaving directory `/home/giles/Desktop/xautoclick-0.19-src'
Installing to /usr/local
if test ! -d /usr/local/bin ; then mkdir -p /usr/local/bin ; fi
if test ! -d /usr/local/man/man1 ; then mkdir -p /usr/local/man/man1 ; fi
cp aautoclick /usr/local/bin
cp cautoclick /usr/local/bin
cp xautoclick.1 /usr/local/man/man1

---

### Post by christianvaldes on 2008-10-07
there is no GUI installed for it yet....
Graphical User Interface

Supposedly one exist but I can't find it anywhere.

you can run it from a command line...

aautoclick

It seems like this project has been abandoned.

I must state that for whatever the program does...there most be a modern day solution for it that does not have to have us go throw all this.

Not sure but I will post if I find the other solution.

[http://xautoclick.sourceforge.net/news.html](http://xautoclick.sourceforge.net/news.html)

---

### Post by Youbuntoo44 on 2008-10-07
Ohhh ok it doesn't have a GUI, but I finally figured out how to install it.  thanks to all for being so helpful!

---

### Post by christianvaldes on 2008-10-07
you can thank me
by giving me a thanks on the ubuntu forum :)

---

### Post by dirkbee on 2008-10-17
> **Youbuntoo44 said:**
> Ohhh ok it doesn't have a GUI, but I finally figured out how to install it.  thanks to all for being so helpful!

If you want the GUI version(s), you need to install the proper development packages, e.g.

sudo apt-get install gtk2-dev

then rerun configure and make and sudo make install.

HTH

---

### Post by steveneddy on 2008-10-17
Can w mark this as solved then?

---

### Post by itisbasi on 2008-10-17
"type "cd Desktop" and make sure to capitalize the D"
I still remember, I struggled to realize this for close to a half an hour when I initially migrated to ubuntu a year back. Lol

---

