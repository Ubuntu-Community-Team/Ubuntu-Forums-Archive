---
title: "Install Ubuntu 10.04"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by gilligan on 2010-09-27
Hi guys,
I tried many times to install Ubuntu 10.04 but I keep getting the following error message:
----------------------
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
----------------------
Can't be the CD or the CD drive because I get the same thing with a bootable USB flash drive.

HDD in SATA 1 port
DVD burner on SATA 0 port
HDD formated
Vice versa does not work neither.
Mobo: Intel D945GNT

I appreciate your help
Gilligan

Please help us!!

---

### Post by mörgæs on 2010-09-27
You could give 10.10 (beta) a try.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If problems occur, best is to search in this forum:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by dirghrabadia on 2010-09-27
Would formatting the HDD again using GParted LIVE CD with ext3/ext4 filesystem work?

---

### Post by RussOfford on 2012-11-13
I get this same message as the original above.

I can't try with v10.10 as one user mentioned above, because I must use a piece of software that is only compatible with v10.04.

Has anyone gotten past/around this message?

I have a SuperMicro SuperServer using the onboard raid.

Since the Ubuntu Desktop CD previously wouldn't load past the Ubuntu logo with the rotating dots below it, I used the 'nomodeset' option to continue.

EDIT:

It seems that 1/2 the people on [this other thread]("http://ubuntuforums.org/showthread.php?t=1556602&page=3") solved their issue by either burning the ISO to a DVD instead of a CD ... and/or re-downloading and checking the file size and verifying the MD5SUMS... but for some people the DVD didn't work either.

Any one try the DVD and have it fail, then continue to resolve this issue another way?

---

### Post by mörgæs on 2012-11-14
Hi, welcome to the fora.

I guess 'RAID' is the keyword here. My first suggestion is searching for guides on RAID installs.

I have never installed myself, so I can't be more specific.

---

### Post by lisati on 2012-11-14
Back to sleep, old thread!

---

