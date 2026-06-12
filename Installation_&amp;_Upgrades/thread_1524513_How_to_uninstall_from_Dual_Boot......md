---
title: "How to uninstall from Dual Boot....."
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by travadinho on 2010-07-05
First off, let me apologize for posting what may be a common question. I have very limited internet access and thought that posting a thread would be most efficient. Here's my question:
 
I installed Ubuntu (version 9.10 32 bit) on my new desktop so that it'd dual-boot with Windows 7. I didn't give Windows enough hard drive space during the drive partition. It has enough space to operate, but I should've allocated more space to Windows. So my question is how do I uninstall Ubuntu without losing Windows? My ultimate goal is simply to allocate more space to the Windows partition while maintaining dual-boot with Ubuntu. How do I do this??? Do I need to uninstall Ubuntu??? My PC did not come with a Windows Boot disk. I only have a cd copy of Ubuntu. 
 
Any advice will be greatly appreciated.

---

### Post by oldfred on 2010-07-05
You can move partitions around with gparted but how easy it is depends on where your current partitions are. Moving a partition with lots of data can take hours where a reinstall may be quicker.

Post either a screen shot of gparted showing current layout and/or 
```
sudo fdisk -l
```

If you computer lets you make a repair disk I would do that first. I am not a fan of recovery disks, but you may want that. Vendor recovery disks usually just totally erase drive and make it just as purchased, so you lose everything. Check your documentation.

You can do a lot of repairs from linux but sometimes you need a windows repair CD.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by anieruddha on 2010-07-05
I dont know how u can do with windows7 but here is how I did in Windows XP.
Make sure that u have windows bootable installation cd/dvd. And Have administrator password.

1. Go to Disk management. Right Click on My Computer -> Manage
and find the Disk management.

2. delete linux partition by Right click on partition and select something like Remove partition. It will alert u. click ok

3. Now boot with windows bootable cd, when all driver loaded, It shows windows partition and say something like recovery console and ask u to give some function key (I dont remember I guess F7 or f8). Press that key. 

4. Now u r in recovery console. Select the Windows. I guess u have only 1 windows system install, so select 1.

5. Give administrator password. (dont left blank, I had problem with blank administrator password and It doesnt allow any user except Administrator)

6. Now give command
>> fixboot
>> fixmbr
>>exit

7. Reboot.

U can directly start from 3rd step and after recovering windows boot manager, delete linux partition, if u want.

For windows 7, I guess it will be same process, just try whether installation media give u option of recovery console.

And one more important, if u continue to using windows, google the "Booting Linux from Windows", It will give u step install grub on 1st sector of partition and to use windows boot manager to point to partition. (Simply u can boot linux from windows and removing linux partition would not cause windows.)

---

### Post by travadinho on 2010-07-06
Great, thanks for the advice.  I'll acquire a Windows recovery disk and wipe the drive.

---

### Post by travadinho on 2010-07-06
Actually, I'm going to post a screen of gparted.  I'll have to do it after work, but check back in a day or so.  If I can just alter drive space through Ubuntu, I'll try that route.

---

