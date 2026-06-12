---
title: "Bootloader location question"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by VideoRoy on 2010-01-30
I have done a couple of dual and triple boots with EasyBCD and also using Ubuntu 9.10 boot loader no problems but this new setup has me a little confused on where to load the boot loader.

I am dual booting with Win7 and Ubuntu 9.10 both 64bit and in fact I am typing from the install now so it works.  I used EasyBCD and it is all working fine no problem.  Win7 on 1 drive and Ubuntu on a 2nd drive.

I got in the habit of always manually partitioning my drives a long time ago because I like to make sure I know where the installs will land.  This time around when I chose where to put the bootloader for Ubuntu I put in on /dev/sda1 but I am wondering if I should have put it on /dev/sda instead since that was a choice.  My mount point in "/" on /dev/sda1.

So the question is should I be putting bootloaders on /sda or /sda1?

BTW my drives / partitions look like this with Win7 as the primary (/dev/sdb1):

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77823   625113216   83  Linux
/dev/sda2           77824       77825       16065    5  Extended
/dev/sda5           77824       77825       16033+  82  Linux swap / Solaris

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       51006   409600000    7  HPFS/NTFS
/dev/sdb3           51006      182402  1055432704    7  HPFS/NTFS

Any help or advice is appreciated.

---

### Post by darkod on 2010-01-30
In comes down to whether you want to use EasyBCD or Grub2. In your case, with two disks, it would have been better choice to put grub2 on /dev/sda (the MBR), not the partition /dev/sda1. Then you just set sda is the first boot option in BIOS and grub2 loads with options for ubuntu and win7.
If by any chance grub2 is messed up, and you need your win7 urgently, you can still boot it by switching the order in BIOS because you have windows bootloader on /dev/sdb.

On the other hand, using EasyBCD requires installation of grub2 on a partition I believe. And it would mostly be used in single disk situations when you don't want to remove windows bootloader from the MBR. Then you would have no choice but to put grub2 on a partition and use EasyBCD to chainload to it.

---

### Post by presence1960 on 2010-01-30
Easy BCD is totally unnecessary. GRUB does the job all by itself. And YES you should have put GRUB on MBR of sda by putting it on /dev/sda

---

### Post by VideoRoy on 2010-01-30
> **darkod said:**
> In comes down to whether you want to use EasyBCD or Grub2. In your case, with two disks, it would have been better choice to put grub2 on /dev/sda (the MBR), not the partition /dev/sda1. Then you just set sda is the first boot option in BIOS and grub2 loads with options for ubuntu and win7.
If by any chance grub2 is messed up, and you need your win7 urgently, you can still boot it by switching the order in BIOS because you have windows bootloader on /dev/sdb.

On the other hand, using EasyBCD requires installation of grub2 on a partition I believe. And it would mostly be used in single disk situations when you don't want to remove windows bootloader from the MBR. Then you would have no choice but to put grub2 on a partition and use EasyBCD to chainload to it.

Thanks for the information that helps a lot.  The other dual boots I have done, except for a triple boot have been on one disc which is why I probably chose /dev/sda1 instead of /dev/sda


> **presence1960 said:**
> Easy BCD is totally unnecessary. GRUB does the job all by itself. And YES you should have put GRUB on MBR of sda by putting it on /dev/sda

I know EasyBCD is unnecessary but I kind of got used to using it.  When I started the dual boot on this current system I am working on I only had a single 1.5TB drive and Ubuntu was not happy because it wanted to be on a Primary partition or overwrite my Win7 bootloader which I did not want to do.  When it did overwrite my Win7 bootloader I was able to fix it easily with EasyBCD.

Now that I have 2 disks, I may go back and use Ubuntu GRUB2 instead.  The only problem there is that I am not the only one using this computer and moving Win7 around to boot first is a pain in the neck although I can do it after having to learn Grub2 structure.

Thanks for all the help and advice! :D

---

### Post by VideoRoy on 2010-01-30
Ok, I guess I am still a little confused.

As a test I went into BIOS and changed boot order so my Ubuntu 9.10 drive was first priority and it booted fine no problems.

So somehow I achieved exactly what I wanted.  Either hard drive can boot by itself if it is the only drive in the system and regardless of which drive is primary, I can launch either OS from Win7 menu or Ubuntu OS Grub2 menu since it picked up the Win7 entry during install as well.  So I can make either drive primary.

This is exactly what I wanted but based on the previous replies I guess I am not sure why it works if the bootloader for Ubuntu was loaded on sda1 instead of sda. :confused:

As long as I have not set myself up for some problem later I think I am good to go.

---

### Post by presence1960 on 2010-01-30
> **VideoRoy said:**
> Ok, I guess I am still a little confused.

As a test I went into BIOS and changed boot order so my Ubuntu 9.10 drive was first priority and it booted fine no problems.

So somehow I achieved exactly what I wanted.  Either hard drive can boot by itself if it is the only drive in the system and regardless of which drive is primary, I can launch either OS from Win7 menu or Ubuntu OS Grub2 menu since it picked up the Win7 entry during install as well.  So I can make either drive primary.

***_This is exactly what I wanted but based on the previous replies I guess I am not sure why it works if the bootloader for Ubuntu was loaded on sda1 instead of sda. :confused:_***

As long as I have not set myself up for some problem later I think I am good to go.
To see your setup & boot process run the boot info script. It wiill answer all your questions and even tell you where GRUB is installed. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Look at the contents of that file for all the info you could ever want to know about your machine.

---

### Post by VideoRoy on 2010-01-30
Very nice script thanks! I am pasting only the relevant portion which is exactly as I thought it was.

> => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 159673559 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.imgHowever my system will boot to Ubuntu no problem even if I remove the Win7 drive and set BIOS to look at Ubuntu drive first.

So the bootloader does not have to be on the MBR of the drive to boot properly.  Whether this will cause me any problems later on I guess is the question.

Also I believe I can move the bootloader to sda without reinstalling but have not figured out if I really need to do that or the easiest method.  I have seen a couple of methods mentioned and I can think of a couple of other ways to try as well.

---

### Post by drs305 on 2010-01-30
The reason sda is preferred to sda1 is because of where and how Grub 2 writes the information. When a user installs Grub 2 on a partition a warning is normally presented warning about using blocklists to store the information. The warning is issued because if the blocks are reallocated...

Well, read it for yourself:
[And Blocklists?]("http://grub.enbug.org/BIOS_Boot_Partition")

---

### Post by kansasnoob on 2010-01-30
Well if you're like me and just love playing help yourself.

Otherwise, if it ain't broke don't fix it!

---

### Post by VideoRoy on 2010-01-30
> **drs305 said:**
> The reason sda is preferred to sda1 is because of where and how Grub 2 writes the information. When a user installs Grub 2 on a partition a warning is normally presented warning about using blocklists to store the information. The warning is issued because if the blocks are reallocated...

Well, read it for yourself:
[And Blocklists?]("http://grub.enbug.org/BIOS_Boot_Partition")
Thanks.  I assumed since the bootloader is in my sda1 partition I have an easier chance of messing it up and harder time to recover.

> **kansasnoob said:**
> Well if you're like me and just love playing help yourself.

Otherwise, if it ain't broke don't fix it!
Yeah, I am with you on the first item.  Long time computer geek and network engineer for ~15 years so I cannot help myself.  Still new to Ubuntu so I have been documenting my changes to the base install to make it easier next time.  This is about my 5th install on different computers (mostly junkers) but this unit I built from ground up to be my video editing rig.

I will practice moving the bootloader on one of the junkers and if it works no problem I will do it here.  If it does not work right I will reinstall again since I only have about a days worth of time into this one and I have my custom list.

---

### Post by VideoRoy on 2010-01-30
Ok, last question ;)

I tried this on my junker setup that had a similar bootloader setup where the drive was sdb instead of sda.

> sudo grub-install /dev/sdb

It seemed to work and results of the script now show there is a bootloader in the MBR.  There is probably still one on partition 1 as well but is that I have to do?

BTW, I really appreciate all the back and forth / help while I learn!

---

### Post by oldfred on 2010-01-30
I have 3 drives and 4 operating systems set up on my desktop. I install each operating system on a different drive and install that operating system's boot loader into the MBR of that drive. (except for one of course). That way if I need to I can in BIOS make any drive the boot drive and boot. But I always make a grub/ubuntu drive the first boot drive since it is very good at booting other systems. The only time I might switch drive order is to test something, update something or a hard drive failure.

---

### Post by VideoRoy on 2010-01-30
> **oldfred said:**
> I have 3 drives and 4 operating systems set up on my desktop. I install each operating system on a different drive and install that operating system's boot loader into the MBR of that drive. (except for one of course). That way if I need to I can in BIOS make any drive the boot drive and boot. But I always make a grub/ubuntu drive the first boot drive since it is very good at booting other systems. The only time I might switch drive order is to test something, update something or a hard drive failure.

That is my goal exactly except I use Windows as my primary.... for now.  Eventually this may become an Ubuntu only rig but video editing is not quite there yet so need to keep a few old Win programs around for a while that will not run in Wine.

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 159673559 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img



I am going to call this one solved because I easily moved Grub2 boot loader to the MBR of the drive in question with a simple grub-install.

Thanks all!  On to tackling some other quirks :p

---

