---
title: "head-tracking plugin for compiz, installation stops at &quot;make&quot; command"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by zenek89 on 2010-05-10
hey Guys I have a problem with installing the head-tracking plugin for confiz. I have downloaded and installed openCV as directed, (it's 2.0 instead of 1.1.0) because 1.1.0 couldn't install either. I use ubuntu 9.10.

that's how it looks like:
[B]When I type in:

[/B]```
cd /root/headtracking/
```to switch to the directory

and after
```
make
```this prints out

[PHP]compiling : headtracking.c -> build/headtracking.lo
compiling : facedetect.c -> build/facedetect.lofacedetect.c: In function ‘headtrackThread’:
facedetect.c:264: error: too few arguments to function ‘cvRetrieveFrame’
make: *** [build/facedetect.lo] Error 1[/PHP]Please if somebody knows what may be the problem just give some instructions. 
Thank You !!

---

### Post by zenek89 on 2010-05-11
anybody who could help? Please...

---

### Post by chili555 on 2010-05-19
Can you please provide a link to the package you downloaded? I'd like to take a look at it.

---

### Post by zenek89 on 2010-05-19
[http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=snapshot;h=81046b1d3d9bc33af9bb4e6c56091c8b8a2754fa;sf=tgz](http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=snapshot;h=81046b1d3d9bc33af9bb4e6c56091c8b8a2754fa;sf=tgz)

this is the link for compiz plugin.

---

### Post by chili555 on 2010-05-19
I am stumped. I suggest you write to the developer.

---

### Post by zenek89 on 2010-05-20
Now on fresh installed Ubuntu 9.10 I'm getting different error. 

```
zenek@zenek-laptop:~/Downloads/headtracking$ sudo make
[sudo] password for zenek: 
compiling : facedetect.c -> build/facedetect.lofacedetect.c: In function &#8216;headtrackThread&#8217;:
facedetect.c:264: error: too many arguments to function &#8216;cvRetrieveFrame&#8217;
facedetect.c: In function &#8216;detect&#8217;:
facedetect.c:327: error: &#8216;CV_HAAR_FIND_BIGGEST_OBJECT&#8217; undeclared (first use in this function)
facedetect.c:327: error: (Each undeclared identifier is reported only once
facedetect.c:327: error: for each function it appears in.)
make: *** [build/facedetect.lo] Error 1

```

---

### Post by jmw86069 on 2010-06-14
From what I can tell, the function cvRetrieveFrame changed at some point to require the camera index number so it can discriminate multiple webcams.
See: *[OpenCV HighGUI Reference]("http://groups.inf.ed.ac.uk/teaching/sdp/archive/sysd2/opencv/latest_tested_snapshot/opencv/doc/ref/opencvref_highgui.htm")*

Also see: *[Blog.pwnage - Compiz headtracking]("http://blog.phpwnage.com/old_blog/article.php?id=44")*

You can either edit the code yourself, or download a working copy of the files to build.

**Edit the code yourself:**
If you only have one webcam, you can probably safely add ", 0" to line 264, so you change it
from:
```
frame = cvRetrieveFrame( capture );
```
to:
```
frame = cvRetrieveFrame( capture, 0 );
```

**Download a working copy of source code:**
*[headtracking-e79ef4df3292b5c98bc0673ea79577eb7b2cf5c7.tar.gz]("http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=snapshot;h=e79ef4df3292b5c98bc0673ea79577eb7b2cf5c7;sf=tgz")*
(On the Blog.pwnage page linked above, this link is found where it says "you have a newer OpenCV, please use this".

I have compiled the headtracking on 64-bit Lucid 10.04, and it works, though jumpy. I had to change a few settings:
Stacking->Window Depth: 5
Stack Padding: 0
Fade Time: 50
General->Height Adjustment: -23
Width Adjustment: 541
Tracker Vertical Angle: 0
Field of View Adjustment: 131 (very picky setting!)
Image scale: 17

The setting which made the most impact was Field of View Adjustment. It was freaky if I used 120 or 140, for example.

When you adjust settings, click the checkbox to enable headtracking, and **don't move the mouse!** You'll want to click again to disable it if things go freaky! When they go freaky, you won't be able to find the checkbox any more... Otherwise, Alt-F2 or Alt-T (terminal) and run "metacity --replace" to turn off compiz altogether. Good luck!

---

### Post by fattyz on 2010-06-21
just because i found this only thread on compiz, i am re installing 10.04 now because I got my desktop to completely vanish.  I could see a few things by banging on the keyboard like 4 blank screens, well not totally blank, still had the pretty colors. And I managed to do a screen capture which i could see after a reboot.

It should comeback after the reinstall because I deleted the partition but......  still kinda unstable here guys.  this is looking more and more like win 95 and the old blue screens of death.

I decided on a clean upgrade because 9.10 was getting buggy, had to keep rebooting it, all compiz issues.  I want special effects!

2 bad it makes the computer whack out.

FattyZ

---

### Post by fattyz on 2010-06-21
so im back up and running and get to start from scratch again.  and it still boots slower than 9.10 even with a clean install on my dell inspiron 600m.  I'll give it a try for a while, I was really hoping for better effects in compiz but, we'll see.

FattyZ

---

### Post by NIT006.5 on 2010-09-23
> **jmw86069 said:**
> Field of View Adjustment: 131 (very picky setting!)
...

The setting which made the most impact was Field of View Adjustment. It was freaky if I used 120 or 140, for example.


Any tips on exactly how you found 131 to be the ideal setting for you? There's such a large range that I don't really know where to start. When I try lower settings I get upside-down little windows appearing. On slightly higher values the windows just jump around all over the screen almost randomly. And in all cases, the desktop becomes totally unresponsive and I have to "blindly" run metacity --replace. I've spent days trying to find the right settings but nothing works as expected, and I've been unable to find any guides on "how" to go about tuning this.

Any ideas or pointers would be greatly appreciated :)

---

### Post by drewsus on 2010-11-16
So, whether I get it from git or from the "working copy" provided by jmw86069, I get this error when I run "**make**"
```
convert   : headtracking.xml.in -> build/headtracking.xml
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h/bin/sh: --header=build/headtracking_options.h: not found
make: *** [build/headtracking_options.h] Error 127
```

Anyone know what is up?

[CENTER]**[COLOR="SeaGreen"]----------------------------------------[EDIT]----------------------------------------[/COLOR]**[/CENTER]
found out that I needed to install another package:
```
sudo apt-get install compiz-fusion-bcop
```

furthermore, I wrote a little script for installing required packages (as far as I can tell) for **Ubuntu 10.10 Maverick Meerkat**. Pay attention to that, because the package names are different even in 10.04!
```
#!/bin/bash

sudo apt-get install git-core compiz-fusion-bcop build-essential cmake subversion libgtk2.0-dev pkg-config libpng12-0 libpng12-dev libjpeg62 libjpeg62-dev zlib1g zlib1g-dev libtiff4 libtiff4-dev libjasper1 libdc1394-22 libcv2.1 libcvaux2.1 libcvaux-dev libcv-dev libhighgui2.1 libhighgui-dev opencv-doc python-opencv 

if [ $? -eq 0 ];then
	git clone git://anongit.compiz-fusion.org/users/klange/headtracking

	cd headtracking

	#FROM THE COMPIZ WIKI:
	#Do not use sudo for these commands. They install the plugins to ~/.compiz/plugins and therefore do not require root privileges
	make

	make install
	exit 0
else
	echo "Headtracking for compiz was not downloaded, compiled or installed."
	echo "Aborting."
	exit 1
fi
```

However, I enable headtracking and the window field shows depth, but the perspective does not change if I move. The webcam is built in and working. 
*Any ideas?*

---

### Post by nshiell on 2011-03-07
Hi I really want to get this set up on my desktop.
Could you please help me through the errors in building this.

```
nicholas@saturn:~/headtracking$ sudo make
make: *** No rule to make target `build/headtracking.lo', needed by `c-build-objs'. Stop.

```

Many thanks

---

### Post by drewsus on 2011-03-07
did you see my script in the last post? If you are using maverick, use the commands there. if you are using lucid, let me know and I will post that script. You will need the packages I said to install. You will also NOT use "sudo make" just like it explains in my posted script. Please read it, do it, and report back.

---

### Post by nshiell on 2011-03-10
drewsus thanks for your reply I'm Using Ubuntu 10.10 Maverick Meerkat

I did try your script, I pasted it into a file called "head.sh"
I have re-run it and here is the output: -

```
nicholas@saturn:~$ sh head.sh 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
compiz-fusion-bcop is already the newest version.
libdc1394-22 is already the newest version.
libgtk2.0-dev is already the newest version.
libjasper1 is already the newest version.
libjpeg62 is already the newest version.
libjpeg62-dev is already the newest version.
libpng12-0 is already the newest version.
libpng12-dev is already the newest version.
pkg-config is already the newest version.
zlib1g is already the newest version.
zlib1g-dev is already the newest version.
libcv-dev is already the newest version.
libcv2.1 is already the newest version.
libcvaux-dev is already the newest version.
libcvaux2.1 is already the newest version.
libhighgui-dev is already the newest version.
libhighgui2.1 is already the newest version.
opencv-doc is already the newest version.
python-opencv is already the newest version.
cmake is already the newest version.
git-core is already the newest version.
libtiff4 is already the newest version.
libtiff4-dev is already the newest version.
subversion is already the newest version.
The following packages were automatically installed and are no longer required:
  python-evince libnss3-dev python-gnomedesktop python-metacity libnspr4-dev python-mediaprofiles python-bugbuddy python-totem-plparser timidity
  timidity-daemon python-gtop
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Initialized empty Git repository in /home/nicholas/headtracking/.git/
remote: Counting objects: 96, done.
remote: Compressing objects: 100% (94/94), done.
remote: Total 96 (delta 51), reused 0 (delta 0)
Receiving objects: 100% (96/96), 129.82 KiB, done.
Resolving deltas: 100% (51/51), done.
convert   : headtracking.xml.in -> build/headtracking.xml
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h
bcop'ing  : build/headtracking.xml -> build/headtracking_options.c
schema'ing: build/headtracking.xml -> build/compiz-headtracking.schemawarning: failed to load external entity "/schemas.xslt"
cannot parse /schemas.xslt
make: *** [build/compiz-headtracking.schema] Error 4
make: *** No rule to make target `build/headtracking.lo', needed by `c-build-objs'. Stop.
nicholas@saturn:~$ 
```

---

### Post by jmw86069 on 2011-06-20
This may or may not be helpful, but I abandoned this plugin about 1 hour after getting things built and working, with a halfway decent config.  Even for me, and I wanted badly for this to work like a Tom Cruise movie on crack, I liked the novelty for about 10 seconds -- then I still tried hard to like the novelty for another 10 minutes.  But I couldn't take the jiggity vertigo.  Turns out there's a reason that the Wii, Xbox360, and PS3 motion sensors use nothing at all like a webcam.  A valiant effort, but I think just too much to ask from a webcam.

I mean, you could try to play Dance Dance Revolution by wedging a keyboard under a tiled floor.  But there's got to be a better way. :-)

Is anybody here consistently using this plugin during their day-to-day computer use?

---

