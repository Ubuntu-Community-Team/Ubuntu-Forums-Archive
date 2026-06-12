---
title: "No such device error message"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by tallyho333 on 2010-03-17
I have been using my desktop as a dual boot machine for several months now. The primary hard drive with windows on it died, and since we have been using ubunto 9.10 exclusively, I just removed the dead drive, changed the jumpers on the secondary drive to primary and did a clean install on the drive which presumably formats the disk before installing. When I try to boot from the hard drive i get the following message:
ERROR: no such device 2eb48bcb-7bb4-4080-b04d-fc32dec8c252

Any help in diagnosing this would be appreciated.

---

### Post by mikewhatever on 2010-03-17
Can you boot from the live cd, open a Terminal (Applications->Accessories) and post the output of the following commands:

sudo fdisk -l

sudo blkid

Double check that jumper too, and yeah, welcome to the forum.;)

---

### Post by tallyho333 on 2010-03-17
I double checked the jumper and it is correct. I tried re-installing the OS and told it to boot from sda1 instead of HD0, but the results were the same except that the UUID number changed.

fdisk -l shows the following 3 partitions:
/dev/sda1  boot=* start=1, end=19271, ID-83  linux
/dev/sda2             start=19272, end=19457, ID=5, Extended
/dev/sda5              start=19272, end=19457, ID=82  linux swap

blkid:
/dev/loop0:  type="squashfs"
/dev/sda1:  UUID="fd7d9627-6170.... type="ext4"  This is the number it is failing on
/dev/sda5: UUID="67918b3c-...   type="swap"
/dev/ramzswap0: type="swap"

---

### Post by mikewhatever on 2010-03-17
I strongly suspect you are not booting from the same, /dev/sda, device. Are there more then one now? When the system is reinstalled, Grub gets reinstalled too, and the menu is generated according to the existing UUIDs. In your case, the UUIDs of partitions change as expected, but Grub still sees the same old UUID, which means there is another installation of grub somewhere else.

---

### Post by tallyho333 on 2010-03-17
This disk is the one that had Ubunto on it when It was configured as a dual boot machine, but
it is the only drive in the system now. Is it possible that the old grub installation survived re-writing the disk?

---

### Post by tallyho333 on 2010-03-17
I have been looking around the file system, and the /boot/grub directory only has one file in it. -- grubenv and that file is just a bunch of #signs. The root directory has links to /boot/vmlinuz and /boot/initrd.img, but these files are not in the boot directory.

Is it possible that grub was not installed?

---

### Post by raymondh on 2010-03-17
Courtesy of Meirfra ....... have a look at this link.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Best of luck,

Raymond

---

### Post by tallyho333 on 2010-03-17
Raymond

Thanks a lot, that fixed the problem. 
How do I change the status of the thread to fixed?

---

### Post by mikewhatever on 2010-03-18
So, what was the problem and how did the sourceforge link solved it?

---

### Post by tallyho333 on 2010-03-19
The problem was the grub configuration was putting an incorrect line in the startup. The link that Raymond pointed me to gave me the solution which was to comment out a couple of lines in the grub-mkconfig_lib and rebuild the grub.cfg file.

---

### Post by mikewhatever on 2010-03-19
But didn't you say there was no grub.cfg?

---

### Post by GringoFrenzy on 2010-04-03
Raymondh, you legend, that completely fixed my issue, thanks!

The only thing is, I ran a bunch of system updates afterwards which seemed to undo all the changes I made, and I had to run through the whole process again. (Perhaps grub was updated?)

Anyway, now I have 2 entries in my grub menu instead of one which is a bit annoying, but I'm sure I can edit it out somewhere...somehow.

---

### Post by raymondh on 2010-04-04
> **GringoFrenzy said:**
> Raymondh, you legend, that completely fixed my issue, thanks!

The only thing is, I ran a bunch of system updates afterwards which seemed to undo all the changes I made, and I had to run through the whole process again. (Perhaps grub was updated?)

Anyway, now I have 2 entries in my grub menu instead of one which is a bit annoying, but I'm sure I can edit it out somewhere...somehow.

"legend" ..... No, far, far from that.  The real legends are the likes of Meierfra, Herman, Zazen, etc.!!!  :) Nevertheless, I'm glad you got your system working towards the right direction.

Grub may have updated.  As for entries, what do you mean? Kernel or windows' entries?

Raymond

---

