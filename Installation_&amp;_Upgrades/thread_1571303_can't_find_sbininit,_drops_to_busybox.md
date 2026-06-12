---
title: "can't find /sbin/init, drops to busybox"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2010-09-09
I'm running Ubuntu 10.04 i386 on a K9M6PGM-2 mainboard with an AMD Phenom Triple core @ 2.3 gig. I have 2 gig of RAM and Lucid is on a 320 gig HDD, /dev/sda1 shared w/Win XP. I have in the SDC position an 80 gig with Ubuntu Karmic. Long before the Widows was installed this problem annoyed me. My hope was that by wiping GRUB out and rebuilding it from the Live CD that this problem would be fixed but after several boot process' the problem ihas returned.

When I boot into Karmic and look at /sbin I find the file init but of course cannot open it. Is there any way to fix this?

The nachine might boot into Lucid 3 or 4 days in a row with no problem and then refuse to boot anything but WinXP or Karmic. It seems not to be the GRUB as Wendoze and Karmic boot as expected.

At the /dev/sdb I find;
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9327 74919096 83 Linux
/dev/sdb2 9328 9729 3229034+ 5 Extended
/dev/sdb5 9328 9729 3229033+ 82 Linux swap / Solaris
and do not know the origin of the partition.

---

### Post by th1bill on 2010-09-23
iniyramfs solution for Lucid

I have tried a number of published solutions and have even published one that worked for over a week. The following, of course, is from the Terminal after a successful boot but it has been the solution on several units. On my AMD triple core Phenom the #chroot /proc accomplished nothing but neither did it hurt. For those of you that are newbies, cut and paste one line at a time to your Terminal and you'll not get into trouble. Just refrain from remembering the sudo su command, it'll keep you from a mistake until you know why.

sudo su

#mkdir /mnt/sda1
#mount /dev/sda1 /mnt/sda1
#chroot /proc
#update-initramfs -u
#reboot

---

