---
title: "Dual Boot, 2 hard drives...almost there."
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by bocmaxima on 2007-02-15
I have found a couple of different topics on this, but I dont know what to add to my GRUB list. I have 2 hard drives in my comp 93 actually, the 3rd being a FAT32 drive for sharing media between OSes), this is how its laid out. I installed Windows on the master IDE drive, and used gparted live disc to format the slave IDE to FAT32 (I couldnt find any decent tools on windows). Then I installed Edgy onto the Master SATA drive (the one it is set to boot to in the bios), but I had unplugged my other drives before doing so, because I didnt want to confuse them and erase them. Now, i have two good installs, and I just neeed to somehow get the windows drive into GRUB so I can choose that one when i need it. Like I said before, I know I have to add something to the grub list, but I dont know exactly what, or how to go about finding it. 

If you need my fdisk -l, let me know, or any other info, would be appreciated. I been through a few different topics on it, but none seemed to match my situation.

Thanks in advance.

---

### Post by confused57 on 2007-02-16
> **bocmaxima said:**
> I have found a couple of different topics on this, but I dont know what to add to my GRUB list. I have 2 hard drives in my comp 93 actually, the 3rd being a FAT32 drive for sharing media between OSes), this is how its laid out. I installed Windows on the master IDE drive, and used gparted live disc to format the slave IDE to FAT32 (I couldnt find any decent tools on windows). Then I installed Edgy onto the Master SATA drive (the one it is set to boot to in the bios), but I had unplugged my other drives before doing so, because I didnt want to confuse them and erase them. Now, i have two good installs, and I just neeed to somehow get the windows drive into GRUB so I can choose that one when i need it. Like I said before, I know I have to add something to the grub list, but I dont know exactly what, or how to go about finding it. 

If you need my fdisk -l, let me know, or any other info, would be appreciated. I been through a few different topics on it, but none seemed to match my situation.

Thanks in advance.
"Should" be relatively easy to add a grub entry to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Just set your SATA with Ubuntu as your first boot hard drive, and the drive with Windows as your 2nd hard disk, in your boot order.

---

### Post by bocmaxima on 2007-02-16
> **confused57 said:**
> "Should" be relatively easy to add a grub entry to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Just set your SATA with Ubuntu as your first boot hard drive, and the drive with Windows as your 2nd hard disk, in your boot order.

Perfect! One more issue to resolve and I have the perfect Linux install. Thanks!

---

