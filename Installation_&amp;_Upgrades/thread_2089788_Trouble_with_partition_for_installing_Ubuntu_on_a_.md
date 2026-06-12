---
title: "Trouble with partition for installing Ubuntu on a computer that has win7"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by cetacea on 2012-11-30
before I even begin, I think I gotta apologize preemptively, for I am a supra-noob.

I'm trying to install ubuntu 12.10 on a laptop (or an ultrabook, as they are called these days) that has Win7 as its "native" os. I've read several installation guide regarding installing ubuntu, but when tried to follow the instructions I ran into something none of them mentions which is that for some reason my laptop already has 4 primary partitions and it is not possible to create more. 

Here is what the Gparted says about my HDD: 
dev/sda1(ntfs): system-boot
dev/sda2(ntfs): OS
dev/sda3(ntfs): Recovery
dev/sda4(fat32): HP_tools-lba

Now, from what I can tell, the sda1 and sda4 are not visible to me when I run win7. sda3 is visible, but not accessible. sda2 is where the win7 and all my applications and data reside. My original plan was to manipulate sda2 so that it would be divided into additional partitions that would eventually contain ubuntu and swap files. But as you can see, unless I can either remove one of those primaries, or find another way to create the fifth primary partition, I cannot move forward. What should I do? 

Thanks.

---

### Post by dino99 on 2012-11-30
4 primary partitions is the max supported; so you need to clean your windows and set an extended partition instead of one that is primary. Use windows tools  (and/or ccleaner) to clean/shrink.

here is how i do install:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by 2F4U on 2012-11-30
> or find another way to create the fifth primary partition, I cannot move forward.

Unfortunately, that is not possible. You are at the limit. Consult your manufacturers manual if there are options to create backups of at least one of the partions. There is often an option to create installation media from either the recovery or the vendor tool partition.

---

### Post by haqking on 2012-11-30
Primaries and the limit of 4 is restricted to MBR, if your BIOS suports it then in future if you decide to wipe the HDD you can  use GPT then there is no primary restriction.

until then you are screwed unless you can free up some space, a primary is not needed for Linux (actually contrary to popular belief a primary is not needed for windows either but that is irrelevant here) or as said create backup disks and remove the hidden partition.

---

### Post by oldfred on 2012-11-30
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Is an UltraBook another name for Intel SRT with a smaller SSD to speed things up. That complicates it even more as that is usually RAID which needs special drivers and gparted does not modify RAID partitions.

Post this from LiveCD/DVD/Flash installer's command line.

sudo fdisk -lu

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)

---

