---
title: "Assistance with Ubuntu Install"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by Dippers85 on 2012-10-20
Hey guys, first time here and my first foray into the world of Ubuntu :D 
 
Anyway, I downloaded the latest version from the website today, burned it onto a DVD and I'm now trying to install it onto a 100GB partition that I created for the OS. I get to the beginning of the installation where you have to select where you want to install it, but everytime I try and install it onto the partition it keeps telling me that a "Root File System is not defined." 
 
I've gone into the settings of the partition I want to use and I've alternated between boot loader's between DOS & Windows but no difference, file system is set as NTFS, but it doesn't seem to like anything. 
 
Can anyone offer me some advice on where I may be going wrong? 
 
Thanks guys!!
 
EDIT: Don't know if its worth mentioning, but I also have an install of Windows 7 & Windows 8 running on their own seperate partitions too!!

---

### Post by offgridguy on 2012-10-20
I don't know how much help this will be but when i installed ubuntu as a dual boot, I didn't have the partition selected before hand but let the ubuntu installer create the partition and then install.

---

### Post by jspike397 on 2012-10-20
Offgridguy,
NTFS is not a proper file system for Linux.  The majority of Linux users use EXT4 as a file system.  When you install Ubuntu, click on something else when it comes to where to install it on, delete the 100 GB NTFS that you have made for Ubuntu and add a 100 GB EXT4 partition, and you can install Ubuntu on there.

Hope this helps.

Jspike397

---

### Post by SMOKE14 on 2012-10-20
You can't use Ubuntu on a NFTS file system. You'll need to delete the 100GB partition, and and make a new partition as EXT4 and the mount point "/" without the quotes.

---

### Post by Dippers85 on 2012-10-20
> **jspike397 said:**
> Offgridguy,
NTFS is not a proper file system for Linux. The majority of Linux users use EXT4 as a file system. When you install Ubuntu, click on something else when it comes to where to install it on, delete the 100 GB NTFS that you have made for Ubuntu and add a 100 GB EXT4 partition, and you can install Ubuntu on there.
 
Hope this helps.
 
Jspike397
 
Ahh ok, I'll get cracking then and let you know. Cheers for the advice!!

---

### Post by offgridguy on 2012-10-20
> **jspike397 said:**
> Offgridguy,
NTFS is not a proper file system for Linux.  The majority of Linux users use EXT4 as a file system.  When you install Ubuntu, click on something else when it comes to where to install it on, delete the 100 GB NTFS that you have made for Ubuntu and add a 100 GB EXT4 partition, and you can install Ubuntu on there.

Hope this helps.

Jspike397
Thank you for the reply, I have learned something here, however it should have been 
addressed  to Dippers85.  By the way, welcome to the forum Dippers85.

---

### Post by Dippers85 on 2012-10-20
Hey guys, another little update: Managed to get it installed and its dual booting ok. I did blow away Windows 8 too so that I only have Windows 7 and Ubuntu running side by side. 
 
Its all running fine, the only odd thing is in the boot menu for Ubuntu....its displaying Windows 7 as Windows 8 for some reason haha :D but naturally Windows 8 isn't there anymore so when you select it, it actually boots back to Windows 7 as it should. 
 
Aside from that it all seems ok. Guess now its on with the tinkering and exploring! :D

---

### Post by SMOKE14 on 2012-10-20
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Try this :)

---

### Post by Dippers85 on 2012-10-21
Ahhh seems disaster has struck and I can't even begin to explain why!! 

After Ubuntu was installed last night everything was going perfectly fine, no problems. I booted into Windows to send some emails before going to bed and then shut down the machine. 

Woke up this morning, and turned on the PC this afternoon. Selected my Windows partition from the Ubuntu boot menu and......SNAP!! Doesn't boot into Windows, saying no partition exists!! So I reboot the PC figuring its a little error/glitch and try booting to Windows again.....same problem!

So I boot into Ubuntu fine with no issues, look in the hard drive and find all my data is there as normal on the Windows side of things, nothing has changed seemingly, it is ALL there!!  So, I pop my Windows CD in and try to do a repair setup.......it claims there are no problems to be found so no changes have been made, a dead end. I try and do a system restore to about 3 days ago and it says the restore was unsuccessful and no changes have been made. 

I again try and boot into Windows but it just won't boot at all. So I don't know if the partitions have become a little screwed up or where something has gone wrong, I can't begin to explain where something has gone wrong as I've never used Ubuntu & Windows side by side before. Thankfully I can boot into Ubuntu and grab all my data out from my Windows profile before I nuke the whole thing, format Ubuntu & Windows together and start Windows again from scratch!! 

At least I'm not losing any apparent data!! Disappointing though :(

---

### Post by offgridguy on 2012-10-21
You can try this.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by SMOKE14 on 2012-10-21
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If that doesn't work, you should probably back up your data, format, and reinstall both.

---

### Post by Dippers85 on 2012-10-21
> **offgridguy said:**
> You can try this.
 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
 
Many thanks for that, it went through an install and has my Windows booting up normally again. 
 
My next question would be: Since my PC appears to be using this GRUB boot system since installing Ubuntu, if I wanted to un-install Ubuntu, how would I go about doing that?? And would my PC go back to normal and boot into Windows on its own?
 
EDIT: Ah just seen the link in the above post pretty much answers that question :D

---

### Post by SMOKE14 on 2012-10-21
> **Dippers85 said:**
>  if I wanted to un-install Ubuntu, 
But why would you uninstall one of the best OS's ever? :p

---

### Post by Dippers85 on 2012-10-21
> **SMOKE14 said:**
> But why would you uninstall one of the best OS's ever? :p

Because in this instance something went wrong somewhere, so I would like the option to be able to safely uninstall it if possible :)

---

### Post by YannBuntu on 2012-10-23
> **Dippers85 said:**
> if I wanted to un-install Ubuntu, how would I go about doing that??

see [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
(it can uninstall any system: Ubuntu, Windows...)

---

### Post by SMOKE14 on 2012-10-23
> **YannBuntu said:**
> see [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
(it can uninstall any system: Ubuntu, Windows...)
That's a pretty cool tool, I'll have to bookmark it.

---

