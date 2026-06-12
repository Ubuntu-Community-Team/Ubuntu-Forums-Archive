---
title: "How to install to separate Linux partition without damaging windows"
date: 2021-01-22
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2021-01-22
Hello all!   It's been 13 years since I had a working Linux machine and I want to rectify that.   I had terrible experience with the installation in 2008, and was hoping someone could guide me through a good install this time.

Last February, I bought a new 500GB SSD, with the intention of installing both Windows 7 and Ubuntu on it.  Yes, I know Windows 7 is no longer supported, and a security risk.  But  I wanted to run some old Windows engineering software, and do my browsing and other work with Ubuntu.  So when I installed the SSD, I created 4 partitions - a NTFS partition for Windows 7, a swap partition for Windows, an EXT3 partition for Ubuntu, and a swap partition for Ubuntu.  Due to a death in the family and this crazy virus, I'm only just now am getting around to installing Ubuntu.

 I put the 18.04.3 LTS installer on a CD.   My hardware is old, so I thought 18.04 would run faster than the current LTS version.  I booted up with the CD, and selected install.    It detected Windows 7.  I told it I wanted to keep and use the Windows 7 installation.  Then came the problem...  WHERE to install.   I started the partition manager, and it asked me to select a partition for the boot loader.  I don't understand mount points and boot loaders.  I tried selecting the EXT3 partition for the boot loader, and the installer would not continue. Do I select the NTFS partition for the boot loader?  Will it then ask me where to install the kernel and apps? Or will it put the kernel on the NTFS partition?   I did not want to destroy my Windows 7 installation, so I exited and sought out the experts here.  

Thanks for listening!  Hope you can help me.

---

### Post by ubfan1 on 2021-01-22
Just how old is your hardware?  Pretty much verything after 2011 has UEFI capability, even if it wasn't used, and it sounds like you booted the Ubuntu install media in UEFI mode (depends upon the BIOS/UEFI settings of your machine, since the ISO does both), and it got confused because you didn't have an EFI partition on the disk. Install Ubuntu in the same mode as Windows.  Win7 is USUALLY in legacy mode, and if it boots without an EFI partition (but it could be on another disk), and the disk partitioning is MSDOS instead of GPT, Win7 is in legacy.

---

### Post by oldfred on 2021-01-22
Original Windows 7 ISO was BIOS only, but could be copied to flash drive, files moved & renamed to make it UEFI. But the updated one, included the UEFI boot files. 
So then it installs in the boot mode that you boot the installer.
New systems then should show in UEFI boot menu, two options to boot flash drive, if UEFI Secure boot is off, one UEFI:xxx and just xxx for BIOS.

Actually newer versions of Ubuntu often work better, even on older hardware.
If before about 2012, then likely to be BIOS only. Windows required vendors to install Windows 8 in UEFI mode to gpt partitioned drives starting in 2012.

Also better to use ext4.

If older, lighter weight flavor better as less gui resources required.
Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
[https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)

Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

My 2006 Core2 64 bit laptop with only 1.5GB of RAM, would not install 20.04 Ubuntu desktop. I had to install 20.04 server & added fallback which is another light weight gui similar to old gnome2. Like Ubuntu was in 2008 with some updates.
I then installed Kubuntu since changed to that on my main system and it worked acceptably well.

---

### Post by vidtek on 2021-01-23
I'll stick my 2 bob's worth in here.

500gb ssd, you have already installed win7 but you do not state in what mode, old bios or UEFI.

This is how to proceed with UEFI boot:
Win 7 will already have made an EFI partition, probably sda1.  

You will need to partition the drive with the linux installer -> choose manual partitioning.

***Delete all the partitions you have made for linux (not windows or the EFI partitions), you can do this in the installer and then you will get the correct flags.***

My advice would be to create 2 or 3 extra partitions, one about 50gb for linux (this will be more than adequate - 25gb is the recommended size I think), and whatever is left for your home directory.   I would use ext4 for these for simplicity.
If you have less than 8gb ram, I would also create a swap partition of at least 16gb.   If you have 16gb or more of ram don't bother with swap.

This next bit is critical.   **[COLOR="#FF0000"]You MUST identify your EFI/BOOT partition, it will be a FAT32 and will probably designated sda1 and set the efi/boot flags on it in the installer[/COLOR]**

[COLOR="#FF0000"]**Set the flags on your linux partition as /  and your home partition as /home.**[/COLOR]

You do this in the drop-down box in the partitioning menu when choosing the partition type-fat32, ext2, ext4, btrfs etc.

This procedure is only if win7 is installed in UEFI mode.  If win7 is installed in bios mode I would personally start again from scratch with an UEFI install for win7.   That way you would have a system which is using current practice.   

Cheers, Tony.

---

### Post by yancek on 2021-01-23
You never install a Linux (Grub) bootloader to an ntfs partition.  You should leave the default for device for bootloader installation which in your case with only one drive would be the SSD on which you are installing Ubuntu.  If you install Grub to the Ubuntu partition it won't boot as you also need Grub code in the MBR.

---

### Post by grahammechanical on 2021-01-23
I have been trying to find some pictures/images that show what we mean when we explain in words what we have to do. This is what I have come up with. It is Ubuntu Mate but the images also apply to Ubuntu

[https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651](https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651)

At the first Installation Type dialog select Somethine Else
At the second Installation Type dialog select the partition you want to install Ubuntu in. Then click the Change button.
At the Edit Partition dialog you can change the size of the partition if you want and if there is unallocated space around it.
In the Use As panel select Ext4 journaling file system from the drop down menu.
Tick the box to format the partition
Then in the Mount Point panel select / from the drop down menu
Click OK

Even if you have not changed the partition size you will see a dialog with the option to Go Back or Continue. Click Continue
When back at the Installation Type dialog confirm the device [drive] for the installation of the boot loader. If there is only one drive, then there is only one device/drive that the boot loader can go.

If you decide to have a separate partition for Home you do the same as before but select the partition that you want as Home and this time set the mount point (or flag) to /home.
The procedure for giving Ubuntu a swap partition is the same but the mount point is /swap. Although you might not needed it with Ubuntu 20.04 as that version uses a swap file.

The guide that I have linked to is showing a dual boot between Windows 7 and Ubuntu on the same drive. Similar to what you are desiring to do. I prefer to use GParted in a Ubuntu Live session to create my partitions and then use the installer to assign them mount points.

Regards

---

### Post by Engineeringtech on 2021-01-23
> **ubfan1 said:**
> Just how old is your hardware?  Pretty much verything after 2011 has UEFI capability, even if it wasn't used, and it sounds like you booted the Ubuntu install media in UEFI mode (depends upon the BIOS/UEFI settings of your machine, since the ISO does both), and it got confused because you didn't have an EFI partition on the disk. Install Ubuntu in the same mode as Windows.  Win7 is USUALLY in legacy mode, and if it boots without an EFI partition (but it could be on another disk), and the disk partitioning is MSDOS instead of GPT, Win7 is in legacy.

Sorry for the delay in responding.  I've been laid up.  No UEFI. I built my machine in late 2008.  Good quality gaming components.  I had so much problem with the installation that it sat unused for close to three years.  The SSD, is a Samsung 860 SATA purchased last Jan /Feb.   I do not understand your directions.  Same mode as Windows?  Legacy mode?

---

### Post by Engineeringtech on 2021-01-23
Thanks everyone.  It's going to take sometime to digest this.  I don't realky understand what UEFI is, but I doubt my 2008 MB  has it.  All I know is when I opened the partition manager it found the four partitions I made last year with my standalone partitioning tool, and it asked me where to put the bootloader.  I did not see a DOS partition in the list, just the Win 7 (on NTFS), the empty EXT3 partition, and the swap partitions I had made.  Do I direct the installer to put the bootloader on the NTFS partition?  Will it then allow me to put the kernel and apps on the EXT3 partition?  I hate to risk reformatting now, as I'm likely to screwvup and damage the Windows boot.

---

### Post by oldfred on 2021-01-23
You always install boot loaders to a drive, never to a partition.
BIOS systems boot from the MBR, which is the very first sector on a drive and is not part of any partition.
Grub does have additional boot code hidden in the sectors just have the MBR and before the first partition, but that is all automatic & you do not see that.

If from 2008, then a BIOS only system.

Windows requires MBR partitioning if in BIOS boot mode, so you have the 4 primary partition limit.
You can have any of the Linux partitions in a logical partition, but Windows can only boot from a primary NTFS partition with the boot flag.

---

### Post by Engineeringtech on 2021-01-24
GrahamMechanical-
Thank you for the link to the procedure.  My inference from the discussion is that "/" is the location the kernel/OS, applications will be installed, and "/home" is where user data will go.  Is that correct?  Can I direct both "/" and "/home" to the same partition? Or alternatively, can I place "/" in my EXT3 partition, and / "/home" in my NTFS partition?  (I did not setup a separate partition for my Windows data.  It's in the MyDocuments folder in the same NTFS partition as the Windows OS.)   Is there a good reason why I should reformat to EXT4?

Oldfred-

So "/" does not identify the location of the boot loader?  And I should select "sda", rather than a partition for it's location?  I only have the one drive with four partitions.  I believe when I partitioned the drive with Partition Commander that I made four primary partitions.


I really don't understand all this terminology.  I wish someone would define "mount point" "/" , "/home", for me, and or direct me to a diagram or video which explains the structure of Ubuntu Linux.  I know for instance that Windows places the OS in the "System" folder, and applications in their own folder.  I assume Linux has something similar.

I'm 66 and in very poor health, with failing vision.  This stuff is tough for me to understand.  I get overloaded fast.

---

### Post by yancek on 2021-01-24
>  My inference from the discussion is that "/" is the location the  kernel/OS, applications will be installed, and "/home" is where user  data will go.

"/" is the symbol used on Linux to represent the root of the entire filesystem of the operating system.  Applications/software are installed in various locations on the "/" of the filesystem.  /home is under "/" and /home is where the user personal data (documents, pictures, etc.) is stored and that is under /home/username.  If you open a terminal and enter this command you will see /home as one of the options.

```
 ls /
```

>   Can I direct both "/" and "/home" to the same partition?

Yes and that has been the default install on many Linux systems for decades.  During the install, if you use the manual option (Something Else) you can select different options such as creating a separate /home or data partition.

>  Or alternatively, can I place "/" in my EXT3 partition, and / "/home" in my NTFS partition?

You can but it won't work.  Both the "/" filesystem and the /home partition need to be on a Linux filesystem.  If you put either on a windows filesystem such as ntfs, it will not work anymore than installing windows would work on a Linux filesystem such as ext3/4..  

> (I did not setup a separate partition for my Windows data.  It's in the  MyDocuments folder in the same NTFS partition as the Windows OS.)   Is  there a good reason why I should reformat to EXT4? 

If you plan to share and enable access to this data from both windows and Linux, best leave it ntfs.  Primary reason for that is that Linux is capable of recognizing, reading and writing to an ntfs filesystem and a default windows install is not capable of either reading or writing to a Linux filesystem.  Having a separate partition for shared data is a good idea.  You should not be accessing the windows OS partition as there is too much risk for corrupting something due to either a lack of knowledge or by accident. 

>  So "/" does not identify the location of the boot loader?

Yes it does, in fact it tells you the location of everything.  It's somewhat equivalent to the C drive used on windows which is a carryover from the pre-windows days of the 1970's when computers came with 2 floppy drives and a tiny (by current standards) hard drive, hence the C as A and B were reserved for the floppies.  You can see the root of the entire system with the ls / command.

>  And I should select "sda

That installs boot code into the MBR of the drive which is required.  The code in the MBR will point to the system partition where the boot files reside and then boot the system.

Reading back through your posts I see in your first posts that you created 2 swap partitions, one you said for windows and one for Linux.  Windows doesn't use a swap partition, they have a different method so delete one of them.

Also, in your initial post you indicate you put the Ubuntu live installer on a CD.  That's a type right.  Ubuntu won't come close to fitting on a CD so you must be using a DVD or USB.

Take a look at the link below which explains the installation and shows selecting a mount point.

[https://www.itsupportwale.com/blog/manual-partition-in-ubuntu-18-04-lts-desktop/](https://www.itsupportwale.com/blog/manual-partition-in-ubuntu-18-04-lts-desktop/)

---

### Post by Hagar Delest on 2021-01-24
If your hardware is old, Xubuntu may be a better choice. Its installer looks very like the screenshots from the link posted by grahammechanical. There is no trouble with asking for a bootloader location.

"/" or "root" is indeed where the system is installed. It's the equivalent of "C:/" in Windows (when you have a single drive and single partition).
"/home" is indeed where all user data are stored. It's the equivalent of "C:/users/" in Windows. If you have several users, then each one will have it's profile in that /home. Something like /home/paul in parallel with /home/peter.
You can have /home in the root (/) or on another partition, up to you. It can be modified after installation. Better use the latest ext4 IMHO. Using NTFS for /home is NOT a godd idea. There is no point having such file system for a 100% Linux folder. The only point using NTFS is to share data with a dual boot so that you can access the data from both Windows and Ubuntu.

The mount point is just a folder that is used as the root of a partition when mounted. If you have a partition sda7, giving it a mounting point like /home/paul/documents will make your file browser look at the sda7 partition when accessing the /home/paul/documents folder. This is completely transparent for the user. In Windows, a partition has a letter like F:. There may be a way to make it act like in Linux.

For a first install, don't bother to add too much partitions. Just use a big one for / so that all fits in there. After you've been accustomed to Ubuntu, then you'll be able to tweak the system as you like.

As for the structure, I would see it differently: there is a whole system (in /, that has many folders) and user data are stored in /home. Applications can be installed in different places (mostly /opt and /usr).

---

### Post by oldfred on 2021-01-24
Some details on file structure, but you really do not need to know details to install & use Linux.
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

New users can just install in one ext4 formatted partition with /. 
That still is that standard default install. But assumes either dual boot or smaller drives from years ago.
Now we have TB sized drives & then splitting / (root) from /home is usually recommended.
Those installing servers may split other folders in / into partitions, but normal desktop does not need that. If seeing older instructions or advice from a server type install, ignore all the extra mounts of other system partitions. Just more partitions to manage & make sure one is not almost full when other is almost empty.

---

### Post by vidtek on 2021-01-24
> **Engineeringtech said:**
> GrahamMechanical-
Thank you for the link to the procedure.  My inference from the discussion is that "/" is the location the kernel/OS, applications will be installed, and "/home" is where user data will go.  Is that correct?  Can I direct both "/" and "/home" to the same partition? Or alternatively, can I place "/" in my EXT3 partition, and / "/home" in my NTFS partition?  (I did not setup a separate partition for my Windows data.  It's in the MyDocuments folder in the same NTFS partition as the Windows OS.)   Is there a good reason why I should reformat to EXT4?

Oldfred-

So "/" does not identify the location of the boot loader?  And I should select "sda", rather than a partition for it's location?  I only have the one drive with four partitions.  I believe when I partitioned the drive with Partition Commander that I made four primary partitions.


I really don't understand all this terminology.  I wish someone would define "mount point" "/" , "/home", for me, and or direct me to a diagram or video which explains the structure of Ubuntu Linux.  I know for instance that Windows places the OS in the "System" folder, and applications in their own folder.  I assume Linux has something similar.

I'm 66 and in very poor health, with failing vision.  This stuff is tough for me to understand.  I get overloaded fast.

Oldfred is the guru here.   Sometimes he doesn't quite get how hard it can be for newcomers to linux, but he is always right......

Don't think of linux in the same way you did with windows.   In linux EVERYTHING is a file, yes I literally mean everything.

/ is where you can really mess up!!!  It is the root of all things in your system, everything is derived from there.

For instance, /media is where drives and portable storage is "mounted", so the system can use it.

/home is where your personal files are located as your user  like c:\windows\users\engineeringtech  !!

Things to bear in mind-linux will prompt you for your password when using sudo-it does it for a reason-you can stuff up your system.  The windows nag screen is a pitiful affair by comparison......

dot files eg     .engineeringtech.config  are hidden files within your home directory that contain all the configurations of your desktop and environment.

don't mess with them willy nilly.

By the way, I was 70 in July and I am still struggling with many linux things after playing with it back in the late 90's, but it is wayyyy easier than windows when things go badly.....

All the best and persevere, we are all here to help you on your journey.  Tony.

---

### Post by oldfred on 2021-01-24
Again, I do not think you have to know all this to use Linux & install grub as part of Ubuntu install.
It like having to know how to tune up a car. Info if you want to now details, but not required.

Grub is the Linux boot loader.
Windows boot loader does not have a name, but also is in MBR - master boot record.
With BIOS/MBR, each drive has only one MBR.
Since Windows only wants to boot Windows, we can use grub to boot both Linux & Windows.
But grub only boots working Windows, so sometimes you may need a Windows repair/recovery flash drive or Windows installers repair mode.

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
Shows Windows has boot code in MBR, PBR & inside Windows boot partition & main partition.

Above is more for Windows, but boot process is the same.
And because MBR is tiny, grub has parts of its boot code in various places.
Its in MBR, sectors after MBR, and in the Ubuntu / partition.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

1. /etc/default/grub - the file containing GRUB 2 menu settings.
2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

Oldfred is not always right, but has been working on boot issues (his own) since 2006. And Forum boot issues both old BIOS originally and UEFI since 2009. But as with anything, still learning & trying to update notes with all the new changes. Still have old notes for old BIOS systems, but forgetting a lot of that now.

---

### Post by Engineeringtech on 2021-01-24
Thanks everyone..  I am going to print this whole thread at work, and will take a while to digest it all.  (have no printer at home)   Yes, I still work 4 days a week even with my health problems.  I will let you know how I make out in a few days.

---

### Post by Engineeringtech on 2021-02-14
I want to thank the people who tried to help me with the the dual boot.  I read the entire thread several times and I think I am too confused to proceed.   My health problems continue to get worse, and I need my computer right now.  So I can't risk damaging it.  Perhaps eventually I will buy a separate computer and load just Linux on it.

---

### Post by vidtek on 2021-02-15
> **Engineeringtech said:**
> I want to thank the people who tried to help me with the the dual boot.  I read the entire thread several times and I think I am too confused to proceed.   My health problems continue to get worse, and I need my computer right now.  So I can't risk damaging it.  Perhaps eventually I will buy a separate computer and load just Linux on it.

Engineeringtech- Good idea, let the info percolate around in your brain for a few weeks.   It is all very confusing, we have all been there before you and sympathise.   We are here to help when you are ready.

As a suggestion, go to your local secondhand/pawn shop/ebay/gumtree and grab a used laptop for your experiments in linux.  You can get a reasonable one as cheap as chips, certainly good enough to experiment with linux on.   Chances are you can get a post 2015 Samsung or HP for a couple of hundred dollars (I presume you are across the pond).  The batteries won't be up to much but you can run them on mains ok.

Just a thought, cheers Tony.

---

