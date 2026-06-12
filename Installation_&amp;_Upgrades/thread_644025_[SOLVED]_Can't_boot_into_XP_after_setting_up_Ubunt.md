---
title: "[SOLVED] Can't boot into XP after setting up Ubuntu to dual-boot"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by cadlewv on 2007-12-18
Hello.  First, and unfortunately, I used partition magic to set up a 10GB partition on my system drive.

Now, I can't boot into it.  I get the ole' "xmnt2002 was not found-skipping autochk" 
"autochk was not fount- skipping autochk" error.

I can't use the Partition Magic cd to boot, because it has now changed my C: drive to H:, and it's still looking for it on the C: drive.

What can I do to recover from this mistake and get my XP partition and it's information back?

Thank you.

---

### Post by Herman on 2007-12-18
Hello cadlewv,
Probably Partition Magic has changed the partition number for your Windows partition.
Now your boot.ini file is wrong and needs to be edited to update it with the new partition number. That's quite easy to do.

You just need to boot Windows XP and edit boot.ini. :)


"...okay, so how do I boot XP to edit boot.ini when XP won't boot?" you ask. :confused:

Well here's a link to a website where you can download a ready made floppy disk, CD-ROM (.iso file) or USB file  with a copy of each of the most important files in it for booting Windows XP, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"). 
Look for the CD-ROM (,iso file) download for Windows XP on that site. 
The disks contain their own copy of NTLDR, Ntdetect.com, and a specially edited multi functional generic boot.ini file.  
That should get your  Windows booted, it might take two or three attempts, but keep trying and you'll boot it sooner or later! :)
Then when you have Windows booted, you can edit your boot.ini file for next time.

There's also a more basic but similar how-to from Microsoft, [How to make your own Windows Xp boot floppy.]("http://support.microsoft.com/kb/305595/EN-US/") You can do it that way too, but it's a little bit more work and you'll need another computer with Windows XP in it to get the files from and make the floppy disk.

Regards, Herman :)

---

### Post by Herman on 2007-12-18
In case you have never edited boot.ini before, here is a link that explains how I would go about relaxing the security attributes temporarily and getting access to boot.ini, then re-enableing the security attributes when you're done. most of that web page is really about a different subject, though so just disregard what it says to do to the boot.ini file once you get it open, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html")

When you get your boot.ini file open, probably it will look something like this: 
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)WINDOWS="Microsoft Windows Xp Home Edition" /fastdetect
```You might need to change it to something like this,
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)WINDOWS="Microsoft Windows Xp Home Edition" /fastdetect
``` It might be partition number 1, or 2, or 3, or 4 that you have to change it to, probably it was number 1 before so now it will be one of the other numbers.

If you remembered what partition number it was you selected when you successfully booted with the NTLDR disk, that should be the number to use now.
Another way to find out is to do 'sudo fdisk -lu' in Ubuntu or look with a partition editor.  

Regards, Herman :)

---

### Post by Herman on 2007-12-18
If Partition Magic turned your Windows partition into a logical partition, (if it has a partition number greater than 4), then your job will be harder.
Windows can't easily boot from a logical partition , and the NTLDR CD probably won't have worked.
Windows can boot in a logical partition when it has a primary (partition number 1 to 4) 'boot partition', containing the three necessary Windows boot files, normally it also has an older Windows operating system in it. I don't know if it will work or not if you only made a partition with just those files. It might be worth a try.
Otherwaise you might need to use a partition editor again to re-copy Windows to make it a different partition number again, and make sure it's a primary partition. That might be the easiest way, but back up your data first.

You can use Ubuntu to rescue and back up all your WIndows data, you need to boot Ubuntu and mount Windows, here's how to mount Windows, [            Mounting Windows FAT32 or NTFS filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop") 

Regards, Herman :)

EDIT: Avoid the use of strange partition editors from now on, use a good 'Parted based partition editor, like GParted, QTParted, Partman or Parted (command line). 
All of those are fully compatible with both Windows and Ubuntu.

---

