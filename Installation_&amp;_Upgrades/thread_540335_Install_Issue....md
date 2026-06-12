---
title: "Install Issue..."
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by svtguy88 on 2007-09-01
I'm trying to install Ubuntu to my laptop (dual boot with Vista on the same drive).  I insert the Live CD that I downloaded and burned, and the splash screen loads, I select "Install" and another splash sreen comes up.  After a few seconds, I get a BusyBox console and a message saying "can't access tty;  job control turned off."  

I thought maybe my CD was bad, so downloaded another one.  The first one is the 64bit version, and the second one I tried was the 32bit one.  Both give me the same error.  My laptop supports 64bit computing, so I'd like to use the first one.  Here is my hardware, in case you were wondering:  Toshiba A200, C2D T7300, 2gb RAM, 128mb ATI HD2400, 120gb HD.

---

### Post by LordSoretor on 2007-09-01
I have the exact same problem with a Core2 6420 on a MSI P35 Platinum motherboard. As far as I think (it's the first time I ever want to start a Linux LiveCD), it isn't a SATA problem, or a 32/64 bit compatibility problem.

I'm still looking for the solution myself. I hope we both can find it. The funny thing is I was trying to convince my girlfriend to switch to Linux, but when I tried to run it hangs! So much for the conversion...

---

### Post by kellemes on 2007-09-01
Maybe you'll find a solution here?
[http://ubuntuforums.org/showthread.php?t=421588]("http://ubuntuforums.org/showthread.php?t=421588")

---

### Post by svtguy88 on 2007-09-02
I tried the process that is listed in the first post of the above thread, but couldn't get it to work.  It says to hit F6 for options, then add "break=top" to the options.  I typed it at the beginnning and also tried the end of the line of "options" that comes up, but it doesn't change anything.  Live still tries to boot, kicks me to the same error as before and leaves me with a initramfs prompt...

---

### Post by LordSoretor on 2007-09-03
I solved it. After trying the Ubuntu alternate CD, at some point told me that wasn't able to mount the CD ROM (actually I think it doesn't detect the motherboard chip that controls the IDE). So I looked for a way to put the Ubuntu Live CD on a flash drive, found it in [http://www.pendrivelinux.com](http://www.pendrivelinux.com).

With the flash drive it works OK (it doesn't detect my network card either, but hey, at least it works now).

Check if it works for you. Good luck.

---

### Post by svtguy88 on 2007-09-03
I figured out that by adding "break=top" to the options for boot up (WAY in the beginning of the other options) and then following the other steps outlined on the link above, it works.  I can now boot into Ubuntu and Vista without any issues.  However, my wireless card isn't recognized.  It is an Intel 4965, but the drivers for the 3945 are supposed to work (which are apparently built into Ubuntu already).....any ideas?

---

### Post by Pumalite on 2007-09-03
Try 'Networking'. Better and faster answers on the subject.

---

### Post by svtguy88 on 2007-09-03
Will do....

---

