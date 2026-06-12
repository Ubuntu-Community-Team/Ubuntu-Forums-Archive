---
title: "I think I messed up bad... (grub issues)"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by Zeybrin on 2010-07-14
Well, I had installed Ubuntu 9.10 and had upgraded it to around 9.19 or something when I stopped using it...

So I decided I didnt need Ubuntu any more as I was always using Windows 7 and was actually quite annoyed with the Grub loader.

So I used a partition editor to delete the ubuntu partition and was going to resize the C: Partition back to its original state.

I had to restart the computer in order for the program to resize the partition so I did...

I'm sure you can see where this is going as now Grub can't find the partition it used to use and now just stays in Grub rescue mode... So is there any hope in me getting my computer back to booting the way it did before I installed ubuntu?  I am currently using the 9.10 Disk to boot my computer from the disk drive...

Any help would be greatly appreciated!

Edit: The partition I deleted is currently in limbo as unallocated space... So at least the program never was able to resize the C:... in case I need it..

---

### Post by cariboo on 2010-07-14
You can use your Windows 7 CD to remove grub and fix the mbr. Just boot from the CD and choose the repair option.

---

### Post by YesWeCan on 2010-07-14
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Grub and Windows don't mix that well. I always like to keep my persnickety Windows installation on its own disk, untouched by linux. Ubuntu 10.04 and grub2 are really quite excellent but to keep it simple install them on their own disk next time. :)

---

### Post by Zeybrin on 2010-07-14
Thanks! I wish my computer had come with a Windows 7 CD...(stupid OEM and Newegg) So What I am going to try and do is reinstall ubuntu on the blank space... Use grub to load the recovery part of Windows 7... and then fix the mbr... 

Think it will work? lol

---

### Post by wilee-nilee on 2010-07-14
Both previous posts are correct. Here is a recovery link and the commands with a http link for directions. the commands are from the ms link. Just run the highlighted command from the repair command line.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

[COLOR="Red"]You want to resize W7 with it's disc manager[/COLOR]

If this doesn't work post the bootscript in my signature.

---

### Post by Zeybrin on 2010-07-14
Oh hey... I found a Windows 7 disk... yay! Thanks to everyone for your quick responses! 

I forgot I upgraded my moms computer to Windows 7 (so she had the disks)... lol -face palm-

If anything goes wrong i'll let you guys know.. But I think I will have this all fixed up now thanks to you fine individuals. :D

---

