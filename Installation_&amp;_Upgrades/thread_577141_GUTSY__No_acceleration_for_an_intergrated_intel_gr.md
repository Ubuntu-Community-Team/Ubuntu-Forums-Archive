---
title: "GUTSY:  No acceleration for an intergrated intel graphics card"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by wonkycyber on 2007-10-15
Yo.  I'm running a Dell Inspiron e1705.  After some recent troubles, I needed to reinstall my ubuntu; deciding to give gutsy a whirl since it's the cool thing to do these days, I did so.  However, I've had a strange and pretty drastic issue pop up -- hardware doesn't seem to be accelerated.  My windows lag like an old windows box and video files skip aroudn all over the place.  It's quite noxious, really -- wherein I could run Beryl with great beauty over on edgy, gutsy makes the comp kind of painful.

I figure this is a pretty common graphics card, so this is a problem that may want to get poked at -- let me know if there's sany info yhou need, and I can post here.

---

### Post by sumsar on 2007-10-16
Yepp, i second that. 

After upgrading to Gutsy from Feisty it's like running Vista on a PII I guess.Things like scrolling down in Firefox is really painfull. You can really see how the page is redrawn. If anybody has a clue how to help with this issue I'm dying to know. 
I'm Running a Toshiba Statelite Pro M70 with an intel 915 graphics card though the graphics driver in the System -> Administration -> Screens and Graphics defaults to i810...

---

### Post by sumsar on 2007-10-16
...Even stranger...
Now I rebooted a second time and at startup, before login, i get a window saying it can't recognize my graphics driver. I click OK and now everything works except visual effects wich actually worked before( but were of course painfully slow, should also mention that visual effects worked like a charm in Feisty)

---

### Post by ashkev on 2007-10-18
I am also having this issue.  I am running the integrated graphics from an intel 965ry board.  Beryl worked fine in Feisty, but in Gutsy, none of the visual effects work.  I am also running Gutsy on an HP ZV5000 with no problems.

---

### Post by sdowney717 on 2007-10-18
I have had major trouble with an ATI 9600.
I think enough people have been complaining that it is likely to get noticed and eventually fixed. With feisty it was working. They seem to have eliminated XGL sessions and somehow put the XGL stuff as default. So I have to run compiz-fusion to get any decent video response .

---

### Post by rmx.dave on 2007-10-18
I am also having this problem with Sony Vaio FJ170 laptop and the i810 driver. SLOW AS CAN BE!

---

### Post by ebichete on 2007-10-18
It is likely your hardware fell foul of the Ubuntu compiz blacklist.

To ensure a quality experience when compiz is enabled by default, the Ubuntu developers blacklist a video card (actually PCIID) that is known to crash in **NORMAL** usage. (Note that normal usage is almost but significantly not the same as common usage).

As an example some video cards (and associated drivers) run great until you try to watch a video (using XVideo) and do the visual effects at the same time, then kaboom. Or some other combination, like games that use GL_TEXTURE_INDIRECT. The blacklisting may annoy users who never do such things but it is better than crashing unexpectedly. The blacklist will be updated as the drivers are updated with bugfixes. So there is a chance that one day your desktop will suddenly turn all bouncy and happy.

However if you are a savvy user and know you won't hit the buggy combination (or just don't care) you can bypass the blacklist. Just run this at the terminal:

```
echo SKIP_CHECKS=yes > .config/compiz/compiz-manager
```

---

### Post by sdowney717 on 2007-10-18
why do I still have to run compiz --replace or my system is so slow typing in firefox  glxgears, etc....

---

### Post by sdowney717 on 2007-10-18
without typing compiz --replace
scott@scott-desktop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
5789 frames in 5.0 seconds = 1149.304 FPS
6215 frames in 5.1 seconds = 1223.607 FPS
6102 frames in 5.0 seconds = 1214.805 FPS
5311 frames in 5.1 seconds = 1041.072 FPS
X connection to :1.0 broken (explicit kill or server shutdown).

scott@scott-desktop:~$ 
after typing compiz --replace
scott@scott-desktop:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
11414 frames in 5.0 seconds = 2282.727 FPS
12194 frames in 5.1 seconds = 2376.146 FPS
11923 frames in 5.0 seconds = 2384.503 FPS
13230 frames in 5.0 seconds = 2645.886 FPS
15235 frames in 5.0 seconds = 3042.688 FPS

---

### Post by TheBuzzSaw on 2007-10-18
Google Earth worked just fine under Feisty Fawn. In the Gutsy Gibbon beta, Google Earth barely functions. This graphics issue really needs to be addressed. (I have a Darter Ultra which uses the integrated graphics.)

---

### Post by sdowney717 on 2007-10-18
root@scott-desktop:~# glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
15606 frames in 5.0 seconds = 3121.185 FPS
24058 frames in 5.0 seconds = 4807.102 FPS
25953 frames in 5.0 seconds = 5184.851 FPS
25877 frames in 5.0 seconds = 5175.201 FPS
25953 frames in 5.0 seconds = 5183.912 FPS
25953 frames in 5.0 seconds = 5182.267 FPS
25388 frames in 5.0 seconds = 5074.130 FPS

I just changed composite in xorg.conf from "Disabled" to "1" and my glxgears went up a lot

---

### Post by ashkev on 2007-10-18
I tried to disable the blacklist and I got the following:

kevin@edubuntu:~$ echo SKIP_CHECKS=yes > .config/compiz/compiz-manager
bash: .config/compiz/compiz-manager: No such file or directory
kevin@edubuntu:~$ compiz -replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -replace
kevin@edubuntu:~$

---

### Post by sdowney717 on 2007-10-19
I think you have to install the xgl server

scott@scott-desktop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by ashkev on 2007-10-19
That did it!
```

sudo apt-get install xserver-xgl
```

Then Restart....and all is good now.

---

### Post by svicente on 2007-10-20
Same problem here with and Intel 945 and I wasn't using Beryl or Compiz :(

All scrolling is sluggish and windows take time to be drawn. All was working fine before update.
This makes impossible to browser or almost impossible to even work.


Also on some places (window's titles, some menus...) , spaces turn into some kind of dots :|


P.S.: I am using Kubuntu and I already had xserver-xgl installed.


**SOLUTION**
Well... the possible and most ugly one (like in use a hammer to kill an ant), but quite pratical for people who don't have the time to pinpoint the problem: remove X, KDE removes too auto, and reinstall both (with Adept Manager is quite easy) and everything is working fine, took less than 15 minutes.

---

### Post by sumsar on 2007-10-20
Ok i guess lots of people have problems with their graphics card. But if you have an integrated Intel Card, such as 915, this could be the souloution:

[http://ubuntuforums.org/showpost.php?p=3416144&postcount=15](http://ubuntuforums.org/showpost.php?p=3416144&postcount=15)

Worked for me at least :)

---

### Post by dkarnows on 2007-10-22
I also had the same problem (integrated Intel graphics chip that had hardware acceleration stop working following upgrade to Gutsy). I also fixed the problem by uninstalling xserver-xgl.

---

### Post by markballermann on 2007-10-22
I had problems with compiz when trying to upgrade from feisty with beryl. I have an intel 915 (dell latitude X1) that now works with gutsy/compiz. Knowing what I know now, I would highly recommend going the fresh install route:

After the upgrade to gutsy, compiz wasn't working by default. Enabling compiz in preferences>appearance resulted in 'desktop effects could not be enabled'. Tried several different things:

Installing xserver-xgl -worked, but was painfully slow. Screen would refresh 1-2 Hz. Removed xserver-xgl, doesn't appear to be appropriate for the intel 915.

Running compiz --replace at the command line gave a variety of errors, some related to it not finding the correct version of libwnck. Found some tutorials that said you should use some additional command line switches to get it running, which I did, to a point where it would not crash immediately, but..

Finally after getting all the command line errors to go away (except for one that said 'no stenciling buffer' which I read is not important) the window contents would not update at all (in any window). For example, bringing up a terminal window gave a white screen, no login "$" prompt, but if I blindly type in 'killall compiz' the windows would update normally again.  Compiz was running, if I clicked on the window's entry in the taskbar, the zoom effect would kick in and out (with blank windows). Fun!

Couldn't find anything else at this point that would help, so I did the fresh install. And now it 'just works' (compiz and a laundry list of other problems has just gone away). From this, I think that the intel 915 isn't blacklisted. If you're on the upgrade path and trying to find out how to get it working, you may find just going over to the fresh install is the way to go.

I've been happy with upgrades forever (one server I have upgraded from warty>hoary>breezy>dapper) and my laptop was upgraded from dapper>edgy>feisty and now fresh install to gutsy. I'd submit bug reports for all this, but I just don't have time. 

Go with the fresh install, if you're not already trying that :)

Hope this saves someone some time.

---

### Post by TheBuzzSaw on 2007-10-22
> **sumsar said:**
> Ok i guess lots of people have problems with their graphics card. But if you have an integrated Intel Card, such as 915, this could be the souloution:

[http://ubuntuforums.org/showpost.php?p=3416144&postcount=15](http://ubuntuforums.org/showpost.php?p=3416144&postcount=15)

Worked for me at least :)
This helped immensely! Google Earth is back to its old self!

What does that xserver-xgl thing do anyway? What is it for?

---

### Post by bricedebrignaisplage on 2007-11-07
I had the same problem (slow display with intel 945) and uninstalling xserver-glx solved it.

---

