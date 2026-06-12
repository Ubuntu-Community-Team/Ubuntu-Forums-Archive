---
title: "Just had to reinstall windows..."
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by Anessen on 2007-08-10
Hey, I just had to reinstall my windows OS after it killed itself (again).

After the reinstall, windows was nice enough to obliterate my Grub bootloader, and breaking its own in the process. I fixed this by installing windows on a different drive.

I have tried to reinstall Grub using a tutorial I found here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But now, when grub is loading, it gives an error 17.

My Ubuntu install is intact, I just can't get Grub to install and run properly to boot into it. I am using the Live CD to post this, so I have access to a terminal and google and such.

My drives are set up as follows:
IDE harddisk (40gb):
--Linux Swap Partition (10gb)
--Fat32 Partition (30gb)

SATA HardDisk (160gb) (with Grub bootloader)
--EXT3 Partition (90gb) Ubuntu Install
--NTFS Partition (70gb) Screwed windows install

SATA HardDisk (250gb)
--NTFS Partition (250gb) New windows install

I'm not sure what number Grub assigns to the hard disks, though I think hd0 is my 160gb SATA drive. How can I repair the bootloader?

---

### Post by Pumalite on 2007-08-10
Read this: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)
And then try Super Grub to re-install your Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
What are you doing with a Swap partition of 10 GB?. 1 GB should be enough

---

### Post by Anessen on 2007-08-10
I have tried some things from that link, but it doesn't seem to help.

Just to clarify, grub gives this error when it is loading itself. Not when it tries to boot into Ubuntu. I don't even get to see the menu, it just breaks.

---

### Post by CowzRule on 2007-08-10
Have a look at this thread:
[How to restore Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

I think what you're going to need to do is edit the /boot/grub/menu.lst file. I think your problem is that grub is looking at the wrong drive/partition.

Hope that helps

---

### Post by Pumalite on 2007-08-10
Have you compared the 1st link that I gave you with your menu.lst?

---

