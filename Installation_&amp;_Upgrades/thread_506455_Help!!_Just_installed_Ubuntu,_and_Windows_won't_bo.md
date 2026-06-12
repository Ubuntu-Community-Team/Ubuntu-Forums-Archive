---
title: "Help!! Just installed Ubuntu, and Windows won't boot =/"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by Tommerz on 2007-07-21
Hey everyone,

I just installed Ubuntu Feisty on a laptop, and now windows won't boot at all, just gives me a black screen!!

I even tried restoring Window's MBR from the XP disk, and it said it works but still it won't boot!!

Does anyone have any ideas? :mad:

---

### Post by bigken on 2007-07-21
go back to recovery console and type 

fixmbr enter 
fixboot enter
exit enter 

if this does not work go to the console again and try 

chkdsk /r

---

### Post by bigken on 2007-07-21
failing that you could try  a repair install

---

### Post by Tommerz on 2007-07-21
No joy I'm afraid =(

Unless you mean something else by the term 'Repair install'? Is it something different to pressing r and entering recovery mode?

Where did I go wrong do you think? 

It's uber important I recover this partition, once I do I'd like to install Ubuntu as well.

---

### Post by upchucky on 2007-07-21
look for supergrub its a loader that can fix broken grub files, it has an option to make a usbkey/floppy/cd/ repair for broken mbr

read lots, it is repairable, the problem is that grub dont know windows is there, and the windows bootloader was over written by grub. (windows was not overwritten, only the boot sector part of the drive that had the info needed to load windows)

Knoppix has the power to fix this too.

---

### Post by Tommerz on 2007-07-22
I don't think that's the problem, as I've restored Window's bootloader and it still doesn't load, but I will give restoring grub a shot.

Does anyone have any suggestions on why restoring Windows' bootloader won't work? And why did it mess up in the first place?

---

### Post by Tommerz on 2007-07-22
Well, I just restored grub using an xubuntu cd, and it hasn't fixed the problem, I'm still just left with a flashing _ on a black background when I try to boot Windows.

Is there any thing else I can try? Please could you elaborate on how the Grub Super Disk might help (I'm 75% sure the problem isn't grub related)?

Thanks =)

---

### Post by bigken on 2007-07-22
> **Tommerz said:**
> No joy I'm afraid =(

Unless you mean something else by the term 'Repair install'? Is it something different to pressing r and entering recovery mode?

Where did I go wrong do you think? 

It's uber important I recover this partition, once I do I'd like to install Ubuntu as well.

instead of going into repair console load the disc as if your going to install windows 
this will give or should give the option to do a repair install

---

### Post by Tommerz on 2007-07-22
Hmm, doesn't seem to give me the option. I've burnt Supergrub, and tried some of the options available, and they haven't solved it.

I'm just now booting into XP set up again, and running FIXMBR and FIXBOOT followed by chkdsk /r to see if it solves the problem (in case Supergrub triggered something...)

---

### Post by Tommerz on 2007-07-22
Arrgh, that still hasn't done the trick.

Is there anything in particular on Supergrub that might help?

---

### Post by Tommerz on 2007-07-22
Ok, I just fiddled some more with Supergrub's restore options, and now I have an error message saying "Error Loading Operating System".

Does anyone have any ideas what to do?

---

### Post by Tommerz on 2007-07-22
*Bump* I need to get this computer booting Windows by tonight, otherwise I'll have to do a complete reinstall, any ideas at all?

---

### Post by Trompette83 on 2007-07-22
Hi Tommerz,

I'm a new new and new user with Linux.
Yesterday I tried to install Ubuntu after XP installed.
HD1 with windows, HD2 with UBUNTU. Both with several partition inside.
When I rebooted, I had only black screen with GRUB at the upper left corner and nothing else.
I tried to repair unsuccessfuly.
I found out the reason: GRUB deleted Dynamic Drive Overlay in the first Seagate HD.
If You have DDO this could be the same problem.

Actualy the only way I found to repare was to use Diskwisard and errase the whole disk and recreate the partitions. Fortunately I have the image of my system and data.   :)

Now I have Windows well working, UBUNTU installed in the second disk but I can't access it because I have no dual boot.

What news for you?
Did you success?

(Sorry for my bad english)

---

### Post by upchucky on 2007-07-22
that flashing _ on a black background was the point that u could use grub to edit the grub file, the flashing _ was the prompt to enter commands, basic commands are posted in the grub readme, and basic linux commands are posted everywhere. there usually is a default user/password to get u started, a long time ago i had a default one that was root root

it has been a long time since i had to do what u r doing, but u need to edit the grub loader file to set up windows chainloader, and tell grub which drive has linux, and which drive has xp. windows may be sda and linux may be sdb

I may get corrected on this but the above is the general path to take.

Microsoft will not let anyone play with their loaders/IO and such, they think the masses are too stupid to learn basic programming.

dont give up if u can help it there is great satisfaction when u can make things work.

---

### Post by Trompette83 on 2007-07-23
Hi Upchucky,

I'm not sure it was a flashing _ after GRUP. I don't remerber that.

Anyway, I read a lot of post about dual boot and I would like your mind about this config
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

I'll change my boot order to start on hdc with GRUB
But I have a doubt:
Boot will start on hdb. After grub, if I choose Windows, will DDO be activate? I'm not sure.
I don't know where exactly is DDO before or after MBR.
What is your mind?

Their is a schema in this link
[http://doc.ubuntu-fr.org/windows/mbr_2_disque_dur](http://doc.ubuntu-fr.org/windows/mbr_2_disque_dur)
 

My config is identical
2 ATA HD:
hda1 with Win XP NTFS
hda2 data NTFS
hda3 data FAT32

hdc1 UBUNTU 7.04 ext3
hdc2 swap
hdc3 home ext3
hdc4 data FAT32

It seems to be easy and secure. Moreover, windows MBR and DDO are virgin in this case!!!

---

### Post by Tommerz on 2007-07-26
Hey guys, sorry for late reply!!

I probably should have been more clear - Grub did load up, but when I attempted to boot Windows, then I got the _

After running Supergrub, I instead got the equally cryptic "Error Loading Operating System" error.

In the end, I had to reinstall XP =( it also wiped my data in the process.

Does anyone know of a good data recovery tool for NTFS?

---

### Post by Mark Phelps on 2007-07-26
A good windows-based data recovery tool for NTFS partitions is GetDataBack.  I had parition corruptions from a bad SATA driver update and this utility worked wonders.  It ignores the file system index and locates what it thinks are directories and files.  It's not free, though.

---

