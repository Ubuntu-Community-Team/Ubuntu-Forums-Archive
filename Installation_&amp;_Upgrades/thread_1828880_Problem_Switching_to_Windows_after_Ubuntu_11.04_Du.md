---
title: "Problem Switching to Windows after Ubuntu 11.04 Dual Boot install! (Please read!!)"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by mobyguy77 on 2011-08-19
Hey guys! I installed ubuntu 11.04 to my Compaq Presario CQ61-402SA (Dual boot with windows 7 Home premium 64-bit, Via a partition) And now I can't get back to my W7! Disk Utility says that it is "unallocated"! Sorry I don't have any other info as-of-now, but ask and I will happily oblige! I don't know what to give, so just ask for ANYTHING (except my bank details and DOB :P ) It had lot's of important info on it! Sorry for the !s and the urgency, but it's important I get this OS and files back, intact. 

Thx Guys and I hope to see ya'll around.

Das Moby

---

### Post by westie457 on 2011-08-19
> **mobyguy77 said:**
> Hey guys! I installed ubuntu 11.04 to my Compaq Presario CQ61-402SA (Dual boot with windows 7 Home premium 64-bit, Via a partition) And now I can't get back to my W7! Disk Utility says that it is "unallocated"! Sorry I don't have any other info as-of-now, but ask and I will happily oblige! I don't know what to give, so just ask for ANYTHING (except my bank details and DOB :P ) It had lot's of important info on it! Sorry for the !s and the urgency, but it's important I get this OS and files back, intact. 

Thx Guys and I hope to see ya'll around.

Das Moby

Hello. Welcome to the Forums.

First thing first, Get your LiveCD/USB ready. You are going to need it.
Using the LiveCD boot your computer and select try. At the Desktop go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and download and run the program, instructions are there including how to post the results. This will give us a clue to what went wrong and the best possible way to help you.

Thank you.

---

### Post by mobyguy77 on 2011-08-19
> **westie457 said:**
> Hello. Welcome to the Forums.

First thing first, Get your LiveCD/USB ready. You are going to need it.
Using the LiveCD boot your computer and select try. At the Desktop go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and download and run the program, instructions are there including how to post the results. This will give us a clue to what went wrong and the best possible way to help you.

Thank you.


Thanks for your welcome and thanks for your help!

The results are attached

Thx,

Das Moby

---

### Post by oldfred on 2011-08-19
Boot script shows no windows partition. Did you select install to entire drive, it warns you that you will erase everything on drive. Hope you have a good full windows backup or recovery DVDs that the vendor told you to make from your recovery partition which is also gone.

Are you able to boot Ubuntu? You have grub & parts of grub legacy in your install and that often causes issues.

If you had data not backed up and have to try to recover data stop using system as it is overwriting data as you use it. Ubuntu is relatively small compared to windows and some data may be recoverable.

---

### Post by mobyguy77 on 2011-08-19
> **oldfred said:**
> Boot script shows no windows partition. Did you select install to entire drive, it warns you that you will erase everything on drive. Hope you have a good full windows backup or recovery DVDs that the vendor told you to make from your recovery partition which is also gone.

Are you able to boot Ubuntu? You have grub & parts of grub legacy in your install and that often causes issues.

If you had data not backed up and have to try to recover data stop using system as it is overwriting data as you use it. Ubuntu is relatively small compared to windows and some data may be recoverable.

No, I chose to use a partition to install Ubuntu. But, I DID create a new partition table. I think that is the problem (I just worked that out in the past 10 seconds). If so, How can I recover my data? (as much as I can, anyway)

PS- Sadly, I don't have any backups or install disks, please don't say I'm f*cked :)

---

### Post by westie457 on 2011-08-19
Which partition did you have Windows on? In theory it should have been on SDA1 or SDA2. Plus I cannot see an SDA4 in the results text.

One more command to run ```
sudo fdisk -l
```
the l is a lowercase L not a 1.
This time select the text in the terminal. In a new reply hit the # icon and paste the text in the tags that appear. This make things easier to read.

---

### Post by mobyguy77 on 2011-08-19
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8bdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          63      498688   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2              63        1930    14998529    5  Extended
/dev/sda5              63        1930    14998528   83  Linux
mobyguy77@Jacks-Laptop:~$ 

```

There ya go, nice and codey :)

---

### Post by westie457 on 2011-08-19
Having read oldfred's post and your further posts. You are probably right with your comment.

The only chance you have now is using testdisk available _[here]("http://www.cgsecurity.org/wiki/TestDisk")_

Run it from the LiveCD. Do not use the current hard drive at all.

Hopefully testdisk will find your old partition information and be able to restore it. Doing so might mean you lose your Ubuntu installation which is easy enough to replace as it is a new install.

If testdisk cannot restore the original partitions your only hope will be photorec (comes with testdisk) to search the hard drive for the old files.

If it can find any you are going to need another hard drive to write these files to because you cannot write to the drive that is being recovered. And a lot of patience will be needed to go through whatever is found.

Both of these offer a slim chance at best and no guarantees.

---

### Post by mobyguy77 on 2011-08-19
Sorry for bein' a noob 'n' all, but how do I run/install it?

Thx, 

Das Moby

Goin to the land of nod, so if I don't reply, you'll know why! (rhymes FTW)

---

### Post by tlcstat on 2011-08-19
Greetings,
Hey there Mobyguy77! I don't want to kick your tail too hard but what planet did you land from that doesn't backup data. Based on my own experience, if you installed over that Windows partition you can kiss your data good bye. Windows never did have a real secure file system to start with so I personally don't think there will be anything to recover. Now that you are here you might as well learn the use Linux and move on. Welcome to Ubuntu! May your nails get shorter and you head get balder.
tlcstat

---

### Post by oldfred on 2011-08-19
Links on how to use testdisk, be sure to use liveCD. Even if it recovers your NTFS partitions, they will not be bootable as some system files have been overwritten. Some of these links have similar information, but it does not hurt to review many to fully understand what you are doing.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Photorec is part of testdisk. It just scans drive for anything that looks like a file. You may get some files, they will not have file names just extensions, but flac & photos have meta data you can use to rename files.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by mobyguy77 on 2011-08-20
Sorry to be a pain, but I only have an iPod touch 8G to copy to and I only need a few files, after learning that it copies all files it finds (Photorec) Not tried the testdisk yet coz I still can't boot it. Can I selectivly copy files? 

Thx

Das Moby

---

### Post by mobyguy77 on 2011-08-20
> **mobyguy77 said:**
> Sorry to be a pain, but I only have an iPod touch 8G to copy to and I only need a few files, after learning that it copies all files it finds (Photorec) Not tried the testdisk yet coz I still can't boot it. Can I selectivly copy files? 

Thx

Das Moby


I think I might ditch all attempts to recover my data, because I have NO IDEA what-so-ever to do :( It's only 1 set of hol photos, shame it was the biggest album :(

---

### Post by oldfred on 2011-08-20
You can tell photorec to only recover certain file extensions, but you still have to have a large enough drive to copy to. There was a full page of extensions to check off to include or exclude. It was under file options on the third or fourth screen.

---

### Post by vikash_chandola on 2011-08-20
Similar problem was with me when i remove fedora from win 7 dual boot.
It is boot loader problem. 
what i did to solve this issue. 
Boot from windows 7 disk/USB.
go to system repair.
go to command prompt option.
run this command
```

bootrec.exe /FixBoot 
bootrec.exe /FixMbr

```
You are done just start your computer. You will see shining windows 7 logo.
there are many videos on youtube showing how to solve this problem. I also got this info from their.
In future if you want to install ubuntu or any of it's derivative like Lubuntu Kubuntu etc. then use wubi.

---

### Post by mobyguy77 on 2011-08-20
> **vikash_chandola said:**
> Similar problem was with me when i remove fedora from win 7 dual boot.
It is boot loader problem. 
what i did to solve this issue. 
Boot from windows 7 disk/USB.
go to system repair.
go to command prompt option.
run this command
```

bootrec.exe /FixBoot 
bootrec.exe /FixMbr

```
You are done just start your computer. You will see shining windows 7 logo.
there are many videos on youtube showing how to solve this problem. I also got this info from their.
In future if you want to install ubuntu or any of it's derivative like Lubuntu Kubuntu etc. then use wubi.

I mentioned that I had no access to windows installation/rescue CDs, but thanks for tryin' :)

---

