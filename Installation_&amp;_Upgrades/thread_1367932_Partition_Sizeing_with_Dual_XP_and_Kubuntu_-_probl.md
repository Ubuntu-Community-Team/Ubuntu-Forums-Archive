---
title: "Partition Sizeing with Dual XP and Kubuntu - problem"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by ChrisNZ on 2009-12-30
I have/had a 20gb HDD - dual boot OS

Windoz was installed already - and I have no disks with this second hand system. I then loaded Kubuntu and made the Windows XP Os too small. Unfortunately Games are driving this whole issue. Sound Familiar?

I entered into poo street :( by WinXP disk management and deleted Kubuntu and the swap space, re partitioning it as extented partition (well so I thought) Hopeing the effect was Windows would see the free space and add it to Disk 1 ntfs, then later re load Kubuntu from CD.

Yep the boot loader went and the error mssg was 

No such partition
Grub rescue>

I was thinking that the boot loader would disappear altogether leaving a clean start for Win xp. Not so easy though. 

Help!
1) have i now screwed up the HDD without recourse to get into windows to fix the partions?
2) I have tried to boot from the Kubuntu CD but it wont run it at all!
 
Can anyone help with this one please. Thanks
Fortunately I have a 2nd PC I can run with and both are at home.

TIA

---

### Post by dstew on 2009-12-30
> I was thinking that the boot loader would disappear altogether leaving a clean start for Win xp.The boot loader has a short stub that is in the first track of the disk, which is not part of any partition. When you deleted the Linux partition, you removed the grub configuration files and menu, but not the grub stub. You might be able to manually boot Windows with the stub of grub that is left, but it is probably better to re-install the Windows boot loader if you want to return to a pure Windows setup.

You can re-install the Windows boot loader using the **fixmbr** and **fixboot** commands from the [Windows Recovery Console]("http://support.microsoft.com/kb/307654"). You can get the Recovery Console by booting from a Windows rescue CD. If you don't have this CD, you can [download a set of floppy disk images from Microsoft]("http://support.microsoft.com/kb/310994") that will allow you to do this.

---

### Post by ChrisNZ on 2009-12-31
> **dstew said:**
>  ...If you don't have this CD, you can [download a set of floppy disk images from Microsoft]("http://support.microsoft.com/kb/310994") that will allow you to do this.

Hi dstew
Thanks just neede to ID which version of Xp on the hdd. So have downloaded em all. I did try to use the files by booting into the cd rom but with no affect, I suspect windoz file is so configured that it must be unpacked to floppy - then it should work.

Gosh cant remember the last time I used a floppy - must hav some somewhere? :lolflag:

Thanks and Happy New year to u and your family. I'll try this soon and will post results.

---

### Post by ChrisNZ on 2009-12-31
Well what started off well is "still going..."

Apparently  without knowing , Karmic Koala is having a software problem with finding (floppy drives not working) on the system and well.. lets face it not to many use em any-more so only becoming known recently! I have tried a few suggestions but still not working - refer "Is anyones floppy disk working" in general help. After a few more hours I gave up :/

Today I dug out another PC box and it had a working floppy drive and Windows XP sp3 on it!
I then downloaded 3 versions of the Windows Setup disks and found that SP2 was the one I needed and ran it ... upto a corrupt file on disk 5 of 6 #-o
Reloaded again with another floppy (found some in the dungeon).
2nd error upto Disk 5 Again
File NTFS.sys caused a unexpected error 4096 at line 5091 in d:\xpsprtm\base\boot\setup\setup.c.

so setup failed. ](*,)

Will try 1 more time as I'm so patient with windoz! :---) and then some of [-o< to the PC gods.
Nope - Failed again, however consistent on the error mssg though.

Bit of a bother, not having original disks as PC was gifted. If worse case is to wipe and start again then well - I will have to sacrifice this HDD to the PC gods! :)

---

### Post by ChrisNZ on 2010-01-01
Is it possible to do some "surgery" when the HDD as a slave?

---

### Post by dstew on 2010-01-01
Whether a hard disk is slave or master should not matter to software. That is just a setting that is used for putting two hard disks on one controller. The master controller is used for both disks, the slave's controller is put to sleep.

---

### Post by ChrisNZ on 2010-01-01
> **dstew said:**
> Whether a hard disk is slave or master should not matter to software. That is just a setting that is used for putting two hard disks on one controller. The master controller is used for both disks, the slave's controller is put to sleep.

Thanks dstew

Well the out come I was wanting has come to this - my wife says stop 'mucking around' and buy windows disk! :(
Mmm such clarity in thought! Beaten by a worthy opponent - why fight it! [-(

Thanks to all who advised on this - Although the problem was not solved via the above means allot was learnt that may help in future and others. Therefore, this thread is closed.

It so happened a friend of my sons had Xp home ed. disk and was able to use that to recover the HDD without installing the software. (Oh Happy daz... yeh right XP managed to freezup and produce errors mssgs quite quickly after that!)

---

