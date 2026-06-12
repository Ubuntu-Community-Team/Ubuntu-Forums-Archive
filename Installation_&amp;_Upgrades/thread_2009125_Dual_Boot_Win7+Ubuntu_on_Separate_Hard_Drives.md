---
title: "Dual Boot Win7+Ubuntu on Separate Hard Drives"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by RapboY on 2012-06-24
Hi there everyone!

Need some help. I just bought parts for a new pc I'm building next week. It's an i7-2600K and GTX 570 system for multimedia content creation and some gaming. 

I want to install Ubuntu because first it's cool. Second, I'm a fan of open source. Main thing I want to learn is using open source programs (Blender, GIMP, etc) in Ubuntu. 

I have two Hard Drives, one SSD (Samsung 830 128gb) and the other a 7200 RPM HDD (Seagate Barracuda 3tb). I'm gonna be installing Windwos 7 on the SSD, and I was thinking about installing Ubuntu on a partition on the HDD. Then I could just switch OS's using the BIOS. Would this work properly? 

And if yes, can you please help me and explain how I can set it up like that. If no, then please explain to me a better way I could do this. But I'd really rather keep the SSD for Windows OS and programs. 

Also if not, is it possible to install Ubuntu on virtualbox but still get great performance for what I want to do? Thank you so much!

EDIT: By the way, another reason I want to keep them on separate drives is that I've tried the normal Dual-Boot thing before and it worked for a while, but I had some problems after so I decided to get rid of it. I want to give it another shot!

---

### Post by nipunshakya on 2012-06-24
Here's my suggestion.... install ubuntu and windows 7 on the HDD of 3tb. allocate 100gb for windows(primary NTFS), around 100 gb for ubuntu(extended partition with /,/home and swap in it as 15-20,75-80 and 4gb respectively ) and you are good to go... you can use the ssd as a storage media too... by that way, you shouldn't have to work around at BIOS everytime you wish to switch between your OSs...just a selection at the grub will do all.... you can use the rest of the 3tb space as an NTFS partition, to share data between the windows and ubuntu as well... 

you can use gparted for partitioning your 3tb HDD by studying the lik below...:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

and take a look at installing a dual boot on your system by following link: (install windows first and then ubuntu)
allocate 100 gib for windows first, using windows installation disk, and then after installation is done, use ubuntu LiveCd and allocate necessary partitions for ubuntu as well...:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

Just ignore the boot partition mentioned there in the second link as well..

---

### Post by oldfred on 2012-06-24
If a new i7 system the motherboard will have UEFI and BIOS. UEFI is the new way and uses gpt partitioning. BIOS uses MBR partitioning for Windows, but with Ubuntu you can use gpt but need an extra bios_grub partition with gpt & BIOS installs.

Best to install both systems as UEFI or as BIOS. Both Windows & Ubuntu should from the UEFI menu give you UEFI or legacy/BIOS/AHCI install options. For all installs best to format drives in advance. 

Your 3TB drive will have to be in gpt, MBR only goes to 2TiB.

With nVidia you will need the nomodeset option to get it to work.

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by RapboY on 2012-06-24
Wow that's a lot of links guys! I'll read them all and see if I can make a decision then. More suggestions are very welcome :)

EDIT: btw yes it's a new mobo, ASRock Z77 Extreme4.

---

### Post by RapboY on 2012-06-25
Would this link work? I think this is basically what I want to do. [http://www.sevenforums.com/general-discussion/181686-i-need-help-dual-boot-windows-7-ubuntu-seperate-hds.html](http://www.sevenforums.com/general-discussion/181686-i-need-help-dual-boot-windows-7-ubuntu-seperate-hds.html)

Or would this be better? [http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/2/](http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/2/)

I don't understand what it means to install in UEFI, or install in BIOS. Isn't UEFI just a graphical BIOS? Sorry I'm confused. If I install through UEFI, I won't need to deal with Windows Boot Manager right?

Ugh, I hate how this is so much work. I don't understand why there isn't a single easy answer to this. I think how I want to set it up makes so much sense, I really find it weird to have an easy answer for it.

EDIT: Seems like ASRock UEFI doesn't have boot order? [http://www.tomshardware.com/forum/313179-30-extreme-boot-order](http://www.tomshardware.com/forum/313179-30-extreme-boot-order)

---

### Post by darkod on 2012-06-25
Look in the board manual if there is a way to disable UEFI boot. If there is, what you want to do should be easy, since you want win7 on the SSD and you can use it with msdos table if not using UEFI.

Check that first and let us know.

---

### Post by RapboY on 2012-06-25
> **darkod said:**
> Look in the board manual if there is a way to disable UEFI boot. If there is, what you want to do should be easy, since you want win7 on the SSD and you can use it with msdos table if not using UEFI.

Check that first and let us know.

You kinda lost me there.. What do you mean I can use it with msdos? and why would I want to disable UEFI boot?

---

### Post by darkod on 2012-06-25
You would want to disable UEFI since it makes things simpler not to use it. And personally I don't see any benefits from it.

I mentioned msdos partition table. Today mostly two types are used, msdos or gpt table, with msdos still being used a lot. But with the new UEFI boot process, win7 can work only on gpt table.

So, if you decide to go with UEFI, the choice of a partition table is already made, it needs to be gpt.

oldfred gave you links about UEFI dual boot. You mentioned most of it is complicated and looked for easier solution.

In my opinion, that easier solution is not using UEFI. But you need to see if your board can boot in the old fashioned BIOS mode, or only in UEFI.

You are free to use the UEFI on your board, no problem. But in that case start reading the links from oldfred. I'm not saying you need all of it, but there is important information, especially about the dual boot on UEFI. I am not using UEFI so I can't give you exact steps to follow.

The UEFI + gpt combination is quite new on a PC, so maybe all the problems are not ironed out yet. But people have reported successful dual boot with UEFI so it's not impossible. However that would mean you will have to learn new things since the whole setup is new technology. If you don't like that you other option is to try use BIOS boot on your board in which case the partition table on the SSD will need to be msdos so that win7 can work. The partition table for the 3TB will still need to be gpt because disks over 2TB need to use gpt, but that is not a problem since ubuntu can work on gpt with BIOS boot.

---

### Post by oldfred on 2012-06-25
The USB flash drive or CD install version of Ubuntu (and I think Windows) have both efi & BIOS (AsRock calls BIOS mode AHCI). So from UEFI menu bar boot menu and booting from install medium you should get two choices.

How you boot installer then determines how it is installed.

For your 3TB drive I would create both efi partition and a bios_grub partition. Then you have the space allocated to boot either way or could change later without major reformating. The efi partition has to be first so it would be difficult to add later.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

With a 3TB drive I would not create one large /home or data partition. If a NTFS a for sharing data with Windows a chkdsk or defrag and a huge partition can take forever. The only place it may be better as one partition would be for a video server. If not sure you can always leave space unallocated. With my ,then large 640GB drive I left space unallocated and have just added 25GB / (root) partitions for installs of Ubuntu and a few other systems to try out.

---

### Post by RapboY on 2012-06-26
I'm usually good at stuff like this, but right now I'm totally confused. Thanks for the effort guys, I'm still trying to understand all the info. 

Basically right now this is what I want to do. Is this really not as simple as I think it is?

1-Install Windows 7 on SSD.
2-Remove SSD.
3-Install Ubuntu boot(20GB)/swap(8GB-I have 16GB RAM) partitions in 3TB HDD. Will those be enough? 
4-Do I have to reformat what's left of the HDD to NTSC?
5-Put SSD back. 

And in my mind this is the way it's gonna work:
1-Disable Windows Boot Loader from popping up (if it's popping up)
2-PC goes straight to Windows when I press the power button on my pc.
3-If I want to go to Ubuntu, I press F11 (or whatever is the button for Windows Boot Manager) and so Windows Boot Manager shows up and I choose Ubuntu from the list.

Will that work? Is that possible?

---

### Post by darkod on 2012-06-26
If using the good old BIOS boot, it would be like you say. With a little change that before installing ubuntu you will have to create a small 1MB bios_grub partition on the 3TB disk because it needs it to install on gpt.

You don't have to format the rest of the 3TB but if you don't format it as anything, you end up with 3TB disk which has only 28GB used right? You have to format it as something in order to use it.

It can be one or more partitions, ntfs or ext4. It's up to you. You can even have a separate /home partition on it so that you can easily make clean installs of ubuntu in the future.

But with UEFI, I don't know how it affects the above. For example, with two disks in the system, do you need only one EFI System partition, or one partition on each disk. oldfred, do you have anything on this?

Because if there needs to be only one EFI System partition, it will be created on the SSD while installing win7. And if you disconnect it during the ubuntu install, ubuntu will not be able to put its boot files on it.

That's why I said it might be easier to disable UEFI if it's possible. If you go with UEFI, you are bound by the rules that apply to it. I don't have UEFI so I can't even test. I really don't know what changes it brings in your situation compared to the older type BIOS boot systems.

---

### Post by RapboY on 2012-06-27
ah ok, now I understand your point. 

Hmm.. this is looking a little more complicated than I wanted to be. I'm starting to second guess if I should try this again. Ah well, hopefully I learn more this week as I wait for my computer parts to arrive and after I build it. 

More suggestions (hopefully simpler and more straightforward) still very welcome! And thank you to everyone who have been trying to help me so far.

---

