---
title: "Cannot boot live/alternate CDs (Get initramfs prompt)"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phyrewall on 2009-10-08
Ever since Karmic Alpha 5, all CDs that I've burnt (all types, all formats, all MD5 check correct) have failed when I try to run either "Try Ubuntu without changes" or "Install Ubuntu" with this mess:


```
Begin mounting root filesystem...   ...
cp: can not create '/root/var/log/': No such file or directory.
cp: can not create '/root/etc/': Is a directory.
Done.
Begin: Running /scripts/init-bottom...
mount: mounting /dev on /root/dev failed: No such file or directory.
Done.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: mounting /proc on /root/proc failed: No such file or directory.
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.


Busybox (blah, blah blah)


(initramfs)

```(Bear with me, I had to hand copy and type it, can't get it to reproduce in a virtualbox.)

Here's my system in a nutshell:
Alienware M9750 laptop, has run Ubuntu H and J flawlessly.
Intel Core 2 Duo
Two 200G HDD on SATA RAID0, dual boot with win7 in 1st P partition
Two NVIDIA 7950 GTX sli
HDA Intel High Def audio and a Opti DVD/RW


Any ideas? Please help, I really miss my Ubuntu! (Working on the Win 7 boot side, yuck.)

Thanks!

---

### Post by psyke83 on 2009-10-08
Maybe your burning software is to fault.

You could try to create a Live USB image using the "USB Startup Disk Creator".

---

### Post by phyrewall on 2009-10-08
I've used multiple OSs, programs, and computers. I get the same error via USB stick as well.

---

### Post by VMC on 2009-10-08
It's been a while since I booted livecd, but have you tried either the save mode or boot with nomodeset on kernel line.

---

### Post by phyrewall on 2009-10-08
> **VMC said:**
> It's been a while since I booted livecd, but have you tried either the save mode or boot with nomodeset on kernel line.

Just tried,  doesn't seem to change anything. I thought these were graphics related settings?

---

### Post by phyrewall on 2009-10-09
> **phyrewall said:**
> Just tried,  doesn't seem to change anything. I thought these were graphics related settings?

  Shameless self-bump, since I HAVE NO UBUNTU AND I MUST SCREAM!  Seriously, I'm withering away here... I guess I should just install Jaunty and do a dist-upgrade, but I thought a clean install was the only way to truly get Karmic's benefits? Correct me if I'm wrong, and I'll just go ahead with that plan.  Please help me, thanks!

---

### Post by VMC on 2009-10-09
> **phyrewall said:**
> Shameless self-bump, since I HAVE NO UBUNTU AND I MUST SCREAM!  Seriously, I'm withering away here... I guess I should just install Jaunty and do a dist-upgrade, but I thought a clean install was the only way to truly get Karmic's benefits? Correct me if I'm wrong, and I'll just go ahead with that plan.  Please help me, thanks!

Ok then. I'm curious what's on your system. Output ```
sudo fdisk -l
``` from some linux that does work.

---

