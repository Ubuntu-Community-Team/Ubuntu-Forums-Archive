---
title: "Live Linux bootable from HDD?"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by imWACC0 on 2010-06-11
I have a Pentium 1 laptop*, that I could use right now. But it's so old  that it will not boot from USB, CD/DVD or network.

The problem is I don't have a floppy drive for it any more. Is there a  way to put a live CD and/or USB onto a HDD so that I can boot from that?  Any other ideas?

 [FONT=Arial Narrow][SIZE=1]I'm probably not using a the right technical words, but I  hope I get the idea across
*Compaq LTE 5200, docking station, 72 megabytes RAM and 120MHz CPU, if  it matters[/SIZE][/FONT]

---

### Post by arrange on 2010-06-11
This link might help you
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by pytheas22 on 2010-06-11
If the link posted above doesn't help you, you can also use grub2 to boot an ISO image installed on a hard disk.  You can find instructions for doing so on Google; if you need help let us know.

Also, if this computer is a Pentium I, which kind of Linux are you trying to boot?  Ubuntu almost certainly wouldn't boot because you probably only have something like 16 megabytes of memory; you'd need many times that for an Ubuntu live CD.  [Damn Small Linux]("http://www.damnsmalllinux.org/download.html") might work or something along those lines might work, however, although I'm not sure whether you'd be able to run a graphical environment.  But you can try.

Also keep in mind that rather than booting to a live CD to install Linux on this computer, you could just remove its hard disk, attach it to another machine, install Linux to the hard disk there, and then move it back to the Pentium I.  On most Linux distributions this should work.

---

### Post by imWACC0 on 2010-06-11
[FONT=Arial Narrow][SIZE=2]My short list right now is:
[/SIZE][/FONT]
[LIST]
[*]Xubuntu 10.04
[*]Lubuntu 10.04
[*]Damn Small Linux (and/or Not)
[/LIST]

Also, just in case:

[LIST]
[*]FreeDOS
[*]Ultimate Boot CD
[/LIST]

[FONT=Arial Narrow][SIZE=2]
Compaq LTE 5200, docking  station, **72 megabytes RAM** and 120MHz CPU, 1mb for video


I have run XP on it quite a few years back...  but trying to stay away from that!
[/SIZE][/FONT]

---

### Post by snowpine on 2010-06-11
> **imWACC0 said:**
> I have a Pentium 1 laptop*, that I could use right now. But it's so old  that it will not boot from USB, CD/DVD or network.

The problem is I don't have a floppy drive for it any more. Is there a  way to put a live CD and/or USB onto a HDD so that I can boot from that?  Any other ideas?

 [FONT=Arial Narrow][SIZE=1]I'm probably not using a the right technical words, but I  hope I get the idea across
*Compaq LTE 5200, docking station, 72 megabytes RAM and 120MHz CPU, if  it matters[/SIZE][/FONT]

Welcome to the forums! Unfortunately, your system is far, far below [the recommended minimum hardware requirements for Ubuntu]("https://help.ubuntu.com/community/Installation/SystemRequirements"):

> # 1 GHz x86 processor
# 1 Gb of system memory (RAM)
# 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
# Graphics card and monitor capable of 1024 by 768
# Either a Cd/Dvd-drive or a Usb socket (or both)
# Internet access is helpful 

You are even below the minimum for a command-line text only server install, therefore Xubuntu and Lubuntu are certainly out of the question:

> # 300 MHz x86 processor
# 128 MiB of system memory (RAM)
# 1 GB of disk space
# Graphics card and monitor capable of 640x480
# CD-ROM drive

Ubuntu (including its derivatives) really is a wonderful operating system for modern computers; I hope someday you are able to upgrade your hardware and experience for yourself. :)

---

### Post by imWACC0 on 2010-06-11
[FONT=Arial][SIZE=2]Thank you Snowpine, do you know anything that will run on [/SIZE][/FONT][FONT=Arial][SIZE=2]72 megabytes RAM and  120MHz CPU, 1mb for video?

If I can get **any** OS to run on it, I should be able to install others


[SIZE=1]P.S. I guess I should have said this will be in the bedroom to stream audio from my Dell Poweredge Server (4x550MHz Xeon[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=1], 8g ECC, 6 SCSI) that is running Ubuntu headless. Or my main system (ASUS, Quad 2.9, 4g). Or for that matter the test server running Amahi/Fedora. Or... Or... Or.......  8-[[/SIZE][/FONT]

---

### Post by snowpine on 2010-06-11
> **imWACC0 said:**
> [FONT=Arial][SIZE=2]Thank you Snowpine, do you know anything that will run on [/SIZE][/FONT][FONT=Arial][SIZE=2]72 megabytes RAM and  120MHz CPU, 1mb for video?

If I can get **any** OS to run on it, I should be able to install others


[SIZE=1]P.S. I guess I should have said this will be in the bedroom to stream audio from my Dell Poweredge Server (4x550MHz Xeon[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=1], 8g ECC, 6 SCSI) that is running Ubuntu headless. Or my main system (ASUS, Quad 2.9, 4g). Or for that matter the test server running Amahi/Fedora. Or... Or... Or.......  8-[[/SIZE][/FONT]

I have no experience installing Linux on anything that old, sorry. Puppy, TinyCore, SliTaz, and DSL are the "lightest" distros that I have tried, hope that helps point you in the right direction. Personally I would recycle the Pentium 1 and buy an iPod. ;)

---

### Post by pytheas22 on 2010-06-11
72 megabytes of memory isn't bad...I guess I had forgotten what the average was back in the Pentium I days.  I've run DSL on machines like that without much of an issue.  As long as you can figure out a way to boot it, I'd give that a try.

The other lightweight distributions mentioned by snowpine may also work well; I've never tried them.  I like DSL because it's Debian-based and allows you to install apt, and once you get that running it's very easy to install software.

---

### Post by imWACC0 on 2010-06-11
> **pytheas22 said:**
> 72 megabytes of memory isn't bad...average back in the Pentium I days. 

Something has to run on it, there were Linux distros back in 2000
Might have to be Damn Small Linux (and/or Not), all the other ones I've looked at require more/better systems.

---

