---
title: "Lubunt 12.04 Alternate install taking too long"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by BigBig5 on 2012-10-12
I'v been installing Lubuntu 12.04 Alternate and it been going at least 10 hours, but going through all the steps. Not that long before I installed Lubuntu 10.04 and the install didn't take long. So what would be wrong?
Dell Optiplex GX
252mb ram
40G hard drive.

---

### Post by mörgæs on 2012-10-12
There is not enough memory on the computer. 

Is it a GX150, by the way?

---

### Post by Lyfang on 2012-10-12
"Computers with less than 700 MB of RAM are considered low-RAM computers." - [Lubuntu/Alternate_ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") 

"installs on systems with less than about 384MiB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably)." - [Lubuntu 12.04 (Precise Pangolin)]("http://cdimages.ubuntu.com/lubuntu/releases/precise/release/")

See also: "How to install Ubuntu on low memory systems (Pentium III and earlier machines, with 32-192 MB RAM)." - [Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by BigBig5 on 2012-10-12
I solved it. It was the CPU speed in the BIOS, it must of got change. So its working find now.

---

### Post by Lyfang on 2012-10-12
So do you think 256MB RAM is enough for running Lubuntu 12.04?

---

### Post by mörgæs on 2012-10-12
Good you got it solved. It surprises me that such a small amount of RAM is enough.

I have been playing with a gx150 (with 512 MB) the last couple of days. In case you want to keep experimenting:
[http://ubuntuforums.org/showpost.php?p=12292664&postcount=828](http://ubuntuforums.org/showpost.php?p=12292664&postcount=828)

---

### Post by Lyfang on 2012-10-13
Two Fujitsu Siemens, computers given or thrown away by now. I think the specification was:

800 MHz, maybe 384 MB RAM upgraded, Windows ME, installed Ubuntu 8.04 LTS  with GNOME. Slow!  With OpenBox ok(?). Using Adobe Flash Player with Chromium was possible the cause of several Kernel Panics (could have also been failing hardware)!

333 MHZ Celeron that won't boot a CD drive, maybe 192 MB RAM upgraded, Windows 98(?), installed Ubuntu 8.04 LTS with GNOME. Slow! Tried Debian, 6.0.1 (Squeeze). See also: [Corrupt screen, HP Brio, Matrox G100 (display: NEC LCD1860NX and others)]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/393129")
[IMG]http://img.ps2netdrivers.net/img/77/fujitsu.siemens.scenic.xb/small.jpg[/IMG]
Linux kernel has many drivers built in. Linux had once only 10,000 lines of code (September 1991). Has Ubuntu gotten more bloated with recent releases?

---

### Post by marinara on 2012-10-14
lubuntu seems to run ok in a 128MB vm, as long as you don't use chromium, as which point it starts swapping.

---

### Post by Rex Bouwense on 2012-10-15
I have never installed or run Lubuntu on a machine with less than 512 RAM, but I have read that it can be done with 128.  With RAM so inexpensive and available, I would guess not many people are installing with that size any more.

---

