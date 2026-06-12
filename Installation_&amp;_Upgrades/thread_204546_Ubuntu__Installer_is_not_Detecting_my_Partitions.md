---
title: "Ubuntu  Installer is not Detecting my Partitions"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by mayamaniac on 2006-06-27
My Partitions are screwed somehow because the installer is not seeing any of them, it just shows the whole drive space as "Unallocated". Yet from the LiveCD, I can go to System > Administration > Disks, and the Disk Manager can detect all the partitions just fine. Look at the attached screenshots, its very bizarre.

I made the partitions with WinXP. And WinXP is currently installed as the active primary partition (1), and the next parition (2) is also primary, which is where I want Ubuntu to installed to. Notice it says "Inaccessible" next to Status of partition 2 in the screenshot, clicking on "Enable" does nothing.

Are there any tools or via terminal commands to repair the partitions so that the installer will properly detect all the partitions? Please help, thanks.

---

### Post by BoneKracker on 2006-06-27
fdisk and parted are command line tools for working with partitions and filesystems

You can educate yourself from the terminal as follows:
```
man fdisk
man parted
```

Read first, but (provided you aren't trying to install to a RAID array or something) it should look like:
```
# fdisk /dev/sda
```
or
```
$ sudo fdisk /dev/sda
```

Both enable you to get a short help dialog / list of commands by entering the question mark.  p prints out your current partition table.

---

### Post by peterthewolf on 2006-06-27
Same problem I think it is gparted that is at fault as it has the same problem on breezy. When I try to repartition from Dapper install gparted goes through the motions but ends up with partitions of unknown type. Recommendation do not trust gparted it will wreck your system.
My disk is 40gb Maxstor on an Asus Pundit.

---

### Post by mayamaniac on 2006-06-28
thank you BoneKracker.

I did fdisk /dev/sda, it showed a 512k linux partition, the 7th partition. I have no idea how that got there. And its strange that 7th partition did not show in Disk Manager. Anyway, I deleted that partition and now the installer can detect all the partitions just fine now. Ubuntu is installed and just updated. 

Now to figure out how to get my Lexmark printer to work. But I'll leave that for another thread and not bury it in this one.

---

