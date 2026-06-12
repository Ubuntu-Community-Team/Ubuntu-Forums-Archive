---
title: "DOS Installation to a USB Drive"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by and003 on 2011-09-23
A few years ago, before I converted to Linux, I was using an old computer that an office suite called New Deal Office. It was designed for old computers like those that used the original Pentium processor and DOS ... in my case, Caldera DR-DOS.

Even though I am fully committed to using Linux, I am interested in using the files I created using New Deal Office. I am trying to see if I can install such software on an old Seagate hard drive I converted to USB 2.0 by way of a VanTec NexStar3 NST-360U2-BK Hard Drive Enclosure.

Even though I'm working on an idea of my own, I am interested in information about how to use Ubuntu to install DOS software on a USB drive.

---

### Post by haqking on 2011-09-23
> **and003 said:**
> A few years ago, before I converted to Linux, I was using an old computer that an office suite called New Deal Office. It was designed for old computers like those that used the original Pentium processor and DOS ... in my case, Caldera DR-DOS.

Even though I am fully committed to using Linux, I am interested in using the files I created using New Deal Office. I am trying to see if I can install such software on an old Seagate hard drive I converted to USB 2.0 by way of a VanTec NexStar3 NST-360U2-BK Hard Drive Enclosure.

Even though I'm working on an idea of my own, I am interested in information about how to use Ubuntu to install DOS software on a USB drive.

You could use virtualbox to setup a DOS virtual machine ?

There are also a few emulators out there, DOSEmu is one, DOSBox etc

[http://www.dosbox.com/download.php?main=1](http://www.dosbox.com/download.php?main=1)

[http://www.dosemu.org/](http://www.dosemu.org/) (out of date)

---

### Post by papibe on 2011-09-23
Additionaly to haqking's suggestions you can also try [FreeDOS]("http://www.freedos.org/").

Regards.

---

### Post by haqking on 2011-09-23
> **papibe said:**
> Additionaly to haqking's suggestions you can also try [FreeDOS]("http://www.freedos.org/").

Regards.

isnt FreeDos like any other DOS, its not for running DOS software within linux ? it is not a emulator, requires a VM or own Partition right ?

---

### Post by and003 on 2011-09-29
I found something that enabled me to address one part of my plan. There's this guy named Bob Rankin, who has a web site dedicated to Linux and anything associated with it. Part of his site concerns the ability of Linux to handle DOS programs.

Basically, the solution he formulated enabled me to mount the DOS partition on my USB-converted Seagate drive as I would if a DOS partition was on a regular hard drive.

His solution is detailed here:
[http://lowfatlinux.com/linux-dos-partition.html](http://lowfatlinux.com/linux-dos-partition.html)

Now I need to find a way to install DOS software on to my USB drive's partition. I tried using DOSemu but as yet have been unable to make it work properly, i.e. unable to use DOSemu to install software on a USB drive. For some reason, DOSemu keeps asking for an installation disk even though the installation disk is already in the drive.

---

### Post by and003 on 2011-12-08
I used FreeDOS and it works for me. I wish to thank everyone, papibe in particular, for their suggestions. :)

---

