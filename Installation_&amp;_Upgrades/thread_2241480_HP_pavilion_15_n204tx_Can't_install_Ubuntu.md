---
title: "HP pavilion 15 n204tx: Can't install Ubuntu"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by priyesh2 on 2014-08-26
Hi,,
 
1 months ago i bought new laptop : HP pavilion 15 n204tx with Ubuntu pre installed.
I formatted it and installed Win 8.

But now i need both win 8 and Ubuntu or any Linux OS, and my problem(s) are : 

  1 : Since it came with pre installed Ubuntu, when i try to install ubuntu-12.10-desktop.iso, it ask me to erase previous Ubuntu(system default).
  2. Getting message "Can't install 64 bit OS on 32 bit machine" , when i m installing open-SUSE-12.2-GNOME-LiveCD-x86_64. But my laptop is 64 bit.
  3. Fedora is showing blank screen, Fedora-18-x86_64-Live-Desktop or Fedora-18-x86_64-Live-Desktop.

Please anyone help, I NEED any LINUX based OS...

---

### Post by grahammechanical on 2014-08-26
First of all, Ubuntu 12.10 is end of life. do not use that. It most certainly does not have a Linux kernel that is compatible with the hardware that has come out since 2010.
Secondly, I cannot comment on problems with Opensuse or Fedora. I am not interested in those distributions.

Please use a Windows 8 utility to show your hard disk partitions and then take a screen shot and post it here.

Can you run a Ubuntu Live session? This laptop might have a UEFI boot system and although you have formatted the Ubuntu partitions the UEFI still has Ubuntu listed. That is my guess. If this laptop has a UEFI boot system then what mode did you install Windows 8 in? UEFI or Legacy? Which ever mode it was then Ubuntu will also need to be installed in the same mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by priyesh2 on 2014-08-27
Legacy mode, LiveCD

my system : [http://i60.tinypic.com/2cfxefl.jpg](http://i60.tinypic.com/2cfxefl.jpg)

my partitions : [http://i57.tinypic.com/nl8taa.png](http://i57.tinypic.com/nl8taa.png)

i want to install in highlighted drive.

When i m trying to use "Try Ubuntu" option, i m getting this : [http://i62.tinypic.com/flwqvo.png](http://i62.tinypic.com/flwqvo.png)

I'll download latest version of Ubuntu and try it with ur posted link support.

Thanks

At start : [http://i62.tinypic.com/2gtr981.jpg](http://i62.tinypic.com/2gtr981.jpg)

---

### Post by yancek on 2014-08-27
None of the systems you are trying to install are the current releases.  You should be able to get the latest by just googling download Opensuse/fedora/ubuntu or what ever you want.

The last image you posted shows you are trying to install in VirtualBox.  That can be problematic in with a 64bit in VBox.  You are not going to see Local Disk D: in any Linux as that is not how drives/partitions are labelled.  The image showsing the Compiz error is on a windows system.  Are trying to do the install in VBox?  Or are you trying to do a wubi install, installing Ubuntu inside windows as a program?  If so, give it up as wubi is no longer supported and according to the ubuntu site it definitely will not work on a system with windows 8.

---

### Post by priyesh2 on 2014-08-28
This time i m installing ubuntu-13.10-desktop-amd64.iso from USB.

But Ubuntu is not detecting my WINDOWS 8.

And i m not able to make 4th drive/path for swap area, when i click on continue it ask me to select swap area or to install without swap area.

So if i install without swap area, will it work perfectly and also can i access my old Win8

Please see attachment :)

Edit: i did some googling and found that all my partitions are primary, so can't make 5th primary drive.
Is it possible to make logical partition using exiting without deleting my files...if yes how??

---

### Post by yancek on 2014-08-28
Ubuntu 13.10 is not supported.  12.04 and 14.04 are.

You indicated you are using mbr to boot rather than GPT so you cannot create any more partitions.  You would have to delete one and then create an Extended partition and then be able to create a number of logical partitions with the Extended on which to put data.  I'm not sure what you mean by Ubuntu not detecting windows 8 as three windows partitions are showing in your GParted image.  We don't know what your different partitions are so its hard  to make any suggestions.  The smallest at the beginning of the drive is probably a boot paartition, the largest your windows system and the third a Recovery partition if this is an OEM install

Probably you would be better off first of all getting a supported Ubuntu (12.04 or 14.04) and then using the manual install option (Something Else) and creating an Extended partition and installing the Ubuntu system on a logical partition and swap on another logical.

---

### Post by priyesh2 on 2014-08-29
OK, i'll download Ubuntu 14.04, create extended partition and logical partitions and try.

In my last post attached image:
> 
  /dev/sda
     /dev/sda1         fat32        is my USB from which i was booting.
     /dev/sda2         ntfs          is the drive where i want to install Ubuntu (i'll format it to ext4, + some area for swap.)
     /dev/sda3         ntfs          my Win 8 system drive.
     /dev/sda4         ntfs          is my storage drive(my files).


"[COLOR=#000000]Ubuntu is not detecting my WINDOWS 8.[/COLOR]" >> i meant that in previous step where i selected Something Else, At top "Ubuntu can't find and operating system" was written, where it should  Ubuntu  has detected WINDOWS 8. 

So my question was if i install Ubuntu(even if its showing Ubuntu can't find and operating system ), will i m be able to access my old WIN 8.

Thanks.............

---

### Post by fantab on 2014-08-29
Boot with Live Ubuntu DVD/USB and "Try ubuntu". Open Terminal and post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by priyesh2 on 2014-08-29
See attachment

---

### Post by fantab on 2014-08-29
You have legacy 'msdos' partition table, this restricts the number of Primary partitions to ONLY 4.
You already have four.... and Ubuntu won't install until you have space for it on the HDD.

To overcome this 'only 4' primary partition limit you will have to delete one the NTFS partitions and create instead an Extended partition.
An Extended Partition is a Primary partition but only acts as a container for Logical Partitions.

Manage your windows partitions with windows tools only... 

Post a screen shot of your HDD from Windows Disk Management utility.
Can you tell us whats on partition 3 and 4, ie /dev/sda3 and /dev/sda4? Are they factory made or do you manage them yourself?

---

### Post by priyesh2 on 2014-08-30
> 
/dev/sda1            is factory made  (10 GB)
/dev/sda2            is my win 8 drive (48GB)
/dev/sda3            is the drive in which i want to install Ubuntu (48 GB)
/dev/sda4            is my Files (Games, movies, music etc)   (Remaining)


I'll format /dev/sda3, make it Extended and make two logical drives it it. **OR**
One more thing i can do is, while selecting drive for Ubuntu installation, I will create 1 logical partition first for swap and then i think i can  create 1 more primary partition for ' / '.

But my question [COLOR=#000000] if i install Ubuntu(even if its showing Ubuntu can't find any operating system ), will i m be able to boot my old WIN 8, coz i found 1 post here in that his WIN 7 is not booting  [/COLOR]http://ubuntuforums.org/showthread.php?t=2241924

---

### Post by priyesh2 on 2014-08-30
i searched of google...
 
 2 logical drives won't help because Ubuntu ' / ' should be in primary drive to boot.

and after formatting /dev/sda3  and creating 8 GB logical drive for swap (now total 3 primary drives), it is not allowing to create 1 more 40 GB primary drive (total 4 primary).

I asked in online chat, he told me to make my 385 GB drive to logical, but how can i do it without loss of data. It is 95% full, so can't make backup.

Any help is highly appreciated

---

### Post by yancek on 2014-08-30
> 2 logical drives won't help because Ubuntu ' / ' should be in primary drive to boot.

The Ubuntu filesystem does not need to be on a primary partition.  I have both Ubuntu 12.04 and 14.04 installed on my Desktop and both are on logical partitions and both boot without problems.  If you have a significant amount of RAM, you may not need swap.  You could try creating a partition for the filesystem after deleting swap with whatever space you have available although it should be 10GB or close to that as a minimum.

---

### Post by priyesh2 on 2014-08-30
ok, i will install in logical drive..

but after installing Ubuntu, will my win8 boot..if not then can i recover it/ re-install windows8 without affecting Ubuntu

---

### Post by fantab on 2014-08-30
I don't see any reason why it shouldn't... 
Remember to use 'Something Else' to set up your partitions during installation...

---

