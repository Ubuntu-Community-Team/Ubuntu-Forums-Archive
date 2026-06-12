---
title: "Install Problems with 7.04"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by mabreaux on 2007-07-16
I have tried both Ubuntu and Kubuntu ISO to CD install and am receiving the same error.  I know the CD are good since I install it on a different machine. 

The Error is as follows:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3)
Built-in Shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off.
(initramfs)

-----------------------------

Is there a work around for this and if so how do you do it.
The same error occurs on both Ubuntu and Kubuntu iso's 
This error occurs when booting from the CD's burned with the ISO images of the OS.

Michael

---

### Post by Pumalite on 2007-07-16
Read all this:

[http://www.linuxforums.org/forum/linux-programming-scripting/13921-bin-sh-cant-access-tty-job-control-turned-off.html](http://www.linuxforums.org/forum/linux-programming-scripting/13921-bin-sh-cant-access-tty-job-control-turned-off.html)

[https://answers.launchpad.net/ubuntu/+question/173](https://answers.launchpad.net/ubuntu/+question/173)

[http://ubuntuforums.org/showthread.php?t=292533](http://ubuntuforums.org/showthread.php?t=292533)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)

[http://www.mail-archive.com/edubuntu-devel@lists.ubuntu.com/msg01448.html](http://www.mail-archive.com/edubuntu-devel@lists.ubuntu.com/msg01448.html)

See what you make of it. It still puzzles me.

---

### Post by mabreaux on 2007-07-16
I tried to install kubuntu 6.06 lts and is worked fine, what is wrong with the install for 7.04?

Change I upgrade from 6.06 to 7.04?  If so, how?

---

### Post by M0rtii on 2007-07-17
[QUOTE=
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3)
Built-in Shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off.
(initramfs)
l[/QUOTE]

I just downloaded the Xubuntu 7.04 image and burned it using InfraRecorder.  I'm getting this same message when I go to install it on my machine or even just when checking the CD for problems.  I've downloaded the image twice and burned it twice already with the same results each time.

I was able to install Ubuntu Server Edition 7.04 yesterday, so I know my machine works.  I want to switch to xubuntu simply because I need the visuals.

Dell Power Edge 1400sc
Dual Intel P3 667 Mhz CPUs
1 GB RAM
18.2 GB SCSI Hard drive with ID set to 0

Like I said, I just successfully installed the Server Edition and had Windows 2K Pro running before that.

Any help would be great.  This is my first foray into Linux and I have no idea what that means.

---

### Post by merlinus on 2007-07-17
IIRC, you can install xubuntu from server:

```

sudo aptitude update && sudo aptitude install xubuntu-desktop

```

-merlin

---

