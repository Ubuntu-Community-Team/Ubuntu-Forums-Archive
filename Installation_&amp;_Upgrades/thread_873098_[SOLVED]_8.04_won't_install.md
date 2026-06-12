---
title: "[SOLVED] 8.04 won't install"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by linnuxnub on 2008-07-28
I have tried updating from Ubuntu 7.10 to 8.04 with the update manager but half way through the installation process it freezes. Then I tried downloading it and burning it on a CD and booting from it but i get error messages saying: buffer I/0 error on device fd1, logical block (displays this message twice in a row then displays hda: drive not ready for command (displays 9 times). The messages continuing repeating in that order indefinitely.:confused:

Any help is greatly appreciated.

---

### Post by Fire_Chief on 2008-07-28
Did you use the alternate CD when trying the update from CD? You need to use that instead of the regular Desktop version CD. Try burning the ISO at a slower speed. Also, it sounds like your hard drive may be having problems. Might want to run a fsck on it and verify the integrity of the filesystem.

Cheers!

---

### Post by linnuxnub on 2008-07-28
I do not know how to use the alternate CD, I burnt the iso at 12x i don't know if that is too slow or too fast. How do I run a fsck.

I am new to linux so I don't realy know what i am doing. I would appreciate if you continued helping me.

Thank you for your help.

---

### Post by Fire_Chief on 2008-07-29
You can put the alternate CD in the system while running your current version of Ubuntu (don't need to boot from it). It will detect it and offer to upgrade your system from the CD. After it completes you should immediately update the system to get all the packages that were changed after the CD was released (via Update Manager).

Burning at 12x should be okay.

To do a disk check```
sudo fsck -a /dev/hd**
``` where ** is the partition you want to check (i.e. /dev/hda2 or /dev/sda3).

To find out which partitions to check try```
cat /etc/fstab | grep ext3
```This will list the Linux partitions on your computer (probably only see one entry). Make a note of the first bit of the line (/dev/something). This is what you will put for the fsck check device path.

Cheers!

---

### Post by linnuxnub on 2008-07-29
OK thanx I am now running Ubuntu 8.04. I used the alternate CD and it worked fine thank you.

---

