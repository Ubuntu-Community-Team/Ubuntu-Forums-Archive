---
title: "GRUB partition"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by warfacegod on 2010-04-26
Would I be correct in assuming that if I create a partition and mark it as /boot that GRUB2 will install there instead of the partition I mark as /?

Thanks in advance.

---

### Post by tachuela on 2010-04-26
Your kernel would be in boot, but Grub installs in the first 512 bytes of the HH

---

### Post by warfacegod on 2010-04-26
So I can't create a separate GRUB partition?

---

### Post by srs5694 on 2010-04-26
Your question is ambiguous. GRUB actually "installs" in quite a few different locations, depending on your meaning of the word "installs:"


[list]
[*]The GRUB package (such as grub-pc on Ubuntu 9.10) installs ordinary files in /usr/sbin, /usr/share/doc, and elsehwere. On my system, none of these files reside in /boot, but some GRUB files do get copied there (presumably by the grub-install script or something similar).
[*]GRUB's configuration files reside in /boot/grub, and so can be said to be "installed" there. If you use a separate /boot partition, these files will necessarily reside on that separate partition.
[*]In operation, GRUB relies on code that can be stored in any number of locations, including the Master Boot Record (MBR), unallocated space following the MBR (for MBR-partitioned disks), a dedicated BIOS Boot Partition (for GPT-partitioned disks), the boot sector of a Linux partition, and files in /boot/grub. Only the last of those locations is absolutely required for all configurations; the lowest-level GRUB code can reside in *either* the MBR or a Linux partition's boot sector, and different versions of GRUB and configuration options can influence where ancillary code resides. You can specify where the GRUB low-level code goes by passing grub-install an appropriate option. For instance, "grub-install /dev/sda" puts that low-level code in the MBR, whereas "grub-install /dev/sda1" puts it in the boot sector of the /dev/sda1 partition. This latter option often doesn't work for GRUB 2, though.
[/list]


I suspect you mean the last of these points when you ask about where GRUB is installed, and if so I'm afraid there's no simple answer to your question. It really does depend on the exact options used to install GRUB, as well as your system capabilities and configuration (BIOS vs. EFI, MBR vs. GPT, MBR vs. partition boot sector storage for GRUB's stage 1, etc.). You'll have to provide more details about your configuration and be more specific about why you're asking the question in order to get a more precise and accurate answer.

---

### Post by Herman on 2010-04-26
I agree with srs5694 in the post above. GRUB does have files in all of those locations, and to say we're installing GRUB somewhere is a huge oversimplification which can result in confusion for anyone who's trying to learn about GRUB and Linux operating systems.
It's unfortunate that we haven't yet coined better terms so that we can communicate more accurately regarding boot loaders and where parts of them are to be located.
> Would I be correct in assuming that if I create a partition and mark it as /boot that GRUB2 will install there instead of the partition I mark as /?I am guessing your question is in reference to the Ubuntu installer. I am also guessing you mean to ask if you create a partition and designate it as /boot during the partitioning phase of your Ubuntu installation, will the Ubuntu installer create a 'Separate /boot Partition' for you?
The answer to that is 'Yes', the Ubuntu installer will install the GRUB files which normally reside in the /boot directory in your new /boot partition, including the Linux kernel, initrd.img and other associated files.

You will be asked where you want GRUB installed later in the installation and this time the question the installer is asking you refers the GRUB files that normally go in the MBR and first track of the hard disk. Here you may specify which hard disk if your computer has more than one hard disk. There are other options as well.

A 'Separate /boot Partition' is useful if you have an older computer with a BIOS hard drive size limit, because you can restrict the physical location of the Linux kernel to the area inside the BIOS hard drive limit.
It's also necessary for some kinds of special installations such as when you want to make a LUKS encrypted /.

A 'Separate /boot Partition' is not so useful if you plan to multi boot, because it's not easy to get more than one Linux installation to share the same 'Separate /boot Partition, you will need to create another one for every operating system, which can chew into your limit on the number of allowed partitions after a while, even if you do use logical partitions. 

Many Ubuntu users like to multi boot, because of the way the Ubuntu release cycle has been laid out. We have an LTS release, like the Ubuntu Hardy Heron and the upcoming Lucid Lynx, which are meant to be our stable releases. As well, we have our six-monthly releases featuring the latest and greatest bleeding edge software. Not too many of us can resist the temptation to try out the latest in software offerings. Therefore, to have the best of both worlds, it's best to have at least two Ubuntu installations, as well as possibly other operating systems which may happen to have existed beforehand which haven't been disposed of yet. 
Add to that testing version of Ubuntu that's under development and we're starting to have quite a few partitions even if we have single / partition installations. 

Even some new (modern) computers can use a 'Separate /boot partition. I helped a friend fairly recently who has an ASUS EeePC with a failed SSD drive. He had installed Ubuntu in a 1TB external 5 1/4"  HDD instead, but it wouldn't boot. We booted from Ubuntu in a USB flash memory stick and copied files from his /boot directory into another USB flash memory stick and made that into a 'Separate /boot drive'. His ASUS EeePC's BIOS was able to map the smaller drive no problems and that solved the problem.

---

### Post by warfacegod on 2010-04-26
A rather simplified explanation is this. I dual boot. I use 9.10 as my main OS in sda1. sda2 is my /home for sda1. sda3 is what I refer to as my experiment drive. It's where I install various Linux OS's and ...well try out and break them. Not all the time but often enough to be an annoyance, when I do a new install, GRUB gets messed up or gets installed over with a different version. Either GRUB legacy or a beta of GRUB2. So what I'm considering doing is making another partition and have GRUB2 reside there so that I can stop installing it altogether.

---

### Post by srs5694 on 2010-04-27
> **Herman said:**
> A 'Separate /boot Partition' is not so useful if you plan to multi boot, because it's not easy to get more than one Linux installation to share the same 'Separate /boot Partition, you will need to create another one for every operating system, which can chew into your limit on the number of allowed partitions after a while, even if you do use logical partitions.

The number of logical partitions is limited by the size of the disk, at least in terms of the MBR/EBR data structures. You can certainly create /boot partitions as logical partitions, so this isn't really an issue. Also, if you use GPT rather than MBR partitions, the primary/extended/logical distinction goes away, and you can have up to 128 partitions by default, or more than that if you really need them.

[quote=warefacegod]I dual boot. I use 9.10 as my main OS in sda1. sda2 is my /home for  sda1. sda3 is what I refer to as my experiment drive. It's where I  install various Linux OS's and ...well try out and break them. Not all  the time but often enough to be an annoyance, when I do a new install,  GRUB gets messed up or gets installed over with a different version.  Either GRUB legacy or a beta of GRUB2. So what I'm considering doing is  making another partition and have GRUB2 reside there so that I can stop  installing it altogether.[/quote]

Fundamentally, the problem is that the BIOS boot system requires that you have just one primary boot loader -- whatever is in the MBR becomes that boot loader. I expect that what's happening to you is that GRUB's MBR component is being overwritten every time you do a fresh install, so you end up getting a new GRUB menu each time you install a new OS. There are several ways to deal with this, such as:


[list]
[*]Live with it -- Keep records of what GRUB installations you've got and then reconfigure the latest version of GRUB after every new OS installation.
[*]Repair it -- After each new installation, boot the OS with your preferred GRUB setup by using an emergency disc and then run grub-install to restore the original GRUB setup. You'll then need to add your new OS to that preferred GRUB configuration.
[*]Restore it -- If you keep a backup of the first 446 bytes of /dev/sda, you can restore it to restore the boot loader that had been there after each OS installation. As with the previous option, you'll have to manually add a new entry to your preferred boot loader after each OS installation.
[*]Using a simple MBR boot loader -- You can put a simple Microsoft-style boot loader in the MBR (see [this Sourceforge project](http://sourceforge.net/projects/ms-sys-free/) for a way to install several different MS-style boot loaders) and install each Linux installation's GRUB to a different primary partition. The MBR boot loader will then boot whatever primary partition is marked as active, so you can change which boot loader you use with fdisk. Note that this will require you to use primary partitions for Linux root (/) or /boot partitions, and you'll have to tell the Linux installers to put GRUB in the relevant partition's boot sector, rather than in the MBR.
[*]Use a third-party boot loader -- Some boot loaders can redirect the boot process to the boot sector of any arbitrary partition. If you install such a boot loader, you can use it much like a standard MS boot loader, but you can select which partition (and therefore which version of GRUB) to use on each boot. In fact, you can configure GRUB like this, if you like. Again, you'll need to be careful not to overwrite this MBR-resident boot loader when you install a new version of Linux.
[/list]

---

### Post by warfacegod on 2010-04-27
I vote for option 01. It seems to be the least hassle. I've sort of gotten used to reinstalling GRUB2. I was just hoping to get a simple permanent fix, alas. Thanks guys.

---

### Post by Herman on 2010-04-27
> Live with it -- Keep records of what GRUB installations you've got and  then reconfigure the latest version of GRUB after every new OS  installation.Option 01. is easy with GRUB2 because all you need to do is re-install GRUB2 to MBR and run 'sudo update-grub' or 'sudo grub-mkconfig -o /boot/grub/grub.cfg'. 

In the olden times with Legacy GRUB, we used to create a '[Dedicated GRUB Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")', for the purposes of having an 'operating system independant' boot loader for multi booting, or there is [GAG Boot Manager]("http://gag.sourceforge.net/"), which is also very good.

Now because GRUB2 is able to detect other operating systems and automatically add them to the boot menu, it's easier to just re-install GRUB2 and give the command, as opposed to manually editing menu.lst, as we used to do with Legacy GRUB.

I started a thread here, [How to Multi Boot the Easy Way With GRUB2]("http://ubuntuforums.org/showthread.php?t=1462617") , which you might be interested in. :)

---

### Post by warfacegod on 2010-04-27
Thanks for the multiboot link, I've saved it to my bookmarks.

---

### Post by vikrang on 2010-10-28
I just have the same doubt as Warface...Suppose I create a dedicated boot partition , the distro also creates another boot partition in "/"..So now I want to modify the GRUB and say, add another distro,,,,I mount the dedicated partition in /mnt ....My basic doubt is which one is used by MBR?!! The files in both the directories are the same..Which one should I modify??! Should I delete the extra boot directory in "/" partition? Also how do you tell the MBR to look for GRUB in the dedicated partition at boot?...
 
In GRUB 1 tutorial , it is mentioned that except Kernel images all the boot files will be in the dedicated partition..
 
Wheras the same analogy doesnt apply to GRUB2 as the setup is very different
 
 
Also suppose I am in the process of installing another Linux distro , in the installation screens I choose to create only the "/" directory opting to share the swap and boot with the original Linux install
 
 
I take care and opt to choose to install the new GRUB in root partition of the new distro without touching MBR...
 
What are the files to be copied in the dedicated partition? since the other distro also uses the same name "/boot" how will I distinguish which boot directory is for which distro?
 
I know this is avery dumb QN:P But thinking too much has led me to this confusion
 
What is to be done??:confused:

---

### Post by Herman on 2010-10-28
:)  I'm confused too, I'm not sure what you mean by a 'dedicated boot partition'.
Back in the days of 'Legacy GRUB', we had two different kinds of partitions that had GRUB in them, one was called a 'Separate /boot Partition', and the other kind was called a 'Dedicated GRUB Partition'.
At least that's how I used the terms myself, nobody appointed me as the head language cop of the universe or anything, LOL :).

A '**Separate /boot**' partition is the kind that most people just call a /boot partition and it normally gets created during the installation of the operating system and contains the Linux kernel and initrd.img as well as a grub directory, which houses most of the GRUB files that get used for booting. A 'Separate /boot' partition is listed in an operating system's /etc/fstab file as the /boot partition for that operating system, and will be mounted as /boot, and receive updated kernels and initrd.img files and other files automatically.

The other kind of GRUB partition was called, a '**Dedicated GRUB Partition**', which as far as I know was a term coined by a Mr. Steve Litt, the author of [Making a Dedicated Grub Partition]("http://www.troubleshooters.com/linux/grub/grubpartition.htm").The 'Dedicated GRUB' partition only contains GRUB files and is 'operating system independant, and does not contain any Linux kernels, or at least not necessarily.

I suppose it would be okay just to call one a /boot partition and the other a 'grub' partition, but I like to have the words 'Separate' or 'Dedicated' added to further emphasize the fact that I'm talking about two different things.

**Sharing a 'Separate /boot**' (not such a good idea)
It was possible to install another operating system and share the same 'Separate /boot' partition, but, ... BUT! ... the second operating system will over write any of the first operating system's files in the /boot partition which have the same filename and file path. That can cause a few problems. The menu.lst file was the worst affected. Most of the other files were either not affected, because they had a different file name, or they were interchangeable anyway.
The workaround was to rename one of the menu.lst files to some other file name, such as 'menu.lst_b' or 'menu.lst_II' or something, then edit the update-grub script to look for a 'menu.lst_b' or 'menu.lst_II' file or whatever you renamed it.
Here's a link I wrote that explains all that in a much more verbose manner that I don't care to repeat again here, [How to make a separate /boot partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition").
SO, having two or more operating systems sharing the same 'Separate /boot' partition is not particularly recommendable, but if it gets done by accident or out of inexperience, at least with Legacy GRUB it could be worked around. Please refrain from mounting another operating system's /boot during the installation of subsequent operating systems and you'll save yourself a lot of headaches. It's much better, if you must have a 'Separate /boot', to have one for each operating system if you're installing more than one Linux system.

**Sharing a 'Dedicated GRUB Partition'**
A  'Dedicated GRUB Partition' was made to be shared, and was a popular idea back in the 'Legacy GRUB' days, especially for those of us who like to multi-boot. 
 The 'Dedicated GRUB' would always boot from the MBR by default, because it had its stage1 in MBR and stage1_5 in the first track, (the next several sectors after the MBR).
Operating systems could have their boot loaders installed in the first sector of the partition, (the stage1 parts of the boot loaders I mean), and be chainloaded by the GRUB in the 'Dedicated GRUB Partition'. Since the 'Dedicated GRUB partition only contained GRUB, and was 'operating system independant', it was possible to delete operating systems and install different ones in their place without the need to re-install GRUB to MBR every time and it only required a little manual editing of the 'Dedicated GRUB's' menu.lst file each time a new operating system was installed to get all operating systems to boot how the operator wanted.

**Now that we have GRUB2, things are different.**
Multi booting with GRUB2 is a lot easier for the user, it detects other operating systems and adds them to the boot menu automatically, (or whenever we run grub-mkconfig).
I don't think a 'Dedicated GRUB Partition' is really necessary with GRUB2, but it's okay to make one of you so desire. It can be fun to play with.
GRUB2 doesn't like being installed in a partition boot sector, because the core.img is now much larger and more important than Legacy GRUB's old stage1_5 and if I understand correctly it has taken over some of the jobs stage2 used to do. Of course neither stage1_5 or core.img can be installed after a partition boot sector, as they would overwrite the file system metadata blocks. Therefore, the copy of core.img that remains in the file system will need to be used, and it would need to be found by block addressing from the partition boot sector, and that would make your GRUB2 less reliable in certain situations.
Therefore, the disadvantages probably outweigh the advantages of using a 'Dedicated GRUB Partition', these days with GRUB2.
The best way to do things now is to just install each new OS's GRUB (boot.img) to MBR and let the core.img go into the first track and let GRUB2 write it's new grub.cfg to include all detected operating systems.
If an operating system doesn't get detected, try running a file system check in it and run grub-mkconfig again. There's no more need for manually editing boot loader configuration files. :)

---

### Post by vikrang on 2010-10-28
Thanks Mate ! It was nice to receive a reply from a PRO !! No wonder , you are the "King of Grub"

---

