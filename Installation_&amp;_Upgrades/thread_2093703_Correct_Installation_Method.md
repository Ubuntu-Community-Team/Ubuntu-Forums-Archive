---
title: "Correct Installation Method?"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by Androzani1 on 2012-12-11
Is this what I need to do to manually install Lubuntu?
My current set up is:

~20GB "C" Drive
~80GB "D" Drive
512MB RAM

I plan to:

[LIST=1]
[*]Backup all of my data
[*]Boot the live cd
[*]Launch G Parted and shrink/delete my "D" drive
[*]Reboot Windows (once or twice)
[*]Boot live cd and begin install using the "something else" option
[*]Create a / partion (ext4, 20GB)
[*]Create a /boot partition (ext2, 100MB)
[*]Create a swap partion (linux swap, 710MB)
[*]Create a /home partition (ext4, rest of disk)
[*]Make sure everything works
[*]Enjoy
[/LIST]

Correct?

---

### Post by oldfred on 2012-12-11
If Windows is XP you can use gparted to shrink, otherwise use Windows MMC.

You probably do not need /boot. Or 100MB may be a bit small. And with 512 of RAM your swap should be twice or 1MB.

How full are NTFS partitions? NTFS really like 30% free, so do not shrink too much.

Partition plan is fine, otherwise. Others may have different suggestions.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Androzani1 on 2012-12-11
Thanks oldfred. It is XP. 1GB Swap, no Boot.

The D Drive is 99% free, so I think I might just remove it by transferring everything to the C drive and deleting D altogether.

---

### Post by oldfred on 2012-12-11
Depending on how much you may be using Windows, I like having a shared NTFS data partition and never from Ubuntu write into the Windows system partition, only read from it. Then use shared NTFS for read/write.

But if not using Windows much it does not really matter.

---

### Post by Androzani1 on 2012-12-12
Cheers ;)

---

### Post by Androzani1 on 2012-12-17
Sorry to bump this so late on, but where would I install GRUB?

---

### Post by oldfred on 2012-12-17
If multiple physical drives, install grub2's boot loader to the MBR of same drive as your install. Do not install to PBR - partition boot sector unless you have another boot loader that boots multiple systems.

While Vista, pictures show how BIOS/MBR systems work.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Androzani1 on 2012-12-18
Ta :)

---

