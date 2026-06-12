---
title: "Removing Ubuntu from Dual Boot"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by nx0 on 2008-01-12
I've had a good time using Ubuntu, the only problem for me is the graphics card drivers. Maybe in the future I will try making another dual-boot with Ubuntu and find it to be quite handy.

Currently, I have a Vista-Ubuntu dual boot system and GRUB. The Ubuntu partition has 50 gigabytes of my 400 gigabyte drive. I'm posting this from Vista. I have read that I could simply type fdisk /mbr in the command prompt, then format the Ubuntu partition as well as the two gigabyte partition that has something to do with Ubuntu (though I can't remember what) with the Disk Management utility and be able to boot just fine into Windows with the space freed.

But I have also heard that I need to format the partitions then run from a recovery disk and do fdisk /mbr. Is this only if I accidentally deleted the partitions then shutdown without doing fdisk /mbr in Windows?

What I'm looking for is how to remove Ubuntu and GRUB if I'm already running Windows. I haven't done anything to GRUB or the Ubuntu partitions as of yet.

---

### Post by confused57 on 2008-01-12
If you have a Vista install DVD(not a recovery disk), you could use the bootrec.exe utility to restore your Vista boot:
[http://ubuntuforums.org/showthread.php?t=482798&highlight=grub](http://ubuntuforums.org/showthread.php?t=482798&highlight=grub)

Supergrub "should" also be able to restore Vista's IPL to the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Once you're able to boot Vista independently of grub, then you can use Vista's partition manager to delete Ubuntu.

---

