---
title: "Ubuntu installs with erasing disk but still somehow boots to Windows"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by King Big Ben on 2011-09-24
Hey everybody,

I just dug out an old tower i had with one of the first gen 64 bit Athlon processors on it. I wanted to wipe windows off completely and install 64 bit Ubuntu. I booted from the cd, tested it out a bit, then ran the install. I chose to "erase disk and install Ubuntu." The install ran flawlessly. When I rebooted the machine, however, it boots straight back into windows (which should have been wiped off). I go to install Ubuntu again and it acts as though it installed fine, and I go to manually change partitions and it reads as though it was properly installed before, and there are no extra partitions. It's been a while since I've messed with different OS's and partitions, so any help is much appreciated.

Thanks in advance,

-Ben

---

### Post by searchfgold6789 on 2011-09-24
Seriously? :lolflag:
I guess I would try simply removing the Windows partition using the Live CD *first*, then install Ubuntu, if everything else is working. You may use a different Live CD, such as the grub rescue disk or even better the Paragon HD Manager (always get the Server Edition of this, it's much awesomer).

---

### Post by OpenJacob on 2011-09-24
To completely remove Windows you must run a partitioning software such as fdisk, Gparted... which comes standard in Ubuntu and reformat the drive.

To dualboot Win with Lin you can have a look at this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by King Big Ben on 2011-09-25
I actually figured it out...I forgot I had an external hard drive plugged in, and Ubuntu wasn't listing my internal hard drive...so I ended up installing Ubuntu to my external. My new problem is I can't figure out how to get it to recognize my internal hard drive as something to install to. I'll search around and see if I can find an answer, otherwise I'll start a new thread.

Thanks,

-Ben

---

