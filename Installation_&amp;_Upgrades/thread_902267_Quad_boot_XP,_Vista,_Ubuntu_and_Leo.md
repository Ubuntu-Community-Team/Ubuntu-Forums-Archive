---
title: "Quad boot XP, Vista, Ubuntu and Leo"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by acdcfan on 2008-08-27
Hi all 
I have been long time windows user and time has come to try something else. 
This is my first post in search for answers

If I was going to ask for any help in here regarding above hypothetical subject, would I be breaking forum rules? I read forum rules and terms but it did not mentioned anything....


Hypothetically I have dual boot machine, XP and Vista on two separate SATA II hard drives. I am, hypothetically speaking, going to slot in 3rd 500Gb hard drive to install Mac OS 10.5.1. So far, hypothetically speaking, I managed to find instructions on how to install Kalyway on separate partition on the same hard drive but nothing on separate hard drive.
I am being paranoid of destroying boot loader, but I can not tell for certain which boot loader I am using when booting into Vista and which boot loader when booting into XP or they are two totally different ones. Basically when I turn my machine on, after a few seconds I get promoted to choose which OS I want to go to. That's what I want to get if I was, hypothetically speaking, going to install Mac OS 10.5.1.

What are your thoughts on disconnecting 2 hard drives with XP and Vista, installing OS X, reconnecting hard drives back and then what? What would happen then?Mind you I have EasyBCD installed on both hard drives

So far I have installed SATA controller and new hard drive. Both are seen in device manager and disk management. I have left new hard drive unformatted for the time being. It did my head in for about 2 hours. After initial hardware install I couldn't see hard drive in BIOS or any of disk management. Searched high and low to find out the cause but it turned out I didn't plugged the controller properly. How silly.....All is good

I intend on using EasyBCD and in my search I found this tutorial [http://neosmart.net/wiki/display/EBCD/Mac+OS+X](http://neosmart.net/wiki/display/EBCD/Mac+OS+X) where it states following
"" Once OS X has finished installing, the Darwin bootloader should load up OS X for the first time. It should give you an "Other" option to boot into Windows Vista."
Is above statement correct? If it is, then it is smooth sailing al the way.... It goes on further by saying repair Vistas boot loader which makes sense but what is happening to Darwin bootloader? Does it, by repairing it, include an option to boot into OSX from Vistas bootlaoder or......?. To me it seems it does...
Read a lot of good things about grub bootloader
I intend to install Ubuntu on about 65Gb, 3rd hard drive  partition and leave 400gb for Mac. 
My hdd0 is Xp, hdd1 is Vista and hdd3is empty but soon it will have Ubuntu on it... Tonite matter of fact. 

What I need are be instruction how to use Grub to add Mac OS to Grub boot loader... I don't know anything about command prompt so please take it easy with me 

Thank you for reading my post and doing a bit of brain storming to help me 


Any help would be appreciated

---

### Post by Jimmey on 2008-08-27
Your best bet would be to just plug in the extra drive, then install whatever other operating systems you want.

Once your OSs are in place, you'll be stuck in a position where the majority, if not all of them won't boot properly.

For that, you'll need to boot the live-CD to re-install grub to make sure that you can atleast boot Ubuntu. Once that's okay, you'll be able to edit Grub's menu to cater for all of the operating systems you have installed.

See [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") link to see what you'll need to do to recover grub (unless you install Ubuntu last).

Once that's done, like I say, just google around to see how to add entries in grub for each and every OS. The grub file is "/boot/grub/menu.lst".

---

### Post by acdcfan on 2008-08-27
> **Jimmey said:**
> Your best bet would be to just plug in the extra drive, then install whatever other operating systems you want.

Once your OSs are in place, you'll be stuck in a position where the majority, if not all of them won't boot properly.

For that, you'll need to boot the live-CD to re-install grub to make sure that you can atleast boot Ubuntu. Once that's okay, you'll be able to edit Grub's menu to cater for all of the operating systems you have installed.

See [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") link to see what you'll need to do to recover grub (unless you install Ubuntu last).

Once that's done, like I say, just google around to see how to add entries in grub for each and every OS. The grub file is "/boot/grub/menu.lst".

I am posting form Ubuntu live cd and I like what I see.... 
I have installed Xp first on hdd0, installed Vista on hdd1 and now I want to install Ubuntu on hdd2..... 
I will install Ubuntu now on 3 hdd on partition of about 65gb.... Therefore Ubuntus GRUB bootloader will stay untouched

Edit
I know which drive I want to partition, but I don't know which one to choose install section. While I can recognize two and I can not say for sure which one is which between Vista and new Volume.... it has given them something like sda1, sdb1 sdc and I am at the loss which one to choose and what type of partition file type to use 

Please help

---

### Post by Jimmey on 2008-08-27
SDA is the first drive - SDA1 is the first partition of the first drive.
SDB Should be the second drive - SDB1 is the first partition of the second drive (You get the idea) 

Basically it should equate to what you have learned from inside the liveCD = hda1 should be the same as SDA1.

Bascially, when installing there should be a "manual" option for the partitioning menu that you can use to resize a certain partition. Select the partition you want to resize then specify the new partition size as being current partition size minus the size for Ubuntu's partition - For example, if it's currently 50GB and you want the Ubuntu partition to be 15GB, you'd specify the new partition size as being 35GB.

Following that you can use guided partitioning to Use the empty space you just created. It should do it all for you.

---

### Post by caljohnsmith on 2008-08-27
> **acdcfan said:**
> I am posting form Ubuntu live cd and I like what I see.... 
I have installed Xp first on hdd0, installed Vista on hdd1 and now I want to install Ubuntu on hdd2..... 
I will install Ubuntu now on 3 hdd on partition of about 65gb.... Therefore Ubuntus GRUB bootloader will stay untouched

Edit
I know which drive I want to partition, but I don't know which one to choose install section. While I can recognize two and I can not say for sure which one is which between Vista and new Volume.... it has given them something like sda1, sdb1 sdc and I am at the loss which one to choose and what type of partition file type to use 

Please help
When you install Ubuntu, just be careful where you install Grub. When the installer gets to the point about installing Grub, if you hit the "advanced" button, you can specify where Grub will be installed. By default Grub is installed to whichever HDD is first in your boot order, i.e. the HDD that is booted on start up; this may or may not be where you want Grub, you have to decide. Just keep in mind that in Grub's World numbering begins with 0 and not 1, so:
```
sda = (hd0) = 1st HDD
sda1 = (hd0,0) = 1st HDD, 1st partition
sda2 = (hd0,1) = 1st HDD, 2nd partition
sdb = (hd1) = 2nd HDD
sdb1 = (hd1,0) = 2nd HDD, 1st partition
sdb2 = (hd1,1) = 2nd HDD, 2nd partition
...etc
```
So if you Ubuntu HDD is sdb for example, and you wanted to install Grub to the master boot record (MBR) of that HDD, you would choose to install Grub to (hd1). If you need more details or info let me know.

---

### Post by acdcfan on 2008-08-27
> **caljohnsmith said:**
> When you install Ubuntu, just be careful where you install Grub. When the installer gets to the point about installing Grub, if you hit the "advanced" button, you can specify where Grub will be installed. By default Grub is installed to whichever HDD is first in your boot order, i.e. the HDD that is booted on start up; this may or may not be where you want Grub, you have to decide. Just keep in mind that in Grub's World numbering begins with 0 and not 1, so:
```
sda = (hd0) = 1st HDD
sda1 = (hd0,0) = 1st HDD, 1st partition
sda2 = (hd0,1) = 1st HDD, 2nd partition
sdb = (hd1) = 2nd HDD
sdb1 = (hd1,0) = 2nd HDD, 1st partition
sdb2 = (hd1,1) = 2nd HDD, 2nd partition
...etc
```
So if you Ubuntu HDD is sdb for example, and you wanted to install Grub to the master boot record (MBR) of that HDD, you would choose to install Grub to (hd1). If you need more details or info let me know.

Xp drive is my boot drive, which in disk manaement is hdd0 and that is where I want to put grub.. 
Second thing I noticed is that in Partition manager,that comes after you selected your keyborad and time zone, it listed my 3rd hdd as first in line, Vista drive as 2nd, xP drive as 3rd... I concluded that by amount of space that has been used. Even when selsecting my 3rd drive it would not let me partition it. Am I  doing something wrong? 
 I have partitioned my 3rd hard drive into 2 pasrtitions. First partition is Healty 400gb where I want to put Mac, which is at the front of the drive , second partition is active 65gb at the back of the drive  where I want to put Ubuntu... And GRUB at MBR of hdd0 (XP drive) hoping this will help me install Mac without running any command prompt

---

### Post by acdcfan on 2008-08-28
Ubuntu say that my third hard drive is sda hard drive which is incorrect.... My Xp drive is hdd0 so this should read sda but it reads sdb1. Vista drive is hdd1 but in prepare partition it reads sdc1 which is wrong... it should be sdb1 and my 3rd hdd should be sdc (sdc1 and sdc2) because i partitioned it  

Some one please help

Edit
Strike above post I was panicking...Grub is getting installed in hd0 which is correc. 
What I didn't know how is to set partition for swap files therefore installation has occurred without it. 
Can you please tell me how to edit this to allow for swap file.... 
 I have used ext3 for file system....

It has failed to install GRUB ....

---

### Post by caljohnsmith on 2008-08-28
> **acdcfan said:**
> 
What I didn't know how is to set partition for swap files therefore installation has occurred without it. 
Can you please tell me how to edit this to allow for swap file.... 
 I have used ext3 for file system....

It has failed to install GRUB ....
Can you add another partition for swap space, or do you consider that not an option at this point? Generally, Ubuntu needs two partitions: one for Ubuntu's root file system and one for swap space.

But if you don't want to go back and create a swap partition, you can create a 2G swap file (for instance) and use that instead:
```
sudo dd if=/dev/zero of=/media/swapfile bs=1M count=[COLOR="Blue"]2000[/COLOR]
sudo mkswap /media/swapfile
sudo swapon /media/swapfile
```
If you want a different size swap file, just modify the "count" above. Next backup /etc/fstab and open it up:
```
sudo cp /etc/fstab /etc/fstab.082808
gksudo gedit /etc/fstab &
```
Add the following line to /etc/fstab:
```
/media/swapfile none swap sw 0 0
```
Save the file and you're done.

---

### Post by acdcfan on 2008-08-28
It doesn't matter how many times I try I get **"Can not install GRUB Fatal error" **

 I tried putting it in hd0... didn't work , tried dev/sda1 didn't work ](*,)](*,)](*,)](*,)
Any ideas.... ? 

And I still get, through live CD, my hd2 as sda, hd1 sdb and hd0 as sdc... WHY, WHY , WHY? ](*,)](*,)](*,)](*,)

---

### Post by caljohnsmith on 2008-08-28
> **acdcfan said:**
> 
And I still get, through live CD, my hd2 as sda, hd1 sdb and hd0 as sdc... WHY, WHY , WHY? 
Would you please clarify how you know that hd2 is sda, hd1 is sdb, and hd0 is sdc? Also, just an idea, but there is a known bug where Grub fails to install during installation but can be circumvented by using the ext2 file system (instead of ext3) for your root Ubuntu partition. If that works, you can easily "upgrade" your ext2 file system after you successfully install.

---

### Post by bapoumba on 2008-08-28
To the OP: are you aware that [MacOS should only be installed on Apple labeled hardware?]("http://www.apple.com/legal/sla/") Please do not ask for help about it in this thread, unless your hardware meets the requirements, thanks.

---

### Post by acdcfan on 2008-08-28
> **caljohnsmith said:**
> Would you please clarify how you know that hd2 is sda, hd1 is sdb, and hd0 is sdc? Also, just an idea, but there is a known bug where Grub fails to install during installation but can be circumvented by using the ext2 file system (instead of ext3) for your root Ubuntu partition. If that works, you can easily "upgrade" your ext2 file system after you successfully install. 

I have prtitione my 3rd hard drive into two equal partions. I have left other two allone and written down amount of used space. My setup looks like this 
 XP 500gb hd0 (usdes psace 150Gb) and it has 9mb of unallocated space
Vista 500gb hd1 used space 46
Ubuntu 250gb hd2,1 (active NTFS partition) Mac OSx 250gb hd2,2 (healthy partition) 3rd hard drive contolled by PCI SATA controller 
Reason I have done it like this is to be able to tell which is which. 
 I go install UBUNTU... Go through process of selecting language, and keyboard and it then it starts "scanning disks... 
When window comes up it brings information like this... 
 first partitition dev/sda1 250gb. second partition dev/sda2 250gb no used space... which is my 3rd hdd 
 sdb 500gb used space smiliar to vistas .
 sdc 500 gb used space similar to Xp with 9mb of free space 
 sdd 1000gb exetrnal hdd 

That is how I can tell

---

### Post by acdcfan on 2008-08-28
> **bapoumba said:**
> To the OP: are you aware that [MacOS should only be installed on Apple labeled hardware?]("http://www.apple.com/legal/sla/") Please do not ask for help about it in this thread, unless your hardware meets the requirements, thanks. 

I will not ask for help on that subject.... it is hypothetical ofcourse?

---

### Post by acdcfan on 2008-08-28
> **caljohnsmith said:**
> Would you please clarify how you know that hd2 is sda, hd1 is sdb, and hd0 is sdc? Also, just an idea, but there is a known bug where Grub fails to install during installation but can be circumvented by using the ext2 file system (instead of ext3) for your root Ubuntu partition. If that works, you can easily "upgrade" your ext2 file system after you successfully install.
 

When I select file type I selec ext3 and mount only as "/" or should I select something else? 
 I will try tonight to select as ext2 but what about mount point? :? 

Also 
please advice how to partiotion my 250gb partition to allow for swap,user,home, var and temp

---

### Post by acdcfan on 2008-08-29
I have downloaded the file againg and installation went well without grub fatal error, 
Upon restart I was back in vistas boot loader.... 
 Tried to repair the grub with commands 
sudo grub 
find boot/grub/stage1 
and it came back with Error 15 file not found.... 
What do I do now? 
 Do I go back to Vista and use EasyBCD to install neogrub or you guys can show me how to install it fro live CD

---

### Post by caljohnsmith on 2008-08-29
> **acdcfan said:**
> I have downloaded the file againg and installation went well without grub fatal error, 
Upon restart I was back in vistas boot loader.... 
 Tried to repair the grub with commands 
sudo grub 
[COLOR="Red"]find boot/grub/stage1 [/COLOR]
and it came back with Error 15 file not found.... 
What do I do now? 
 Do I go back to Vista and use EasyBCD to install neogrub or you guys can show me how to install it fro live CD
Should be:
```
find [COLOR="Red"]/[/COLOR]boot/grub/stage1
```
Did you forget the forward slash or was that a typo when posting here?

---

### Post by acdcfan on 2008-08-29
> **caljohnsmith said:**
> Should be:
```
find [COLOR="Red"]/[/COLOR]boot/grub/stage1
```
Did you forget the forward slash or was that a typo when posting here?

No I didn't. I copied of another thread ... 
This is how my fdisk looks like 
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92341f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x250024ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x251e251d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x969b09a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS
root@ubuntu:~# 

Is there something wrong? 

I have found the grub at hd0,0 but when I booted back it was vistas boot loader again. Can it be fixed?

Edit 
Grub message 

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

---

### Post by caljohnsmith on 2008-08-29
Sounds like you are simply booting from the Vista HDD, and not the Ubuntu one (which is where I assume you installed Grub to). You need to go into your BIOS settings to change the boot order of the HDDs.

---

### Post by acdcfan on 2008-08-29
> **caljohnsmith said:**
> Sounds like you are simply booting from the Vista HDD, and not the Ubuntu one (which is where I assume you installed Grub to). You need to go into your BIOS settings to change the boot order of the HDDs.

Grub installed at hd0..... 

will try that now....**It worked I booted from that hard drive and so grub boot loader... You are legend.**

I was wondering one more thing if GRUB can be chainloaded[COLOR="Red"][/COLOR]

---

### Post by caljohnsmith on 2008-08-29
Glad you got your Ubuntu HDD at least booting now. To get your other Windows HDDs booting with Grub, you'll need to open up your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst &
```
At the end of that file, add the following:
```
title   Windows (hd1)
root    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1

title   Windows (hd2)
root    (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
makeactive
chainloader +1
```
Reboot, and try the two new entries for Windows in the Grub menu. Make note of which one boots XP and which one boots Vista so you can change your menu.lst to include that info in the "title" lines above. If you get any errors, let me know what they are.

---

### Post by acdcfan on 2008-08-29
> **caljohnsmith said:**
> Glad you got your Ubuntu HDD at least booting now. To get your other Windows HDDs booting with Grub, you'll need to open up your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst &
```
At the end of that file, add the following:
```
title   Windows (hd1)
root    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1

title   Windows (hd2)
root    (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
makeactive
chainloader +1
```
Reboot, and try the two new entries for Windows in the Grub menu. Make note of which one boots XP and which one boots Vista so you can change your menu.lst to include that info in the "title" lines above. If you get any errors, let me know what they are.

You must have been born with knowledge like this... Sorted
Found an F11 key that let me chose which hard drive to boot from... Now we have chaniloaded to Grub..All is good. 
ARe we able to chainload it to XP/Vistas boot loader?

Now to increase my boot time....Increased to 30 sec

---

### Post by caljohnsmith on 2008-08-29
> **acdcfan said:**
> You must have been born with knowledge like this... Sorted
Found an F11 key that let me chose which hard drive to boot from... Now we have chaniloaded to Grub..All is good. 
ARe we able to chainload it to XP/Vistas boot loader?
I don't think I understand your question; so are you still booting from the Ubuntu HDD, and are able to boot your other Windows XP and Vista from Grub? What do you mean by "are we able to chainload it to XP/Vistas boot loader"?

---

### Post by acdcfan on 2008-08-29
> **caljohnsmith said:**
> I don't think I understand your question; so are you still booting from the Ubuntu HDD, and are able to boot your other Windows XP and Vista from Grub? What do you mean by "are we able to chainload it to XP/Vistas boot loader"?

I am booting from Grub... All good here. And yes I am able to boot other systems as well... 
 I mean are we able to chainload Ubuntu entry to Xp/Vistas loader like we did with grub or that is something to do BCDEDIT.exe file?

---

### Post by caljohnsmith on 2008-08-29
> **acdcfan said:**
> 
 I mean are we able to chainload Ubuntu entry to Xp/Vistas loader like we did with grub or that is something to do BCDEDIT.exe file?
Yes you can do that; it is more of a hack to do it in Windows XP, but it can still be done. But with Vista it can be really simple if you use something like "[EasyBCD]("http://neosmart.net/dl.php?id=1")". I would have to ask though, why would you want to do that at this point? If Grub can boot all your OSs just fine, why would you want to add Grub to the XP and Vista boot loaders? I'm just curious.

---

### Post by acdcfan on 2008-08-29
> **caljohnsmith said:**
> Yes you can do that; it is more of a hack to do it in Windows XP, but it can still be done. But with Vista it can be really simple if you use something like "[EasyBCD]("http://neosmart.net/dl.php?id=1")". I would have to ask though, why would you want to do that at this point? If Grub can boot all your OSs just fine, why would you want to add Grub to the XP and Vista boot loaders? I'm just curious.

I was curios thats all... 
I must say I quite like Terminal and using command gksudo gedit /boot/grub/menu.lst Ihave changed time out to 30sec... 
 Commands look easy and make a lot of sense when you get to know them.. :biggrin:

---

### Post by koym on 2008-08-29
thanks to both of you. this makes me ask, if dual booting [or multi-booting] a Mac OS with Ubuntu, XP are not a much more reasonable way around high $ investment in Mac hardware to have its benefits? Or, have I just plain misunderstood? 

My Son who has 32 years experience versus my 16 told me last night, "Dad give up on linux; use your time using Mac." Problem is, I get 26 miles per gallon using a $950 car. But I can't build or buy a Mac as easily as it would be to sling in HDs like you Gentlemen discuss. 

My Mirus PC P5GC-MX has a 750gig & 80gig with Freespire 2.0.8 based on Ubuntu 7.02 running on one partition of the 750; + my emachine 80 gig acquired for zero dollars dual boots with XP and Linspire 5.069. Am studying your successes and in the midst of installing Ubuntu 8.04.1 62 bit and Ubuntu Studio for video editing. hope I understand you people. :lolflag:Many, many thanks.

---

### Post by caljohnsmith on 2008-08-29
> **koym said:**
> thanks to both of you. this makes me ask, if dual booting [or multi-booting] a Mac OS with Ubuntu, XP are not a much more reasonable way around high $ investment in Mac hardware to have its benefits? Or, have I just plain misunderstood? 

My Son who has 32 years experience versus my 16 told me last night, "Dad give up on linux; use your time using Mac." Problem is, I get 26 miles per gallon using a $950 car. But I can't build or buy a Mac as easily as it would be to sling in HDs like you Gentlemen discuss. 

My Mirus PC P5GC-MX has a 750gig & 80gig with Freespire 2.0.8 based on Ubuntu 7.02 running on one partition of the 750; + my emachine 80 gig acquired for zero dollars dual boots with XP and Linspire 5.069. Am studying your successes and in the midst of installing Ubuntu 8.04.1 62 bit and Ubuntu Studio for video editing. hope I understand you people. :lolflag:Many, many thanks.
Well I certainly understand your desire to avoid paying the money for an Apple computer just to get a Mac OS. But I only helped acdcfan install Ubuntu, not Mac OS. I too wish Mac OS were available for PCs, but that's not the case yet (at least legally speaking). So sorry, but I don't think anyone in these forums is going to be able to help you install Mac OS on a PC. ;)

---

### Post by acdcfan on 2008-08-29
Hi guys 
Funny thing is that after I get Grub options which system to boot into and I select Vista, it take me to Vistas boot loader where I have options of XP or Vista... 
 Is this something usual?

---

### Post by acdcfan on 2008-08-29
> **caljohnsmith said:**
> Well I certainly understand your desire to avoid paying the money for an Apple computer just to get a Mac OS. But I only helped acdcfan install Ubuntu, not Mac OS. I too wish Mac OS were available for PCs, but that's not the case yet (at least legally speaking). So sorry, but I don't think anyone in these forums is going to be able to help you install Mac OS on a PC. ;)

How about adding Mac OS to Grub bootloader if location of install is known?

---

### Post by acdcfan on 2008-08-30
> **caljohnsmith said:**
> Can you add another partition for swap space, or do you consider that not an option at this point? Generally, Ubuntu needs two partitions: one for Ubuntu's root file system and one for swap space.

But if you don't want to go back and create a swap partition, you can create a 2G swap file (for instance) and use that instead:
```
sudo dd if=/dev/zero of=/media/swapfile bs=1M count=[COLOR="Blue"]2000[/COLOR]
sudo mkswap /media/swapfile
sudo swapon /media/swapfile
```
If you want a different size swap file, just modify the "count" above. Next backup /etc/fstab and open it up:
```
sudo cp /etc/fstab /etc/fstab.082808
gksudo gedit /etc/fstab &
```
Add the following line to /etc/fstab:
```
/media/swapfile none swap sw 0 0
```
Save the file and you're done.

Where do I start with this code? 
Terminal or ..... ?

---

### Post by msaa on 2008-08-30
long time ago, i have dual boot win98 and xp with ext part reserved for linux...since not much info and slow net speed....i givup!!...go tru this **acdcfan** i guess it pretty well to have here a summary how u do it in step by step documentation...it a great fun for Linuxfan!!!...

i wait ur Quadboot version working...:)

---

### Post by acdcfan on 2008-08-30
> **msaa said:**
> long time ago, i have dual boot win98 and xp with ext part reserved for linux...since not much info and slow net speed....i givup!!...go tru this **acdcfan** i guess it pretty well to have here a summary how u do it in step by step documentation...it a great fun for Linuxfan!!!...

i wait ur Quadboot version working...:) 

I am working very hard on that... I am determent to get it going and will not stop until I do....

Edit 
I have created swap file of 2Gb now I want to create root file... How do I do that? 
And how do I get Utorrent to see visa and xp drives... Somehow I can not access vista and Xp drives at all

---

### Post by acdcfan on 2008-10-05
> **caljohnsmith said:**
> Glad you got your Ubuntu HDD at least booting now. To get your other Windows HDDs booting with Grub, you'll need to open up your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst &
```
At the end of that file, add the following:
```
title   Windows (hd1)
root    (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1

title   Windows (hd2)
root    (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
makeactive
chainloader +1
```
Reboot, and try the two new entries for Windows in the Grub menu. Make note of which one boots XP and which one boots Vista so you can change your menu.lst to include that info in the "title" lines above. If you get any errors, let me know what they are.

After being away for a while I have tried above option and result is as follows.... 
When I enter first command it takes me straight to Vistas boot loader but second command takes me to  Press any key to boot...... 

I am typing exactly as posted above..... if possible I would like to be able to add XP and Vista to Grub and boot straight into either of the two. 

regards 
acdcfan

---

### Post by acdcfan on 2008-10-11
Anyone?

---

