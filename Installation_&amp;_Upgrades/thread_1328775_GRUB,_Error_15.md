---
title: "GRUB, Error 15"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by chunnel on 2009-11-16
I have reviewed recent posts regarding this, but they didn't address my problem.  I have 5 hard drives on my system.  I have installed Ubuntu 9.10 twice now and both times it installs fine, then I click to reboot.  At which time, I get the error message regarding GRUB "Error 15" and the computer goes no further.  I can't even get into Windows now, which I'll now have to reinstall, because when running the startup fix, it claims that there are no errors in my Windows 7 startup.  But ignore the Windows 7 problem, I just can't get Ubuntu to run.  

Prior to this, I had installed OpenSUSE 11.2.  This worked but was not very user friendly.  I undeleted the partitions I had to setup for OpenSUSE and had the Ubuntu install configure the partitions automatically.  Though it did tell me during the install that I needed a Root directory.  I have no idea what that is and there is no help during the install for that.  So I tried several options "/boot"  "/usr" and it finally installed when I chose "/".  One thing I have yet to understand is why do you make certain parts of Linux so easy and familiar and yet in regards to things like the root drive selection, provide absolutely no information for someone unfamiliar with Linux?  This is why I have tried Linux over the years but have always gone back to Windows.  You refine certain things, yet leave other simple things in code to be deciphered.

Perhaps one day you all will figure that out.  Maybe stop providing Linux in Vietnamese or Finnish and get the basic one in English as refined as Windows.  Then after that's done try to provide the program into other languages.  It seems you value diversity over getting the program right.  I just don't understand that point of view.  But I digress.

---

### Post by wrgb2 on 2009-11-16
Have a look at this post: [http://ubuntuforums.org/showthread.php?t=1325871](http://ubuntuforums.org/showthread.php?t=1325871)

---

### Post by chunnel on 2009-11-16
First, I am installing a 32 bit version even though I have an AMD FX-60, 939 processor (64 bit), because I want to install this on a friends machine and I'm trying to figure out how to install it.  Second, my RAID has been disabled in my BIOS and I'm running the 4 drives as separate drives.

Does your fix still apply?

P.S. I just tried your fix, no difference.

---

### Post by sfordin on 2009-11-16
Not a fix for the Grub issue, but to avoid having to reinstall Windows, try using the Windows rescue CD, open a Command Prompt, and then use the bootrec /fixmbr command. That'll kill Grub, but you should be able to boot into Windows again.

Scott

---

### Post by chunnel on 2009-11-16
That did fix my Windows 7 install, thanks.  
However, your fix regarding disabling RAID did not.  I still cannot run Ubuntu.

---

### Post by chunnel on 2009-11-16
Correction, it fixed the install of Windows, but somehow destroyed my user password.  I cannot log into my windows.  I'll still have to reinstall as I never created a system disk to reset the password.

Also, the fix you had above stated that I should use the alternate install CD for AMD 64.  I have no idea what that is nor where I can find such a thing.  I tried the install using the current 32 bit disk and disabling the raid in F6.

---

### Post by chunnel on 2009-11-16
It took awhile, but I found this link;
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs-Ubuntu/9.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs-Ubuntu/9.10/release/)
and I am downloading ubuntu-9.10-dvd-amd64.iso then I will try again.

---

### Post by atirox on 2009-11-16
You dont need to reinstall windows. All you should need to do is to boot into safe mode, select the Administrator account that should be created by default, then open the command prompt, and type in 

```
 net user (your username goes here) * 
```This will prompt you to enter a new password twice. Once you do that, reboot the machine. You should be able to use the new password.

---

### Post by chunnel on 2009-11-17
I'm learning more about Windows from you than I have from Microsoft Forum.  What's up with that?

---

### Post by chunnel on 2009-11-17
I've downloaded the AMD 64 Iso and tried to install that via Wubi installer, which no longer works, it told me to reboot and then I installed it on the same disk as Windows 7.  It installed, but never ran.  It booted right into Windows 7.  Windows 7 didn't show Ubuntu in the Programs list as it should have if Wubi worked.  I then deleted the partition and tried another install direct from the disk on reboot.  After install it says GRUB and does nothing else.  I then tried your bootrec fix from above, but that didn't work this time.  So I installed it again and tried the NoRAID thing in install and deleted the previous install.  Again GRUB and then nothing happens.  I again am in the position where I must install Windows 7 again.  I can't fix the MBR and I get to F8 to try safe mode.

---

### Post by atirox on 2009-11-18
> I'm learning more about Windows from you than I have from Microsoft Forum.  What's up with that? 	
Lol, no idea man. None at all. :) 

Anyway, concerning your drive troubles, if I understand correctly, you have 5 hard drives on your system, and i assume that Windows 7 is on the drive that is the Primary master drive. If memory serves me correctly, the primary master should be the first hard drive that is read from after POST. This means that the boot record on that drive is the one that is used to boot the machine. What seems to make the most sense to me, is to install Ubuntu onto that drive, the Primary master drive in your computer, as it would put the MBR section of GRUB and the rest of GRUB onto the same drive... that is, if you have 5 physically separate drives, and we aren't referring to partitions... Then, you could alter GRUB's config file to have Windows added to the boot menu... This should work, but since I am almost completely new to the Linux environment,  I cant verify that this will work. However, if we were speaking of a Windows environment... >:D

WUBI should modify the boot options so that you can choose between Windows and Ubuntu via the Windows Boot Loader... However, since you are using Windows 7, I can't tell you how to do this, as the boot loaders changed after Windows XP. On a side note, Windows XP is the last version of Windows that i have used well enough to learn most of its secrets, as my hardware is a 6 year old Compaq Presario R3055CA, which doesn't support Vista in any shape, size or colour. In Windows XP, you would normally go in and edit Boot.ini, or open sysdm.cpl, choose the advanced tab, then i think its startup and error recovery. that would allow you to modify the listed operating systems in XP... Perhaps in 7 as well... 

The NT kernel sees local disks in a weird way. For example, the XP partition i have is listed as:
```

Multi (0) Disk (0) Rdisk (0) partition (1)\....

```
I found this out by booting into safe mode, and watching the text that came up. I assume that what you see above translates to C: drive eventually. C drive on my laptop is the first partition on the drive. I assume that if you had lets say, XP pro installed on a second partition, it would be:
```

multi(0)disk(0)rdisk(0)partition(2)\....

```
However, that would be something like a fat32 or NTFS partition... Since WUBI creates a virtual partition, i dont know how it boots... Perhaps by loading a program that mounts the virtual partition...

As for fixing your MBR so you can load windows, the simplest method would probably be to hook up the drive with your Windows partition as the only drive in the system, then boot off the windows 7 CD, get to the repair console, which should be on there, and type in fixmbr. Or, at least, thats the way it is for the Windows XP install CD.... Anyway, doing that would give you a working windows partition as a temporary fix until you can figure this out.....

Sorry for the rant... its late, and i was jacked up on sugar... A bag of the Western Family Two Bite Brownies, and a bottle of root beer are great... but should probably be consumed sperately.... :)

---

