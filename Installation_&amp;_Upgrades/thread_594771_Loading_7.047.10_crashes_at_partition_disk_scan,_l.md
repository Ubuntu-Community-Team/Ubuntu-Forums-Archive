---
title: "Loading 7.04/7.10 crashes at partition disk scan, logical sector 2048"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Rebajas on 2007-10-28
Afternoon everyone,

I'm trying to load either 7.04 Live CD or 7.10 alternative installer onto an old P3 based machine. It has a Celeron 1400Mhz processor, 256 Mb of RAm and a 160Gb Hitachi drive that I went out for only yesterday.

Using the alternative text install the machine dies when partitioner tries to scan the disk at 36%.

The error was proceeded by a warning:

```
Device /dev/sda has a logical sector of 2048. Not all parts of 
GNU Parted support this at the moment, and the working code is HIGHLY 
EXPERIMENTAL.
```

I have changed the BIOS setting for the drive to LBA as suggested elsewhere in the forum but this hasn't made a difference. What other options do I have?

Thanks in advance.


Tony.

---

### Post by Rebajas on 2007-10-28
Would you believe it - unplugged my ipod shuffle and all works (so far).

Bug report logged at offers more info, enough to get me passed GO! anyway:
[http://lists.debian.org/debian-boot/2007/04/msg00770.html](http://lists.debian.org/debian-boot/2007/04/msg00770.html)


Thanks - another user converted to Linux ;)

---

### Post by Pumalite on 2007-10-28
You cannot boot a Live CD with 256 MB os RAM, unless you make 500 MB /swap partition ahead of time, Even if you manage to install, the OS would be too heavy for your system. I advise: Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by Rebajas on 2007-10-28
Hi Pumalite,

Said machine has had XP running on it with Norton AV - if it runs faster than that then I will be happy.

I'm installing 7.10 using the text installer, taking a while but hopefully it will be fine. Got a 666Mb swap now as well.

What do you reckon?

---

### Post by Rebajas on 2007-11-03
Well - the machine has been running fine for week and my partner is a very happy convert. Still got some set up to do but so far so good.

Ta.

---

### Post by Pumalite on 2007-11-03
If you are happy; I'm happy.

---

### Post by Rebajas on 2007-12-15
I'm happy, and even more important than that, my GF is very happy with Ubuntu.

The main reason for doing this was that XP was slowing down her Christmas shopping - even using Firefox she was getting frustrated, she seems to think everything is much faster now.

Thanks.

---

