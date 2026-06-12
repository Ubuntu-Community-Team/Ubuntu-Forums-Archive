---
title: "recover windows from ntfsclone without having backup of mbr."
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by bullfinch on 2007-11-12
I took a backup of my ntfspartition using ntfsclone and cant get windows running again.


I used the command: ntfsclone -s -o image.img  /dev/hda1 -f
and to recover i used: ntfsclone --restore-image --overwrite /dev/hda1 image.img




Now when I try to run it it doesnt work. 

I have tried ms-sys -w /dev/hda  to rebuild the mbr. but it doesnt work.

I have also tried to make a small partition with grub on it and try to boot windows from grub.

If I do that i use: 

title=Win2K
root (hd0,1)
makeactive
chainloader +1

This results in the message 
root (hd0,1)
Filesystem type unknown, partition type 0x7
makeactive
chainloader +1

and it just hangs there. 

I would really perfere to use grub instead of the windows bootloadercrap to load windows.

I am quite confident that a fixboot and a mbrfix thing from the windows cd would do the trick, but I would really like to use grub.

---

### Post by Herman on 2007-11-12
Hello bullfinch,
I'm not familliar with the software you're trying to use, ntfsclone, but I really doubt that the condition of the hard disk's MBR  would have anything to do with a problem in a partition.
The hard disk's MBR is not part of any file system, it is the first sector of the hard drive. The first track of the hard drive is not formatted with any file system so it's not part of any operating system.

Anyway, it would be quite okay for you to go ahead and use FIXMBR to write Windows boot code to your MBR again and try ntfsclone again just to see if it does help.

FIXBOOT will restore your Windows boot sector. The Windows boot sector is not the same thing as the MBR, but a lot of people get the two mixed up, which causes no end of confusion.
You can try FIXBOOT too if you want, it won't hurt.
ntfsclone will probably have included your boot sector already in your back up though.

You can always restore GRUB to MBR again later. The MBR is made out of the same material as the rest of the hard drive and can be written to and re-written an infinite number of times, (theoretically at least), you hard drive bearings will probably wear out before your MBR does.
You can do something like what I explained in this other thread, here:                               [HOW-TO install boot loader from Ubuntu]("http://ubuntuforums.org/showthread.php?t=609548")
That should explain to you how to re-install Grub. You can do that from a Ubuntu LiveCD.

Regards, Herman :)

---

### Post by bullfinch on 2007-11-13
I cloned out the image to a harddrive. 

New mbr:
ms-sys -w /dev/hda (this will ruin grub etc. if you like grub  don't do this. just show partition where it starts.)

Showing ntfs where it is. (ntfs is a bit mongo)
pxeboot:~# fdisk -lu

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   154304324    77152131    7  HPFS/NTFS


The startblock of the ntfs is 63,
so then i ran:

 echo 63 |awk '{printf("%c%c%c%c",$1%256,$1/256,$1/65536,$1/16777216)}'|dd bs=1 count=4 seek=28 of=/dev/hda1

This writes the startingposition of the ntfs to the partition. (wich is great!)

If you want to use windows as hda2 you have to edit the boot.ini-file on the partition. And of cource write the startingposition to the right partition.)
hda1 is partition 1.  (not like grub wich makes hda1 to be hd(0,0))


This is probably a bit unclear, but it might help someone.

---

### Post by Herman on 2007-11-13
ntfsclone is a Linux program that is great for making a backup of a complete NTFS partition.
Here are some links for anyone else who didn't know about it before,

[URL="http://www.linux-ntfs.org/doku.php?id=ntfsclone"]About ntfsclone
[/URL]
[NTFSCLONE(8) manual page]("http://man.linux-ntfs.org/ntfsclone.8.html")

[Using NTFSClone.]("http://franktank.com/blog/linux/using-ntfsclone/")

[Backing up NTFS partition: partimage or ntfsclone? - Knoppix.net]("http://www.knoppix.net/forum/viewtopic.php?p=79256")

Quoted from the manual page:> **Windows Cloning**

 If you want to copy, move or restore a system or boot partition to another  computer, or to a different disk or partition (e.g. hda1->hda2, hda1->hdb1 or to a different disk sector offset) then you will need to take extra care.   Usually, Windows will not be able to boot, unless you copy, move or restore  NTFS to the same partition which starts at the same sector on the same type  of disk having the same BIOS legacy cylinder setting as the original  partition and disk had.  
 The ntfsclone utility guarantees to make an exact copy of NTFS but it  won’t deal with booting issues. This is by design: ntfsclone is a  filesystem, not system utility. Its aim is only NTFS cloning, not Windows  cloning. Hereby ntfsclone can be used as a very fast and reliable  build block for Windows clonning but itself it’s not enough. You  can find useful tips following the related links on the below page 
 [http://wiki.linux-ntfs.org/doku.php?id=ntfsclone](http://wiki.linux-ntfs.org/doku.php?id=ntfsclone) 
I agree with you, bullfinch, GRUB makes an excellent boot manager for booting Windows with, and it is a great idea to use GRUB installed in a dedicated GRUB partition.
[         How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")    (contains GRUB files only) .

You don't need to have Linus installed to use GRUB.
GRUB is a great boot manager and can be used to multi boot Windows installations better than Windows' own method. 
 [Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm")

If someone clones their Windows partition and it used to be partition 1, then reformats their hard disk, and makes a dedicated GRUB partition as partition 1, then Windows will have to be partition 2 or some other number.

You need to edit boot.ini to get Windows XP to boot if your Windows partition number gets changed somehow, or you'll get one of these error messages when you try to boot Windows, [Error messages from Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_Booting_errors") [COLOR=#000000]...(Windows begins to boot, but fails with message...)
[/COLOR]You'll find an illustration about how to edit boot.ini somewhere in that link or sub-links from it.

```
 title  Win2K
rootnoverify (hd0,1)
makeactive
chainloader +1
```Should get rid of the 'filesystem unknown' error message, and should chainload Windows by its bootsector if the bootsector is healthy and (hd0,1) is your Windows partition, or in other words, partition number 2.
(Because maybe your dedicated GRUB partition is already occupying the number 1 slot).
[A Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

It would be a little easier for most people if they are planning to do this if they create a large empty partition for Windows first, so it will have the number 1 slot, and then create the GRUB partition in the number 2 or some other slot.
Then it shouldn't be necessary to edit boot.ini.

Thanks for your information there, bullfinch, I just thought I'd try to fill in some gaps so it might make sense to someone who is less experienced and might be trying to make some sense of this thread. 
Did it get it right? 

Regards, Herman :)

---

### Post by bullfinch on 2007-11-14
What I really want to do is to replace the ghost system I used to have with ntfsclone and linux booting over network.

This means that I can't run a windows xp install cd because then it would be just as easy with a ghost cd.


I don't really want grub eather.
I just want ghost functionality on a ntfsclone-based backupsystem. 

what I do:
#this clears out the whole start of the disk.
dd if=/dev/zero bs=20M count=1 of=/dev/hda

# this creates a bootable ntfs disk of the whole hda. (look below, i'll post it)
./partition.sh 

#this wrotes out the windows bootloader to hda
dd if=copyoforiginal.bin  bs=446 count=1 of=/dev/hda 

#this writes out the whole ntfspartition
ntfsclone --restore-image --overwrite /dev/hda1 image.img

#this gives me the startpos of the ntfspartition.
fdisk -lu 
/dev/hda1   *          63    78165359    39082648+   7  HPFS/NTFS

# This writes out the startposition to the ntldr (window bootloader)
echo 63 |awk '{printf("%c%c%c%c",$1%256,$1/256,$1/65536,$1/16777216)}'|dd bs=1 count=4 seek=28 of=/dev/hda1 

#this resizes the ntfspartition to fit the space. (i'm not sure if i need this)
ntfsresize -n /dev/hda1 && echo y | ntfsresize -f /dev/hda1


This method ofcource doesn't work... hmf!

orginal:	 	/dev/hda1   *          63    78156224    39078081    7  HPFS/NTFS
./partition.sh:	/dev/hda1   *          63    78165359    39082648+   7  HPFS/NTFS


## partition.sh: (the script)
fdisk /dev/hda >/dev/null 2>&1 <<EOF
p
d1
n
p
1


t
7
a
1
w
EOF


#script end.

I have no idea why this isn't working. But I think that the windows bootloader wants more info on the partition than the starting point. how can I edit the rest of the data? 

It has to be something like the "echo 63 |awk '{print"-thing. but only to another space on the disk.

How do I create a windows bootloader from linux?

---

