---
title: "Understanding Grub"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by john8791 on 2007-09-09
In light of the recent Kernel upgrade that messed up many people's menu.lst, I decided I would learn all I can about Grub.  I have found some real good sites but there is one point of confusion I hope someone can clear up for me.

As I understand it, "Stage1" is/can be located in the MBR which then contains code and a pointer to Stage2.  What I'm confused about is the "stage1" and "stage2" files in /boot/grub.  If stage1 is in the MBR, what is the stage 1 file for?  Is it just a copy of what is in the MBR?

Thanks.

---

### Post by logos34 on 2007-09-09
The following link should answer your question:

[MBR Page]("http://users.bigpond.net.au/hermanzone/p6.htm")

---

### Post by john8791 on 2007-09-09
> **logos34 said:**
> The following link should answer your question:

[MBR Page]("http://users.bigpond.net.au/hermanzone/p6.htm")

Excellent page but I am still confused as to the purpose of the file "/boot/grub/stage1".  Why is there a physical "file" named stage1 when stage1 code is in the MBR?

---

### Post by logos34 on 2007-09-09
As I understand it stage1 in /boot/grub is the original file which is written/copied to the mbr (or bootsector of the root partition) when the 'grub-install' or 'setup' command is run.  It's hard-coded with the location of stage1.5 and stage2.

more info here:
[http://www.gnu.org/software/grub/manual/grub.html#Images](http://www.gnu.org/software/grub/manual/grub.html#Images)
[http://en.wikipedia.org/wiki/GNU_GRUB#GRUB_boot_process](http://en.wikipedia.org/wiki/GNU_GRUB#GRUB_boot_process)
[https://wiki.ubuntu.com/Booting](https://wiki.ubuntu.com/Booting)
('Finding the kernel and initrd>grub')

---

