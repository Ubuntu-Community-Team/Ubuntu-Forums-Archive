---
title: "Can't boot to Karmic Live CD"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by deamon_knight on 2009-11-21
I'm trying to clean install Karmic on a machine. I cannot boot to the Live CD, I get no video, My monitor acts like it is in sleep mode. I can switch to virtual console #1 and get a prompt. This is true for all variants K/X/Ubuntu live disks (Downloaded yesterday). I also installed from the Alt CD but had the same result. A 9.04 live CD works normally. This an older unit, P4 2.8GHz, 1GB RAM, Intel Mainboard, Nvidia GTS 7600. But since 9.04 works, I expected 9.10 to work as well. I saw this thread [http://ubuntuforums.org/showthread.php?t=1305459]("http://ubuntuforums.org/showthread.php?t=1305459") but this looked like mostly solutions to upgrades from 9.04 to 9.10 that went bad. Any suggestions on how to install fresh with this problem?

Thanks

---

### Post by barefootNH on 2009-11-21
I did a lot of research and I'm ready to upgrade from Microsoft. Last night I downloaded (bitTorrent!) 9.10 versions of Kubuntu, Ubuntu, and Kubuntu Alternate. I attempted to do fresh installs on a machine dedicated for the task (Athlon 900 MHz/ 512 MB RAM). (I checked the md5 and checked the live CD on a different, more modern computer to make sure they were OK.)

I booted to the language selection, but if I choose anything other than MemTest the screen goes blank with just a flashing cursor in the upper left corner. This exact same thing happens with each of the 3 aforementioned varieties.

I then tried the Wubi method, with both the version on the CD and straight from the web site, but it kept telling me that the disk drive was not ready, Cancel, Try Again, Continue. 

Windoze XP/SP3 runs just fine on this machine, so I'm really really surprised I can't get Ubuntu working.  I'm guessing that there is some very unique problem with my computer?

---

### Post by von Stalhein on 2009-11-21
I don't think it's your machine, at least not uniquely.

I've used Ubuntu since Edgy, and live cds have always booted, until Karmic.

Ubuntu by default uses open source NV drivers that seem to be a little bit inconsistent with some setups  i.e won't work!! You can use the proprietary drivers to get a GUI, but there's a bit of CLI work to do.

I tried with various builds of the Alternate CD and the Live CD - I could only install from the Alternate (text based install).

If you are still keen - have a look at this post, which worked for me: -

[http://ubuntuforums.org/showpost.php?p=8205792&postcount=28](http://ubuntuforums.org/showpost.php?p=8205792&postcount=28)

---

### Post by deamon_knight on 2009-11-21
I'm pretty baffled by this release, I've usually had excellent luck with the Live CDs unless some very odd hardware was involved. I have Karmic Running nicely on a newer board with an Ironically older Vidocard, so I'm really confused. This is all mainstram hardware. I rely on the live CDs as an Indicator but I've been using Ubuntu since 7.04 and I thought I could figure it out after trying a live CD, I may have to go back to 9.04.

Von Stalhein, I've seen several posts suggesting downloading the driver and installing manually will fix it, but won't this break after the next kernel patch?

---

### Post by von Stalhein on 2009-11-22
Oh yes,that's what happened when the next kernel came through.

Geez I laughed.

I'm not sure why it didn't have to be done with Jaunty though - the only fiddling I ever did there was with Grub to make sure the dual boot on this still worked.

Incidentally, the dual boot setup is borked here atm, but that's another story.

---

### Post by deamon_knight on 2009-11-22
Well, installing the Nvidia drivers worked, got me to a desktop. However, if the next kernel update breaks this, I'd hardly call this fixed.

---

### Post by von Stalhein on 2009-11-23
Oh, I'm treating the whole thing as a tremendous learning experience.  :D

---

### Post by deamon_knight on 2009-11-23
Agreed, but at some point I'd like to be able to use the system as a desktop rather than an Ubuntu troubleshooting platform.

---

### Post by von Stalhein on 2009-11-24
I'm laughing on the inside when I need to reconfigure the graphics after a kernel upgrade.

I'm also losing the argument with my partner when she asks me why it doesn't "just work".

Perhaps I have masochistic tendencies. 

A new release will be along soon.........

---

### Post by deamon_knight on 2009-11-24
What is really killing me is that Karmic installed on an another less powerfull system! Between the software updates/polish that were included in Karmic and my finally understanding some of the Multimedia How-tos (and aquiring a reasonably powerful second system) I thought now was a real chance to move entirely over to Ubuntu! And now Karmic Just won't play nice.

---

### Post by von Stalhein on 2009-11-25
> **deamon_knight said:**
> What is really killing me is that Karmic installed on an another less powerfull system! Between the software updates/polish that were included in Karmic and my finally understanding some of the Multimedia How-tos (and aquiring a reasonably powerful second system) I thought now was a real chance to move entirely over to Ubuntu! And now Karmic Just won't play nice.

I use Windows less and less. Unfortunately the rest of the family does not will not and is not.

It's vexing to say the least - especally since I've had bugger-all issues from Fiesty onwards.

Maybe I have to wait for Obstinate Ox (TM)

---

