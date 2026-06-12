---
title: "getting back into windows"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by jonemo on 2006-02-18
Couple of hours ago I felt like giving Ubuntu another go after it killed my windows while getting stuck in installation about a year ago.

5.10 installed smoothly, I chose selecting the partition manually and my ntfs windows partition wasn't touched (thats at least what ubuntu told me). i was never asked wether I want grub or not during the install, i just had it and it does not give me windows as an option. to get an idea of what to put into the /boot/grub/menu.lst I run fdisk -l to see my partitions. everything is as expected and windows seems to still be there (hda3):

```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1119     8988336   83  Linux
/dev/hda2            1120        1150      249007+  82  Linux swap / Solaris
/dev/hda3   *        1151        2569    11398117+   7  HPFS/NTFS
/dev/hda4            2570        4864    18434587+   f  W95 Ext'd (LBA)
/dev/hda5            2570        4864    18434556   83  Linux

```
I never made it so far in installing any linux so i made an uneducated guess and put 
```

title		Windows 95/98/NT/2000
root		(hd0,2)
makeactive
chainloader	+1
```

at the end of the /boot/grub/menu.lst.

upon selecting this when booting i get the error message
```
NTLDR missing
press CTRL-ALT-DEL to reboot
```

as it appeared in the language that i have windows installed in (and the above is a translation) it indicates that my windows is still alive, or not? well anyway - how do i get my ntldr back or better: **how do i get back into windows?**

---

### Post by knalle on 2006-02-18
NTLDR missing means that GRUB loaded windows successfully, sad to say it seems like your windows installation is hosed.

my grub windows entry:

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Tibor60 on 2006-02-18
You can save your windows. But first you must do an MSDOS  FIRST partition,
copy there the NTLR and NTDETECT files from the windows installation CD.
After it boot from the Windows instalallatio CD and in text mode run the fixboot command...
I can help if you write what partitions were there before installing ubuntu? You should not change the partitioning, because even if you save your windows, there can be a mess with the drive letters...

---

### Post by jonemo on 2006-02-19
Hi Timbor60,

I dont know what a MSDOS FIRST partition is but doing the fixboot thing crossed my mind before...

i actually didnt change the partitions at all during the install except for fomatting the hda1 with ext3 (thats where ubuntu lives) and formatting the space that i had left free for swap. no resizing or deleting whatsoever. i copied the result of fdisk -l below and added a comment for each partition:

```
   Device Boot      Start         End      Blocks   Id  
/dev/hda1               1        1119     8988336   83      Linux [was unused before, now ubuntu and / live here]
/dev/hda2            1120        1150      249007+  82  Swap [unused before, now swap]
/dev/hda3   *        1151        2569    11398117+   7  HPFS/NTFS [this is/was where my windows is installed]
/dev/hda4            2570        4864    18434587+   f  W95 Ext'd (LBA) [this seems to be the extended partition, which contains only one logical partition]
/dev/hda5            2570        4864    18434556   83  Linux [this one is another issue: its meant to store data but windows couldnt recognise it. i'll sort that out later]

```

drive letters are not so important as my data are all (well, almost all) on an external disk that i unplugged for the time i am fiddling around.

---

### Post by Tibor60 on 2006-02-19
It seems that your windows boot partition was on the hda1. And the ubuntu install formatted this partition and deleted the ntldr and ntdetect files. You need a partition managing software (Partition Magic is good for it), resize the hda1 partition, do a very little (20-40 MB) MSDOS partiton and copy there the ntldr and ntdetect files... and do the fixboot. But without the ntldr and ntdetect files fixboot will not help. 

An other solution, you can do  a boot floppy, but for this you need a functioning window system on an other PC. Place to this functioning system a clean formatted floppy disk, SEND to this floppy the ntldr, ntdetec and boot.ini files. (Copy will not do the job, you must SEND TO FLOPPY function!!!) Than you must edit the boot.ini file for your system and after all this you can boot from this floppy to your windows 2000 or XP system...

---

### Post by jonemo on 2006-02-19
allright, i think i messed it up completely now. cant load windows, cant load ubuntu. its not the first time that i crashed my computer because i wanted to have a quick glance at linux. of course it's not linux' fault but because i am too stupid.

as i am going to reinstall windows anyway and might feel like giving ubuntu another go in a year or so: **would it be better to put windows on hda1? ** from what i read in this forum it appears like then grub would recognize it automatically...

regarding your solution: are you serious? you want me to put ntldr and the other stuff on a partition that is formatted in a file system windows cannot read and has a complete ubuntu install on it and then make it so small that my ubuntu is definitely lost?

---

### Post by macdo on 2006-02-19
Windows **really** likes being on the first partition of the first disk (so hda1). Linux can be put anywhere. So start by installing Windows, and during the install partition so that there is free space behind it. 
Then, when you come to install Ubuntu, use the manual partitionning tool, leave the ntfs partition alone, and add the partitions you want. Alternatively, use a dedicated tool like gparted. There are hacks to put windows on a second disk, but even so, it has to think that it's on the first disk when it boots. 
What Tibor60 means is to add a partition infront of your hda1, that has the files that windows needs on it. That way, it boots from the first partition.

The only fs that both windows and linux can use safely together is fat32, by the way - which is probably why windows doesn't recognise your hda5.... Linux only has very limited support for ntfs (I'm told that it can damage data...), and windows has none for ext2 or ext3.

-- 
macdo

---

### Post by Tibor60 on 2006-02-19
I only give you the advice from my many years experience working with windows and linux systems together. If you dot a new install, I recommend you to do a first 20-30 MB MSDOS FAT16 (or even FAT12!) partition (hda1 or hd0,0 for grub) for booting your windows system. The main windows system you can place ANYWHERE on your winchester, at any (big enough of course!) partition. At any problem later you can copy to this first partition the ntldr, ntdetect and boot.ini files, and edit the last so that you can reach your windows partition at any place on your winchester, after doing the fixboot from the windows installation disk.

Not bad to do a second little partiton (40-50 MB) for booting the linux system. This should be formatted as en ext3 file system, and mounted under /boot. And the main linux partition to place anywhere on the winchester. But think over very good what partitions to do, because if you will not change later the partitions on your  winchester, you can repair both linux and windows very easy.

I recommend first to do some study about editing the boot.ini windows file and the grub system in whole. If you do, you will never have in the future problems with booting to your system. And if you will know exactly where are your systems, you can boot in to any system from a grub boot floppy at any time.

My experience shows that it is a very dangerous thing  to do partitioning as a default from any installation  cd or dvd, when you have a system already on your winchester. Better to do some study and partiton the winchester with the help of a good partitioning software.

---

### Post by jonemo on 2006-02-20
my winchester? who's that? sorry, not a native speaker...

anyway, i "fixed" it now. i reinstalled windows (was only two weeks old) and ubuntu - but the other way round. windows is on the first partition, ubuntu right behind it. in that case during the installation grub comes up asking a couple of question and bobs your uncle.

that doesnt mean i am without problems now. while ubuntu is so straightforward that mailclient, chat and browser and a decent media player are set up and running my windows bitches around and doesnt want any drivers anymore, possibly because i installed sp2 before the drivers or whatever. that's the reason why i set ubuntu as the default boot option and just do everything with it :D 

@tibor: your advice sounds sensible but i fear i dont get it completely (and it came too late, but thats because i cant wait). i think once you know that windows wants to be at home right at the beginning of the disk (where is the beginning of a disk anyway?) things work out quite well. but keeping a note of what system is on what partition is really worth the postit.

---

