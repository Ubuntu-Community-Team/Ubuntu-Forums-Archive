---
title: "problems dualbooting windows 8 and ubuntu"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by mreyna16 on 2013-05-09
long story short about windows... i bout a samsung series 5 ultra (that isnt in the list of bricked ultrabooks) that came preinstalled with windows 8, i accidently deleted some partitions when trying to fix it and eventually led to deleting all partitions and reinstalling windows 8 in uefi mode

so, now i installed ubuntu 13.04 in uefi mode and now i cant boot into windows. i ran boot-repair and still no go. my computer loads grub and im able to see 3 windows entries (dont remember how they are exactly named) and cannot boot into any of them, they all give me an error.

here is my url that boot-repair gave me, if anybody can have a look and help me please.

[http://paste.ubuntu.com/5649050/](http://paste.ubuntu.com/5649050/)


also, i have very little knowledge on how ubuntu works, therefore the installation i did was because of a tutorial i followed and saw that different tutorials would tell you to make partitions that others wouldnt tell you to make... i have a 500 gb hard drive and would only want 100 gb for windows and the rest for ubuntu. so if anybody can check my partitions (i think you can see them in the url boot-repair gives you) and tell me if i have to many ubuntu partitions or if its ok the way i have it set up (i have 50 gb for the ubuntu installation, later ill make my partition bigger)

thanks in advance

---

### Post by oldfred on 2013-05-09
It looks like Boot-Repair has installed the secure boot Linux kernel and modified boot to allow booting both Windows & Ubuntu with secure boot. Does this entry in grub let you boot Windows with secure boot on?
 menuentry "Windows UEFI bkpbootmgfw.efi" {


UltraBooks have a small SSD for caching Windows. It uses Intel SRT which also uses RAID and causes issues. It used to be Ubuntu would not install, but now it does. But then grub will not install. It does look like you have grub installed, but may have video issues.
UltraBooks also use dual Intel & nVidia.

Some other Samsungs, each should be similar. The one with Series 5 did not want the Windows speeded up with the Intel SRT cache, so they installed Ubuntu's / (root) onto the SSD for quick boot. They then cannot turn Intel SRT back on.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

Does your UEFI/BIOS have a setting to use only Intel or only nVidia graphics. No one seems to have posted exactly how they get it to work or some get nVidia settings to work and others get Intel settings to work.

      
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

nomodeset works for nVidia, but if Intel some need this, or you may need both Video and other boot parameters.

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

This converts to only Ubuntu in BIOS mode, I do not recommend it nor its partitioning scheme.
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by mreyna16 on 2013-05-09
sorry, you lost me with all the links lol, again remember im a total noob when it comes to these things (studying for computer engineer but still have a lot of learning to do, thats why im installing linux ;) )

to answer some of your questions, no it doesnt let me log in to windows when enableing fast boot and no i dont have the options to change to nvdia

will re-doing both windows 8 and ubuntu installations be easier? keep in mind i want them both in uefi mode

---

### Post by oldfred on 2013-05-09
Not fast boot, I am not sure you should ever turn that back on. 
But turn on secure boot.
Can you boot from UEFI menu directly to either Windows or Ubuntu. Windows entry may actually boot into grub menu as it looks like boot repair did the rename for those systems that only boot Windows in secure boot mode.

---

### Post by mreyna16 on 2013-05-09
> **oldfred said:**
> Not fast boot, I am not sure you should ever turn that back on. 
But turn on secure boot.
Can you boot from UEFI menu directly to either Windows or Ubuntu. Windows entry may actually boot into grub menu as it looks like boot repair did the rename for those systems that only boot Windows in secure boot mode.

that worked! thanks oldfred! i will mark this thread as solved

off topic question: i was reading fedora 18 is very stable compared to ubuntu 12.04+ and although im not trying to get flamed for posting this in the wrong thread non the less in the ubuntu forums but how true is this?


EDIT: how do i mark it as solved?

---

### Post by oldfred on 2013-05-10
Glad that worked. :)

Do  not know about Fedora. I like to install different versions in another 10 to 25GB but have not installed Fedora. I think for UEFI it now uses a newer version of shim.

 Matthew Garrett
[http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/](http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/)
James Bottomley's random Pages - Linux Foundation Secure Boot System Released
[http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/](http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/)
[http://blog.hansenpartnership.com/owning-your-windows-8-uefi-platform/](http://blog.hansenpartnership.com/owning-your-windows-8-uefi-platform/)


 Screen shots of current work around for closing, more info in thread in my signature.

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by mreyna16 on 2013-05-10
> **oldfred said:**
> Glad that worked. :)

Do  not know about Fedora. I like to install different versions in another 10 to 25GB but have not installed Fedora. I think for UEFI it now uses a newer version of shim.

 Matthew Garrett
[http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/](http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/)
James Bottomley's random Pages - Linux Foundation Secure Boot System Released
[http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/](http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/)
[http://blog.hansenpartnership.com/owning-your-windows-8-uefi-platform/](http://blog.hansenpartnership.com/owning-your-windows-8-uefi-platform/)


 Screen shots of current work around for closing, more info in thread in my signature.

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Is newer version of shim better? Again, sorry but im a noob for these things

---

### Post by oldfred on 2013-05-10
I think the link above says shim is going to be obsoleted.
Matthew Garrett who was (or is ) from Redhat worked on shim but now Linux Foundation has its own key to install. And Garrett says shim will be merged with that version.  It is a complicated process so a lot of work has to be done to make it somewhat easier for you to manage your own keys.

---

### Post by mreyna16 on 2013-05-10
> **oldfred said:**
> I think the link above says shim is going to be obsoleted.
Matthew Garrett who was (or is ) from Redhat worked on shim but now Linux Foundation has its own key to install. And Garrett says shim will be merged with that version.  It is a complicated process so a lot of work has to be done to make it somewhat easier for you to manage your own keys.

I have decided to stay with ubuntu but since this install that you have helped me with was in a way a trial and error thing. i feel confident that i can make my own install of ubuntu again and the main reason why im going to do that is to redo all the partitions the way they are supposed to be and to give them the proper size. that being said, i have a 500 gb hard drive and one 22 gb ssd drive (which i know we dont need for the ubuntu installation) and i want to leave 100 gb for windows including the partitions it makes (in other words since windows 8 makes other partitions such as recovery my main c: drive will have less than 100 gb) and the other 400 for ubuntu and its partitions.

so, what partitions do you recommend i make in the 400 space, primary or not primary, and what size? if i didnt mention something in particular let me know what else you would add or take into consideration with the 400 gb space

---

### Post by mreyna16 on 2013-05-10
I was reading on another thread you were commenting and saw that in linux we can use the ssd to also speed it up...

So id like to add that i have a 22gb ssd and if possible make it to work with windows and linux... I have 4gb of ram so you can considerhow much space i need for the swap partition 

Id also like to add that i might make a specific partition so i can use all my files (music, pictures, videos, etc) just like u have it

Again, thanks for your help!

---

### Post by oldfred on 2013-05-10
Your SSD has to be either for Windows or your turn off the Intel SRT and use the SSD for / (root) but then you cannot use it for Windows. Your choice. If you use Windows more then I would keep it for Windows. 

My standard recommendation is 10 to 25GB for / (root). For new users I usually suggest the separate /home as then a new clean install is easier. But more advanced is separate data partitions. But if dual booting with Windows I do suggest that you have a shared NTFS data partition and only set Windows system as read only. And with Windows 8 hibernated (it is always hibernated or SRT), you may not even be able to read it.

Partitioning is personal and how you use system. I find my own most optimal configuration a year or two later is not so good & time for changes. By then I decide I want a new hopefully more reliabe drive and have space to reorganize. 

I started with just /, swap. I did have XP & shared NTFS data on one drive and Ubuntu on another drive. When I got a new larger drive I created new NTFS shared data and Linux formatted data partitions and lots of 25GB partitions where I install another Ubuntu to test or install another system. I now need to houseclean several version as they are not supported but I still have them. I only have a separate /home for literally one day. I created it for my new upgrade from 32 to 64bit with 9.10, but realized I wanted to share data not user settings.

I would create a 25GB / partition, and either 4.5 or 2GB for swap. I have 4GB of RAM and do not think I have used my swap. But because I have some swap on every drive except SSD, it automounts all of my swaps so I end up with more than I want unless I manually remove entry from fstab.

You also do  not have to fully partition drive but have to plan ahead a little as reorganizing can be difficult. I usually put swap last, Windows first, then Linux boot partition and then data partition(s). If thinking of other installs I may leave space between last data & start of swap so I can either expand data partition or create another 10 to 25GB partition to experiment with.

If you have UEFI, you  have gpt partitioning. You can only have 128 :) and they all are the same.
Only with MBR(msdos) partitioning do you have primary & extended with logical partition in the extended.

---

### Post by mreyna16 on 2013-05-10
what about boot partition? does the installation automatically do it for me or do i need to manually do it?

ill leave the ssd for windows (i want to get used to using linux but i want to leave it for windows because this is what i use for college and leaving windows will be for that)

so then correct me if im wrong (im sure im doing it wrong)... i would make a 25bg for /root, 4gb for swap, and the rest for the os? in that order?

what about making a seperate partition to put my media files in for both os's to use? would that be considered /home? 

ive decided to give each os 100gb including the other partitions needed on both os's and 300 as storage for my movies, photos, etc.

if im wrong (which i know im missing something to get it how i want), please let me know in what order you would do the partitions, what size, and what type of format...


EDIT: can you please also explain what each partition is for? some are self explanatory but since im a new linux user id like to know what exactly these partitions are for, thanks!

---

### Post by oldfred on 2013-05-10
With Ubuntu the default install partitions are / (root) and swap. All the system is in folders in root.  And that is all you need for a desktop install. 
In the old days or on some servers to isolate activity some or many of the system folders may be installed to separate partitions. Old systems or servers or some with different formats may need a separate /boot partition. 

But if you want to easily reinstall / (root) for a new version separating /home makes that easier. You still should backup /home as it has all your data & user settings, but you can reinstall to / reformat it, but not reformatting /home to preserve data & settings.
Since /home is Linux, it cannot be NTFS, so you cannot use it for sharing data.
You need a separate NTFS formatted data partition.

Swap is used as overflow for RAM or if you launch so many apps at once that all of RAM is used. But Linux caches activity so RAM is often full, but it releases unused apps space for a new active app. Only if all spce is used for active apps then you may need swap.
       [URL="https://help.ubuntu.com/community/SwapFaq"]https://help.ubuntu.com/community/SwapFaq

[/URL]
 Explanation of file structure - these are normally folders but can be partitions
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G   10G   17G  39% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  140K  2.0G   1% /run/shm
/dev/sdc2       100G   34G   67G  34% /mnt/shared
/dev/sdc6        97G   49G   43G  54% /mnt/data
/dev/sdd4        28G  4.8G   22G  19% /media/Quantal
```    

My sdc2 is NTFS from when I still used XP, my sdc6 is ext3, but I would use ext4 if creating it now. And I just have / on my SSD in sdd3. I have another install in sdd4. I am up to 18 partitions in sdc, many obsolete or test installs.

---

### Post by mreyna16 on 2013-05-10
then ill make a 20gb for root, a 4gb for swap and a 76gb for installation, and since i already have 100gb for windows then ill have 300gb that ill partition as an ntfs to share it with windows...

should i make them all primary?

---

### Post by oldfred on 2013-05-10
You can only have 4 primary partitions and one of those needs to be the extended partition. The extended partition acts as a container for all the logical partitions.

---

