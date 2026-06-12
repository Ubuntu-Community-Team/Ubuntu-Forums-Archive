---
title: "External drive installation"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by ndiniz on 2014-01-18
I have an external drive with nearly 3 TB in capacity. I would like to use the entire drive for my Linux installation. I plan to run at least Ubuntu 12.1 but as for the others, I'm not sure. I also need to know where I should put GRUB. I'd appreciate it if someone could give me some suggestions as far as partitioning is concerrned.

---

### Post by TheFu on 2014-01-18
Don't allocate any more than you need.  Use LVM2 to manage space.  Setup partitions like this to start:
* / 20G
* /var 20G
* /home 30G - keep settings and documents that YOU edit, create here. Easy to backup.
* /data - whatever you need today for data. This is for media files like music and videos. Things that don't change too much.
* swap 2G or the amount of RAM in the system, which ever is greater

LVM makes adding storage to any partition trivial. No need to over think it now.

I hope you got two disks, so 1 can be a backup to the other. Every HDD will fail. They never fail when it is convenient. Some fail in the first 160 days and then about 5% fail per year. After 5 yrs, I start getting nervous about HDDs and replace them even if there isn't any issue. Old-age is an issue for HDDs to me, though I know many people running 10yr old HDDs happily ... though much slower.

You didn't mention anything about encryption either. That changes the layout slightly.

I really hope the external HDD is eSATA. USB seems to have problems with queuing, IME.  I'm not the only one with this issue - even on USB3. When more than a few processes try to use the USB channel, it sorta "gets stuck" - sometimes for 20-30 seconds - where it does nothing. Not good for an OS. Of course these issues may have been corrected by newer drivers or USB3 firmware.  It would be too painful to consider using USB2, IMHO. Heck, even for backups USB2 is painful.

---

### Post by tfrue on 2014-01-18
This is really simple to do, so I hope you will be surprised lol.

Live boot Ubuntu, click on the installer, click Something Else, click on the appropriate drive( like /dev/sdb), and use the whole drive, you should use /dev/sda as the grub install point, and let it be.

That should be it.

Grub will install in it's appropriate places and you will have two partitions on the disk when it's all said and done, one for / and the other swap.

If you want to know, grub will install on /dev/sda, which should be the first HDD on your system. We want to do it that way so you will not have two boot loaders on one machine.

Good luck, 
Chris

---

### Post by ndiniz on 2014-01-19
I think I do need to format my drive as FAT32, and I probably also have to adjust my BIOS so that it runs in UEFI mode, since I'm running Windows 8.1. Am I correct? I do have a lenovo desktop by the way.

---

### Post by Bucky Ball on 2014-01-19
Little off-topic, but I would advise against Ubuntu 12.10. a) it is only supported for another few months, until April and, b) 12.04 LTS or 13.10 are better choices as they are both directly upgradeable to 14.04 LTS, to be released in April and a long-term support release with five years support. 

As you were ... and good luck. ;)

If Win8 is running in EFI you have to install Ubuntu that way. Switch off fastboot, secureboot in the BIOS and boot into Win8 and disable faststart in there. 

EFI makes previous advice about grub redundant as it will install 'automagically' to the EFI partition which was created by Win8. That's what you want.

When you get to the partitioning section of the install, you must choose 'Something Else' and partition manually. A basic setup for that drive would be:

/ - root; your OS, you need not more than 20Gb;
/home - your personal data, the rest of the drive, but leaving;
/swap - swap, 2Gb fine unless you hibernate in which case it should be same size as your RAM.

Put /swap at the end.

As I say, don't do anything with grub. When installing EFI Ubuntu will find the existing EFI partition and stick it there without help. Just make sure you DON'T mark that partition, or any other existing partition, to format.

Good luck.

PS: DO NOT format the disk as FAT. Think you are getting confused with the requirements of the EFI partition (a tiny one of about 100-500mbs). You will see that when you are partitioning during install. It will be marked as a FAT partition. Leave it alone. Don't format, don't change its name. Don't even look at it! Well, yea, you can look at it. Just leave it alone. Win is relying on it and Ubuntu installed in EFI is relying on one to be there.

As the EFI partition will be on another drive, you may have to force grub-efi  to install there. Not sure, never done it on two separate drives. :-k

---

### Post by Bashing-om on 2014-01-19
ndiniz; Hi !

It is your system and no one can tell you how you will run your system. All we can do is give you a running start !

ubuntu's default file system is 'ext4', so if you are going to slice up that drive to accommodate additional operating systems set aside ubuntu's partition as a minimum of 30 gigs - ubuntu's partition editor is GParted -//NTFS is a univeral file system format to share with other operating systems.
Install:
leave that space for ubuntu as 'unallocated' the install wizard will do the formatting ;
In the actual install - choose -> something else - and make sure that unallocated space is selected ;
Once you have the drive set up, and ubuntu installed you will then need to make sure that grub *Grand Unified Bootloader * - at the end of the install process - is installed where you want it. Your use dictates where to install/

It is as simple as you make it, this is all there is too it.

[INDENT][INDENT][INDENT]it ain't no big deal
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-01-19
Please note: OP has confirmed Win8 is installed in EFI. Even though this install is on a separate disk, think that dictates what happens with grub. For a start, it will not be grub-pc, as referred to so far, but grub-efi that gets installed.

---

### Post by Bashing-om on 2014-01-19
Bucky Ball; Noted.

Me got to get caught up with the new fangled ways. EFI do put a different slant on things .

[INDENT][INDENT]progress
[/INDENT][/INDENT]

---

### Post by ndiniz on 2014-01-19
I did a complete wipe of my external drive. I also did a conversion from MBR to GPT. Is that required? I know my main hard drive is GPT.

---

### Post by Bashing-om on 2014-01-19
ndiniz; Good !

That is correct. With Windows 8 one has to match with windows (GPT)  EFI  boot code. As Windows is installed EFI  so must ubuntu be installed in EFI mode also. As Bucky Ball advised above, EFI requires that the hard disk be partitioned as GPT. 

You are getting there ->
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by ndiniz on 2014-01-20
Now what about the file system? I have FAT32 and NTFS. What file system should I use?

---

### Post by Bashing-om on 2014-01-20
ndiniz; Hey,

If it remains your goal to install ubuntu as the sole operating system - and nothing else - on that 2nd hard drive:
Do not concern your self with formatting that drive, the install wizard will take care of that detail ( and set the file system type to the default ext4)
 - Be advised this will not use a lot of space, the initial install of ubuntu is but around 30 gigs. The remainder of that drive will not be used for a long long time.

Now as to grub, how do you want to boot the system ?
If you choose so at bios to set the booting hard drive, set grub to the MBR of that second drive;
If you choose so as to ubuntu to control what operating system to boot, then in bios set the boot priority to boot that 2nd hard drive, update-grub (os-prober) will pick up the windows operating system and chainload it to the grub's boot menu.

Doing it the above way, Window's install will not be touched, and in the event you have the need, you can boot Windows directly just by changing the boot priority in bios to that hard drive that Windows is installed onto.

[INDENT][INDENT]it can be as easy as
[INDENT][INDENT][INDENT]falling out of bed wide awake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndiniz on 2014-01-20
OK, here's an interesting thought: Let's say that I decide to automatically launch windows if I have the external drive disconnected Is there a way that I can make GRUB probe my hardware & see if the external drive is connected? If so, I want to make sure that it allows me to run Ubuntu IF the external drive is connected. Otherwise, it should automatically launch windows 8.1

---

### Post by ubfan1 on 2014-01-20
Just change the device boot order to have USB (and DVD) before the hard disk.  Without the USB disk, Windows should boot.  No nvram entries need to be made.  No changes are even needed on the  hard disk's EFI partition if you have an EFI partition on the USB hard disk.  Now the install will ask you for the location for the bootloader.  You should specify the USB's EFI partition.  (I think 12.10's installer will ignore you anyway and just use the hard disk's EFI, but 13.10 should use what you specify.  If the Ubuntu files get put into the USB's EFI partition, they will be under directory /EFI/ubuntu.  But since the USB is a removable media, the default bootloader is actually /EFI/Boot/bootx64.efi.  Make bootx64.efi a copy of shim.efi (for secure boot enabled), or the unsigned grubx64.efi (without secure boot).  For secure boot, also copy the signed grubx64.efi into /EFI/Boot.  The 13.10 install should use a 3 line grub.cfg file which pulls in the maintained grub.cfg from the /boot/grub directory, so no further changes ever need to be made to the EFI partition.  This USB with it own EFI should boot on any UEFI machine (provided you have the correct secure boot setting you used).

---

### Post by Bashing-om on 2014-01-20
ndiniz; WOW !

Sure, this is linux, all things are possible, but this would sure be a confluent mess. Depending on your priorities. The only way I can see to make that arrangement work is a minimalistic install of ubuntu onto the same hard disk with windows, and the actual install of ubuntu in  it's dedicated partition on the 2nd drive with some wild mount options in the /etc/fstab file of ubuntu on that 1st hard drive. Else, if we have to get real fancy with if statements with regards to os-prober and grub's config files, boot time could be long long delayed !

Windows8 - UEFI- is in play here; this arrangement would be even more taxing to implement and no way to keep from messing with Windows boot code.

The simple thing (simple is better) is to boot the operating system of choice by setting the boot priority in bios at boot time. You know that the 2nd disk is connected so just set the bios boot priority to boot from that device when you want to boot up ubuntu.

[INDENT][INDENT]one huge step

[/INDENT][/INDENT]

---

### Post by ndiniz on 2014-01-21
I need to figure out something here. I may have had a little trouble with GRUB. I need to do a complete profile check on the partition table I have for my windows 8.1 installation so you guys can help me figure out where to put GRUB. I'll work on getting the profile done later. Linux IS on my external drive.

---

### Post by ndiniz on 2014-01-21
OK

Here's what I have as far as windows 8...

Main hard drive is C:\ which, according to the computer is /dev/sda

here's what I have on it:

> /dev/sda1 is NTFS, space used is 489  out of 1048 MB
/dev/sda2 is fat32, space used is 33 out of 272 MB
/dev/sda3 is fat32, space used is 277 out of 524 MB and is a windows recovery environment
/dev/sda4 is unformatted and has 134 MB available
/dev/sda5 is NTFS, space used is 172175 out of1971836 MB and is the windows 8 loader
/dev/sda6 is NTFS, space used is 294 out of 367 MB available
/dev/sda7 is NTFS, space used is 12406 out of 26214MB available
if I had wanted to run the GRUB from my main hard drive, where would I put it?

---

### Post by ndiniz on 2014-01-21
ok. Do I need to provide my external drive with a /boot area, and how big should it be? Also, should GRUB be put there?

---

### Post by TheFu on 2014-01-21
**sudo parted -l**
put inside "code" tags on the forums (Adv Reply) would be helpful. That way we get all the data directly from the hardware, so it can be more accurate.

Actually, if you could run the **boot-info** script, that would be even better. See my signature for links.

---

### Post by oldfred on 2014-01-21
I would make sure to have an efi partition on external drive, so you can boot from it. But you can install grub2's efi files to either drive(or both, but then will have duplicate entires in UEFI menu). The advantage of having the efi on the external is that then you can boot from that without the internal drive.

If you do LVM, then you still need the efi partition and default Ubuntu with LVM full drive install also has /boot as separate partition. But you have to use manual install not any auto install options since installing to external drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by ndiniz on 2014-01-22
ok, I was able to successfully install Ubuntu, but, for some stupid reason, when I press F12, my external drive doesn't show up. I know I was able to boot it once before from the external drive, but I can't remember how.

---

### Post by ndiniz on 2014-01-22
I do know that some things in my bios need to be disabled in order to get the external drive to boot, so what I need to do, for the time being is write down the BIOS info, and the options available so someone can tell me what I need to disable.

---

### Post by oldfred on 2014-01-22
Do you have secure boot on? There may be other settings in UEFI/BIOS also that are needed, but lets check install.
What system is this as settings can vary a lot.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ndiniz on 2014-01-22
This system is a Lenovo H430

I have attached a Zip file with a Microsoft Word file that has the current BIOS configuration (with Optimized defaults enabled)

---

### Post by oldfred on 2014-01-23
It looks like you have boot from USB off.
> 
   [COLOR=#262626][FONT=Arial, serif][SIZE=2]Excluded from boot order is USB HDD and USB CDROM

You also have secure boot on, which may work, but often better with it off.
[/SIZE][/FONT][/COLOR]
Not sure what difference is between Quick Boot and Rapid Boot? I just know that anything related to Windows hibernation which is usually called one or the other should be off. And if you have Intel SRT that must be off.
   

> [COLOR=#262626][FONT=Arial, serif][SIZE=2]Quick Boot is Enabled (can be set to disabled)[/SIZE][/FONT][/COLOR][COLOR=#262626][FONT=Arial, serif][SIZE=2]
[/SIZE][/FONT][/COLOR][COLOR=#262626][FONT=Arial, serif][SIZE=2]Rapid Boot is disabled and greyed out[/SIZE][/FONT][/COLOR]



---

### Post by ndiniz on 2014-01-23
Secure Boot is now disabled and I've adjusted the boot order

What do I do now?

---

### Post by oldfred on 2014-01-23
Can you now see external drive?

Post Bootinfo just to see details on install.

---

### Post by ndiniz on 2014-01-23
I'm going to attempt the install later on.

---

### Post by ndiniz on 2014-01-23
I have confirmed that I have Ubuntu 12.04.3 LTS on my flash drive. I was able to get into Ubuntu 12.04.3 LTS from my flash drive. Would it be better for me to install in Persistent mode, or Live mode?

---

### Post by oldfred on 2014-01-23
While still an install to another drive a flash drive install is a bit different than to a 3TB drive.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)
Live session failed to start from USB with persistence enabled
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1239833](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1239833)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by ndiniz on 2014-01-23
OK, this is absolutely weird. When I go to make the partitions, the space on my external drive is shown as only 375 GB. Why?

---

### Post by oldfred on 2014-01-23
Post this for whatever the drive is sda, sdb, or sdc.

 sudo parted /dev/sda unit s print

sudo parted -l

---

### Post by ndiniz on 2014-01-23
ok, the disk file type was FAT32. I changed it to NTFS and everything is fine again.

Now it's a matter of figuring out what other bios settings I need to make. Any suggestions?

---

### Post by oldfred on 2014-01-23
May vary by brand, model, chip & video chip.

But if Windows 8 you must have fast boot off and probably better with secure boot off.

---

### Post by ndiniz on 2014-01-24
oldfred, look at my bios configuration! I have it in a zip file.

---

### Post by ndiniz on 2014-01-24
For now, I consider my attempts to be a complete failure. I'll try again at the end of the summer. My external drive got damaged by me by accident and since I can't get it repaired, I'll have to buy a new one. Trying is all I can do.

---

### Post by ndiniz on 2014-01-27
Actually, I won't! I am actually in the middle of wiping my external drive clean of any residual data. I just read an article on Ask Ubuntu about having to compile, and build the latest grub bootloader. I may have to do that before I can do anything else. I refer you to this: (I think this is a work-around for both Windows & Mac OS X computers.)

[http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi](http://askubuntu.com/questions/91484/how-to-boot-ubuntu-from-efi-uefi)

---

### Post by oldfred on 2014-01-27
That link is to 11.10, grub2 has changed a lot since then. After 12.04.2 it will boot with UEFI secure boot. 

And major changes in 13.10 and soon in 12.04.4 in about two weeks.

And 14.04 has an even newer version.
[http://www.omgubuntu.co.uk/2014/01/grub-2-beta-ubuntu-14-04-lts](http://www.omgubuntu.co.uk/2014/01/grub-2-beta-ubuntu-14-04-lts)
[https://lists.ubuntu.com/archives/ubuntu-devel/2014-January/037978.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-January/037978.html)

But vendors also are updating UEFI/BIOS to fix errors and make improvements.

---

### Post by ndiniz on 2014-01-27
But do you think I should try it just to see if it works?

---

### Post by oldfred on 2014-01-27
When I got my new huge 640GB drive several years ago, I only needed two 100GB data partitions. And I left the rest unallocated. Then I added 25GB partition for a new install just to try it. Then  anther, etc. drive is almost full of installs as I had room, but most now are obsolete and need housecleaning.

Or I am the last one to ask about trying a new install. My answer always is yes. :)

---

### Post by ndiniz on 2014-01-28
Just some info I need on step three on that guide I found.
[LIST=1]
[*]Install the system into the hard drive "/" partition and remember to point here the bootloader (GRUB 1.99) to install to. If you've created a separete "/boot" partition, you have to choose that one for the bootloader installation.
[/LIST]

---

### Post by oldfred on 2014-01-28
If a BIOS system:
I do not know what instructions you have, but normally you install grub to the MBR of a drive or sda not to any partition like sda1. BIOS only boots from MBR.
Boot loader is different than grub menu & kernels which are in the boot folder whether a separate partition or within / (root). Usually most desktops do not need /boot in a separate partition. But if RAID or LVM you may need /boot separate. Some old systems only boot from first 137GB of a hard drive and a separate /boot may fit easier inside the first 137GB.

If a UEFI system:
You still install grub2's boot loader to sda, but the efi boot files will be in the efi partition with separate folders for every different install. The efi partition has a boot flag, but that is just the way parted & gparted assign the long GUID to make an efi partition in gpt partitioning. Not really the same as a boot flag in BIOS/MBR which is to identify the Windows partition with boot code. Grub does not use boot flag in BIOS.

---

### Post by ndiniz on 2014-01-28
ok, I've done a re-install of Ubuntu to my external drive. I need to figure out exactly what I need to do to get to my external drive.

---

### Post by oldfred on 2014-01-28
If you cannot select Ubuntu or external from BIOS.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by ndiniz on 2014-02-01
I do think I may have this problem solved. I'm downloading Ubuntu Studio 13.1 32 bit. I think it may end up working. I'll see about testing it sometime today.

---

### Post by oldfred on 2014-02-01
Any 32 bit will only install in BIOS boot mode, it has no UEFI. But  still should work, if you boot from UEFI/BIOS menu in BIOS mode. But you have to switch to UEFI mode to then boot Windows.

All new 32 bit versions have PAE to address more than 4GB of RAM, but have to switch it in and out as it cannot directly address it like 64 bit versions. So new systems should use 64 bit version.

---

### Post by ndiniz on 2014-02-02
I had read something here on the forums that someone had trouble getting some kind of distro for Linux to boot from the external hard drive he had, which was a Toshiba, and since I have a Toshiba 3 TB External drive, I thought I'd give the suggestion I found a try. I ran Bootinfoscript, and the attachment I have is the result.

---

### Post by oldfred on 2014-02-02
You only show one huge NTFS partition on your 3TB drive.
You need to install Ubuntu in UEFI boot mode. The efi partition needs to be near front of drive. And Ubuntu / (root) partition should not be over 25GB.

You should partition in advance with gparted and then use Something Else or manual install to make sure you install grub to the 3TB drive's efi partition.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by ndiniz on 2014-02-02
OK, now attempting installation from previously suggested disk partitioning scheme.

---

### Post by ndiniz on 2014-02-02
OK, I've got the installation completed, but I still can't get my computer to boot from the external drive. I did everything that was suggested in the last post before installation. I must be an idiot. I'm mad at myself. What should I do? I'm going to try it again later on. I'll wipe the drive clean and try it again.

---

### Post by oldfred on 2014-02-02
Best to see what may be wrong.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by ndiniz on 2014-02-03
Now that I think about it, would it be possible for me to have GRUB run on my computer's main hard drive?

---

### Post by oldfred on 2014-02-03
I install grub2 everywhere. But sometimes it takes some effort to configure it correctly. And now the new UEFI systems have made it a bit more complex as you have to know if booting in UEFI or BIOS mode.
But since installer boots in either mode there are ways to configure both.

---

### Post by ndiniz on 2014-02-11
Well, my external drive conked out on me yesterday, but I think part of my problem is that I had to set the disk as Active.

---

