---
title: "Installer not booting."
date: 2005-08-02
forum: Installation &amp; Upgrades
---

### Post by Veracon on 2005-08-02
I've just downloaded Ubuntu to replace Mandrake Linux, and have already done the repartitioning. Therefore, I tried to start the computer with the CD in my primary CD drive, however, it just loads Windows (98). I tried to access the BIOS using both F1, F2 and DEL, and something happened when I pressed DEL. However, it requested some sort of password that I don't recall making.

I'm trying to dual boot with Windows 98 SE.

---

### Post by kosmic on 2005-08-02
ok, the first thing you should do is go to your bios and change the boot setings you have to change so the CDROM is the first to boot.

Second problem, your Bios is passworded and you don't have the password, you have to open you PC case and search for a small Batery (is the same that some watchs use), remove the batery and power the pc on, it will not boot, then plug the pc off and insert the batery and voila no password in BIOS :)

---

### Post by Veracon on 2005-08-02
Thanks, another thing you may know the answer to:
According to PartitionMagic, I have two partitions now: the Windows one and a lump of unallocated space. I tried just resizing the Windows partition to use the full HDD, however when trying to resize, it tells me this:
Error 2003 while executing Batch. File size does not match FAT allocation for file. Will now reboot.

---

### Post by kosmic on 2005-08-02
First backup your entire disk, then try to partition the drive again but this time with fdisk, is a DOS Program that comes it windows, but be careful this program can wipe out your entire disk. 

Another way is boot the ubuntu install CD and in the partition menu, wipe out the entire disk and then create a partition with all the space availibe..but booth of this steps is destructible to the data you have in the disk, including the instalation of Win98 :(


Solution install ubuntu in this spare space :)

---

### Post by Veracon on 2005-08-03
Thanks for the response. I'm not crazy about opening my computer to access the BIOS, so I was wondering if it would somehow be possible to make an image of the CD which I could then boot from a floppy? With all other Linux distros I've used, an [font=courier]img[/font] file was downloadable. I see there's not one for Ubuntu, but I believe I heard somewhere you could make them somehow? :???:

---

### Post by Veracon on 2005-08-04
Sorry if it's not allowed to double post. Does no one know if this is possible? :?

---

### Post by Silvanus on 2005-08-04
You can't just put a CD onto a floppy. The Ubuntu files take up something like 600 MB; unless you have 400 floppies and a whole lot of time, you're going to have to use the CD.

---

### Post by Veracon on 2005-08-04
I'm not that stupid. :razz: 
What I'm saying is that with both Mandrake and DamnSmallLinux there were .img files available which would allow a floppy boot to load the CD.

Anyway, I used some CMOSPWD tool which recovered my password. Now it's time to try installing.

---

