---
title: "upgrade from windows 8.1 to windows 10 with dual boot ubuntu"
date: 2015-08-15
forum: Installation &amp; Upgrades
---

### Post by yuhang on 2015-08-15
Has anyone tried upgrading to windows 10 with dual boot?

I have Ubuntu and Windows 8.1 installed on two separate hard disks, and grub installed on the disk drive where Ubuntu is installed. 

I have reserved a free windows 10 upgrade. The system told me it is ready to install windows 10. I restarted the machine to boot into windows, but I was stuck with a purple screen(like the GRUB colour). 

Could anybody give some suggestions how I can upgrade to windows 10? Thank you very much!

---

### Post by grahammechanical on 2015-08-16
There are some Windows 10 threads dotted about the forum. But it seems that you have a problem unrelated to the thread title. Does the Grub boot menu load? Do you see options to load Ubuntu and Windows? Can you load Ubuntu? Can you load Windows? Please clarify.

[http://ubuntuforums.org/showthread.php?t=2288986](http://ubuntuforums.org/showthread.php?t=2288986)

[URL="http://ubuntuforums.org/showthread.php?t=2290694"]http://ubuntuforums.org/showthread.php?t=2290694

[/URL][http://ubuntuforums.org/showthread.php?t=2290529](http://ubuntuforums.org/showthread.php?t=2290529)

---

### Post by yancek on 2015-08-16
It's too late now but, it seems the primary reason for having windows and Linux on separate drives is to remove boot complications.  When you upgraded to windows 10, you should have dis-connected the windows hard drive.  If you did this, then it would be a different problem.  In addition to answers to the questions above, you might download and run "boot repair" and select the "Create BootInfo Summary" option, post it or a link to it here and someone should be able to help.  It will contain a lot of useful, detailed info on your system.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2015-08-16
If you have your machine set to boot Ubuntu by default, that is going to seriously confuse the Win10 upgrade tool.  Your best bet would have been to disconnect the Ubuntu drive before doing the update.

---

### Post by yuhang on 2015-08-16
> **grahammechanical said:**
> There are some Windows 10 threads dotted about the forum. But it seems that you have a problem unrelated to the thread title. Does the Grub boot menu load? Do you see options to load Ubuntu and Windows? Can you load Ubuntu? Can you load Windows? Please clarify.

[http://ubuntuforums.org/showthread.php?t=2288986](http://ubuntuforums.org/showthread.php?t=2288986)

[URL="http://ubuntuforums.org/showthread.php?t=2290694"]http://ubuntuforums.org/showthread.php?t=2290694

[/URL][http://ubuntuforums.org/showthread.php?t=2290529](http://ubuntuforums.org/showthread.php?t=2290529)

Dear friend, 

Yes, my system can load the grub menu, and I can specify which system to boot into from the menu. 

I can boot into either Ubuntu or Windows 8. prior to the attempt to upgrade my system. 

I'll have a look at the treads you posted. 

Thanks for the information.

---

### Post by oldfred on 2015-08-16
UEFI or BIOS?
But with either make sure you have changed system to boot Windows by default not grub before upgrading. Windows has been known to write boot partition on drive set as default. For most that is just sda, but better to be safe.
Also run Boot-Repair's summary report to backup details of your current installs, and make sure you do have good backups of everything.

---

### Post by yuhang on 2015-08-16
I have created a bootInfo summary with boot repair.

[http://paste.ubuntu.com/12103242/](http://paste.ubuntu.com/12103242/)

---

### Post by yuhang on 2015-08-16
I am using the traditional MBR method to boot my system. 

"[COLOR=#000000] make sure you have changed system to boot Windows by default not grub before upgrading."[/COLOR]

 I always see a grub menu when I restart. That's probably mean the system boot Grub by default.

I'll have a loot so that it boot to Windows by default.

---

### Post by oldfred on 2015-08-16
Reinstall a Windows boot loader to sda. You can use Boot-Repair or your Windows repair CD or flash drive.
Change BIOS to boot Windows by default.

Windows needs to have default drive as Windows drive, a primary partition formatted as NTFS. And either a separate Boot partition or main install as the NTFS partition with the boot flag.

---

### Post by yuhang on 2015-08-17
Used EasyBCD to regenerate Windows boot loader, now it works like a charm! 
Thanks a lot!

---

