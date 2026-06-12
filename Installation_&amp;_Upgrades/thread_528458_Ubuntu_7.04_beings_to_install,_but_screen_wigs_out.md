---
title: "Ubuntu 7.04 beings to install, but screen wigs out"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Zeron0 on 2007-08-17
OK, here is the situation:

I insert my CD fine, and it gets to menu screen. After I select install, It goes to the bouncy bar, and then then to the loading bar. After that, the screen flickers a few times then I see a bunch of white and green lines. It happens with Ubuntu and Kubuntu, I haven't tried XUbuntu. I tried different video modes, but they all give some weird , severely off-center screen, or a combo of both the lines and off-center.

Specs:
Nvidia 6600
Intel Celeron C1
2 Gb Physical RAM (forgot the name, sorry >_<)
MSI MS-679 (Mobo)

Hope that little bit of info helps. I assume it is a video card issue, but both Mandriva and Slackware boot with no problem. I can't even get to the install screen with this.

Thanks for your time and help.

---

### Post by merlinus on 2007-08-17
Have you tried Safe Video Mode from the startup menu?

-merlin

---

### Post by Zeron0 on 2007-08-17
i've tried all the modes and they all do the same thing, just different variations of it.

---

### Post by merlinus on 2007-08-17
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.  And it will not be prey to video card problems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by Zeron0 on 2007-08-17
ok, scratch everything I have said. For some reason, Safe made started to work.

Oh well. Computers are like people. They work when they want to.

Thanks for the help!

---

### Post by splintercellguy on 2007-08-17
After installing, you will most likely want to do sudo dpkg-reconfigure xserver-xorg in Recovery Mode to get the display working.

---

