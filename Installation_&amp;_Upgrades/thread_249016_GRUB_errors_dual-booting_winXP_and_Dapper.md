---
title: "GRUB errors dual-booting winXP and Dapper"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by Nigy on 2006-09-01
Hi

Several months ago, I had Windows XP home and an earlier Dapper Drake version peacefully cohabating my (then) sole Harddrive on two partitions. However, i got rid of ubuntu not long after because i needed that harddrive space.

Now, after purchasing and installing a second, larger SATA HDD, and transfering all my windows files etc from the smaller HDD (HDD2) to my new second HDD (HDD1), I wanted to re-install ubuntu on HDD2 (using my newly downled version of Dapper Drake).

I loaded up the LiveCD, and easily installed ubuntu onto HDD2, with teh ex3 file ..system (and swap space). However, (I have tried this multiple times) GRUB gives me an error (error 17 if i remember right) when i chose to boot into ubuntu, and another error (13 i think) when i tried to boot into windows. However, the problem in solvable (the problem being not being able to boot into windows; the ubuntu problem is not fixed yet) by either booting up with the windows cd in and simply not booting from it (i dont know why) or swapping the SATA cables.

im using a 64 bit cpu, and the 64bit edition of dapper drake. 


Thank you very much for your help.

---

### Post by coffeecat on 2006-09-02
You can find [the Grub manual here]("http://www.gnu.org/software/grub/manual/").

Grub errors:

> 13 :

Invalid or unsupported executable formatThis error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).> 17 :

Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.From your post it looks as though you have Windows on sda and Ubuntu on sdb. Is this correct, and what partition numbers do you have Windows, Ubuntu root, swap and any other partitions on? Also, suggest you boot up from the live CD, mount your installed Ubuntu partition and post the contents of its /boot/grub/menu.lst so we can see what it's trying to do. Don't post the virtual menu.lst created by the live CD.

**Edit:** Might as well post the contents of /etc/fstab as well - that's the installed version, not the virtual version the live CD sets up. You mention swapping the sata cables. You're not making sda into sdb and vice versa are you? That's a sure fire way to completely confuse any operating system and make it unbootable.

---

