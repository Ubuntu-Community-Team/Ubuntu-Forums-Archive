---
title: "How should I install GRUB2 for multiboot?"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by aajax on 2016-08-27
I'm salvaging a computer by starting with nothing installed on a new hard drive to be used for booting.  The intention is to install multiple instances of bootable systems.  One or more will be Ubuntu.  I want each system to be capable of being completely independent (i.e., self contained).  In that, I could set the partition it resides in active and it will boot.  Also, the failure of any of the systems does not affect the others.  However, because there are multiple systems I'd like to be able to select which one I want to run when booting the computer.

To do this I think I need a small partition which is only used to run GRUB2, which will normally be the active partition.  Then a completely self contained Ubuntu system is installed in another (i.e., 2nd) partition.  Likewise another completely self contained system can be installed in another, 3rd, partition.

It looks to me like I may need to start by installing a complete Ubuntu system (using LiveCD).  Let's say into Partition 2.  From there I can install grub2 into a different partition by using the grub-install script.  Let's say that Partition 1 is the target for grub-install.

Assuming that the above is a valid interpretation of how Ubuntu installation can be done, what is not clear is the minimal requirements for the partition (i.e., size, file system, etc.) that is to be the target of grub-install.  The choice of file system likely affects the choice of system to used for emergency repair or update, which means what choice of filesystems is possible?

If this approach is valid what is the best choice for partition size and file system for the grub2 partition (i.e., Partition 1)?

If this is either not valid or a bad approach what is good approach?

---

### Post by oldfred on 2016-08-27
I have multiple Ubuntu installs.
With grub2, you do not need a grub only partition.
Back with grub legacy, I did use one of those, but you totally have to manually maintain it.

With BIOS, you only have one MBR per device, so last system installed takes over control of MBR and then booting. Most Linux now use grub2.

Active partition is mostly a Windows thing. That tells the Windows boot loader where to find more boot code. But Lilo & Syslinux also use boot flag.
Grub does not use Active partition which in Linux is the boot flag.

I use 25GB for / (root) including /home, but then have a large data partition which I mount in every install. But all my installs are Ubuntu or a flavor of Ubuntu.

 And then I can boot a partition not the specific grub entry. Debian based installs have a link in / that is to most current kernel after update. So you boot link and can then boot an updated install without having to manually edit 40_custom or run sudo update grub in every install to have most current kernel in grub.cfg for os-prober from booting install to find and add to boot menu.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by grahammechanical on 2016-08-27
If you intend to install any version of Microsoft Windows, then install it first. The Linux boot loader (Grub) will detect Windows and list it in the boot menu. But the Windows boot loader only detects other versions of Windows. So, if you install Windows after Ubuntu or any Linux distribution then you will not be able to boot into Linux because it will not show up in the Windows boot menu.

Also, it makes a difference if the motherboard has a BIOS or a UEFI boot system. The advice will be different.

As a minimum Ubuntu needs two partitions. One for Ubuntu (mounted / ) and one for swap. As we can only use one OS at a time, other installs of Linux will use the same swap partition. If you intend to hibernate (suspend to disk) the swap partition will need to be a little larger than the amount of RAM as the state of the OS in memory is stored in the swap partition during hibernation.

The amount of RAM will determine the size of the swap partition. If the amount of RAM is large enough so that swap is rarely used then swap can be 1 or 2 GB. If RAM is 1 or 2 GB then you might want 2 or 3 GB swap.

Regards.

---

### Post by yancek on 2016-08-27
Choose a system you plan to keep, Ubuntu?  and install Grub2 to the MBR if you are using an MBR system.  When you install more systems, use a Manual or Expert option which should give you the option to install Grub to the partition on which you are installing the new system.  Re-boot Ubuntu and run sudo update-grub.  If you allow each new installation to install to the MBR on one of the auto-install methods, you eliminate the need to update-grub from Ubuntu but if the installation fails, your computer is bricked and you need to go through a convoluted process to reinstall Grub.

---

### Post by aajax on 2016-08-28
I understand that multiboot can be done without a dedicated boot partition.  However, I want/prefer a dedicated boot partition because this allows each system to be independent.  I want to be able to backup and restore systems (i.e., root partitions in Linux terms) using captured images (e.g., as created by partimage).  If one of the systems is also required to boot another system then there are different scenarios that must be followed depending on which system you might want to replace with one of the images.  I also realize that there is some FSTAB editing that is required when you relocate a partition (e.g., restore an image to a different partition than the one where the backup came from).  My idea, which I've done in the past with both grub and something called bootmagic, is to have a dedicated partition that handles only the booting.  In that, because it is single purpose there is no backup/restore needed for it.  If something happens to it you simple reinstall it.

My experience is limited to BIOS based computers and the one I want to salvage is also a BIOS computer.  My understanding is that the Master Boot Record (MBR) is something the BIOS needs to figure out which partition contains the boot loader.  In that the MBR is not OS specific it should be the same for either Windows or Linux.  Making a partition active has the affect of designating where the boot loader resides.  I am aware that, beginning with Windows Vista, Microsoft changed the boot mechanism where it essentially now uses a separate boot partition, which is normally also used for system restoration, and the installation process changed as a result and it has become quite unnatural to do multiboot but I have figured that out and have W7 systems running multiboot without system restore (i.e., the way I'd like to run Linux).  Microsoft even claims that this new boot loader can be used to boot Linux but I'd prefer avoiding the need to figure that out assuming that grub2 can do the job.

It looked to me like the grub-install script is used, from a running Linux system, to install grub2 into another partition.  I think that what grub2 calls chain loading is how it can find a boot loader in the same manner as the BIOS does but for a Linux system there is no need for a chain loader because grub2 is sophisticated enough to know how to find the Linux kernal and start it without a boot loader.  Therefore, in my proposed method of operation the dedicated grub2 partition is active and it displays a menu, using grub2, which allows the desired system to be selected for booting.  I would want each of those system to also have grub2 installed in a manner that it could boot that particular system.  This provides backup for failure of the dedicated grub2 partition.  In that, you make the partition active and it can be booted using the boot loader it contains (but which isn't used when operating in the multiboot mode).

So far the replies have not said that this cannot be done and I'm not persuaded that the alternative approaches are better than what I'm after.  Of course if what I'm after cannot be done then they would have to be considered better if they, at least, work.

---

### Post by oldfred on 2016-08-28
Grub2 does not like to be installed to a PBR - partition boot sector. That is the way you would have to install grub to be able to change a boot flag and boot a partition.
Grub does not use boot flag or the active partition. It searches for and finds boot files.

With Linux you have to think & work differently than with Windows.

I keep a copy of a bootable flash drive, and you can easily reinstall grub to MBR to boot whichever system you want to boot. 
       [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

But I often have a grub boot on a flash drive which I can manually edit to boot just about anything.
       
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)

---

### Post by grahammechanical on 2016-08-28
> So far the replies have not said that this cannot be done and I'm not  persuaded that the alternative approaches are better than what I'm  after.  Of course if what I'm after cannot be done then they would have  to be considered better if they, at least, work.

I am certainly not going to even try to persuade you that it is not possible. It is called freedom. Human knowledge is increased when someone looks at a matter from a different direction and is willing to do things differently.

---

### Post by yancek on 2016-08-28
> My understanding is that the Master Boot Record (MBR) is something the  BIOS needs to figure out which partition contains the boot loader.  

The BIOS doesn't need to "figure out" anything.  You set the specific drive to boot, usually a BIOS will have a 'boot' tab with an option under it to set boot priority. If you have two hard drives, drive A and drive B for example and you have drive A set to first boott priority, the BIOS will go to sector 1 on that drive which will have boot code pointing to the location/partition on which the rest of the boot files exist.  The sector is far too small to contain all the necessary boot code for any current operating system.  

> Making a partition active has the affect of designating where the boot loader resides

Simply marking a partition as active/bootable won't boot it, at least with Linux.  The active/bootable doesn't mean a thing with Linux systems and isn't used as pointed out above.

> Microsoft even claims that this new boot loader can be used to boot Linux

Earlier versions of windows, even xp, could be used to boot Linux and you can certainly do it with the newer bcdedit.  I've done this myself just to test it but it is a much more convoluted process that the Linux Grub bootloader.

> Therefore, in my proposed method of operation the dedicated grub2  partition is active and it displays a menu, using grub2, which allows  the desired system to be selected for booting.  I would want each of  those system to also have grub2 installed in a manner that it could boot  that particular system.  This provides backup for failure of the  dedicated grub2 partition

Again, the first part of the above quote, it doesn't matter if it is marked active.  Even if you have Grub installed on the other partitions, whether you are using one base system without a boot partition or you are using a boot partition, you can only have the code in the MBR pointing to one location so what you are suggesting won't work, at least not without reinstalling Grub to point to that partition.  Again, simply marking the partition as active is not going to magically boot another system on a different partition.

You can certainly boot any number of systems directly or by chainloading from Grub2, either on a root filesystem partition or on a separate boot partition.

I don't see how what you appear to want, at least as I understand it, would work.  Maybe someone else will have an idea.

---

### Post by aajax on 2016-08-29
*oldfred says, "But I often have a grub boot on a flash drive which I can manually edit to boot just about anything."*

This sounds pretty much like what I want to do but I'm willing to consume a partition on a hard drive for this purpose.  Therefore I have some questions.

1. Is the flash drive bootable?  If so, does it only run grub or is it a complete Linux system?  If only grub how was it created?
2. How big does the flash drive need to be?
3. What filesystem is used on the flash drive?

Based on feedback received I've followed up and done a little more study.  In the GRUB Manual under **3.4 BIOS Installation** it says "*The partition table format traditionally used on PC BIOS platforms is called the Master Boot Record (MBR) format; this is the format that allows up to four primary partitions and additional logical partitions. With this partition table format, there are two ways to install GRUB: it can be embedded in the area between the MBR and the first partition (called by various names, such as the "boot track", "MBR gap", or "embedding area", and which is usually at least 31 KiB), or the core image can be installed in a file system and a list of the blocks that make it up can be stored in the first sector of that partition.*"

Based on above it sounds like what I want is the second choice whereas what appears to be recommended and what most of the replies to this post reference is the first choice.  However, in my case I don't want anything else in the subject file system and based on other research it looks like many different file system can be used.  I would think that the software, possibly booted from an emergency repair disk of some kind, that might need to be used to make a repair would influence the choice of file system.

Let me try to describe a hypothetical scenario to see if it helps explain my objective.

1.  I want to run multiple different Linux systems on the same computer.  These system are used for testing and experimentation.
2.  Lets say I have 2 different systems one in Partition A which is used for booting the other Partition B.
3.  Each partition is used for experimenting with software and partimage is used to make backups of configurations that are worth saving.
4.  An experiment on Partition A leads to undesirable results that may include the system becoming unusable.
5.  Partition A needs to be restored and the image I would like to restore was made from Partition B.
6.  An image made from Partition B is restored to Partition A but Partition B was never used for booting.

Note:  In the above scenario it is necessary to edit some configuration files in the restored version of Partition A before it will load and work but the restoration does not mess up the grub2 needed for booting if it were located elsewhere.

Where does that leave me when it comes to grub2?

---

### Post by yancek on 2016-08-29
Given you 6 step scenario outlined above, if your Partition A is corrupted and you want to boot Partition B, you could chroot into Partition B from a Live CD/flash drive and install Grub to the MBR rather than moving/restoring it to partition A.  Then you could format Partition A and install some other system.

You could install a minimal system, such as Lubuntu if you want an Ubuntu derivative which should be less than a 4GB partition.  Have Grub in the MBR pointing to this partition to boot and don't use/change anything on it.  After installing another OS to another partition and installing it's Grub to it's partition, reboot Lubuntu and run sudo update-grub which should create a menuentry for the new system.  This would seem to be the simplest solution unless you have a very tiny hard drive.

Another option is to use a flash drive and create a boot directory on it and from a working system with Grub2, install Grub to it with a command similar to the one below.  You would have to determine the UUID for the flash which should show in the /media/user directory when you plug it in.  Change the entry below for user to what you actually have on your computer and also change the UUID to what its is on your system.  You would then need to manually create a grub.cfg file.  You can use a current grub.cfg or find a simple template online to use and then just put in a chainloader entry for each partition and when you install the new OS, make sure you install Grub to the partition on which you are installing the OS.  The command below assumes the flash drive is /dev/sdc so make sure you get the correct drive or you will overwrite the Grub code on one of your other drives.

> sudo grub-install --force --no-floppy --boot-directory=/media/user/USB20FD/boot /dev/sdc
  

> menuentry 'CHAINLOAD TEST' {
insmod ext2
set root=(hd0,1)
chainloader +1
}

If the systems you are installing are all Linux, you can put any number of entries in the grub.cfg using this type entry changing only the set root line to reflect the correct partition.

---

### Post by oldfred on 2016-08-29
But you still have to reinstall grub2 to fix the change in UUIDs. Reinstall of grub is a lot easier than all the edits you must do. Also better to use Boot-Repair and its full uninstall/reinstall of grub2 as then you reset some other files that are used by grub on major updates where to reinstall.
And you have to edit fstab.

I find it just easier to reinstall Linux. It is not like Windows where you just about have to have an image. I can reinstall Ubuntu in 10 minutes if I already have ISO in another partition on another drive or flash drive and already have a / (root) partition to install into. Download and partitioning are two of the longer processes. I do not think you can copy image2 back to image1 partition and edit fstab & grub in less time. And a reinstall is like a major houseclean as old log files & other cruft then is not copied. I do backup /home and have all data on a separate /mnt/data partition that I use in every install.

I only use gpt partitioning and highly recommend it. But if you also want to boot Windows, then system must be UEFI as Windows only boots from gpt with UEFI and only boots with BIOS from MBR. Ubuntu can boot from gpt with either UEFI & BIOS. 

Even my larger flash drives are now gpt. I started converting all new drives to gpt with my 10.10 BIOS system. About when Windows 8 came out I knew evenually I would get a newer system with UEFI and started including both the bios_grub partition for BIOS boot and the ESP - efi system partition for UEFI boot, even though only normally using one or the other.

You can just install grub into any device if you have a working copy of Ubuntu with grub. Command is different if UEFI or BIOS. Or if a larger flash drive you can do a full install and then that will have grub & its os-prober to find other installs and automatically add it to your menu. But I have so many installs I turn off os-prober and add my own entries to 40_custom. See post #2 for details in link.

This was the command I used to install just grub to a smaller flash drive. MC for MicroCenter and 4GB is size, so that became label. Best if partition is labeled, otherwise automounts use UUIDs which are long.
 Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

I am sure I partitioned in advance as grub will not install to a gpt partitioned drive without either the bios_grub or ESP.

 Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde 


All my newer flash drive systems are full installs with also a data partition with several install ISO or repair ISO.

See this user's comments for the easy way.
[https://ubuntuforums.org/showthread.php?t=2335087&p=13537805#post13537805](https://ubuntuforums.org/showthread.php?t=2335087&p=13537805#post13537805)
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by aajax on 2016-08-31
My hypothetical scenario was intending to convey the idea of using system/partition images as a way to capture the state of systems that you might like to later use as the starting point for a new system.  Therefore the image for Partition B that I want to restore to the location now used for Partition A is not the same as the system currently occupying Partition B.  The idea is that you accumulate various good images of systems that achieve an intended objective.  These images are on the shelf ready to be restored but possibly not into the same partition they occupied when the image was made.

I recognize that re-installation of Linux/Ubuntu is a simple task.  But the real work in building a system for a particular purpose has very little to do with getting Ubuntu to work.  It rather has to do with installing and mostly customizing the setup a various packages that provide the capabilities you are after.

What yancek describes regarding Lubuntu is the idea I'm after.  My recollection is that when I used grub, as opposed to grub2, I was able to install it into a very small partition (i.e., a few megabytes as opposed to gigabytes).  It could be manipulated/altered/configured by mounting it to any running system to include SystemRescueCD.  I suppose what I thought I could make is something like a Super Grub2 Disk (less than CD size) but put it into a real partition.

It looks like SystemRescueCD still fits on a CD (i.e., less than a GB) but they seem to be still using the original grub.

One of the reasons for being stingy with disk space is that I'm wanting to use a solid state drive (SSD).  However, my research into SSD suggests that you want to utilize it for the kind of data that is read very often but written very little.  Therefore, I expect to also need at least one conventional hard drive which in my case is also readily available because the drive on the system I'm salvaging works fine.  The hard drive would have a shared swap partition along with a partition for application data (i.e., a Home directory which might be shared).  I'm also thinking about putting temporary storage and log file directories on the hard drive.  This leads to the idea of putting the primary boot manager on the conventional hard drive and using it to boot various system partitions on the SSD (a modest 250GB SSD would accommodate 3 partitions that are around 80GB).  The capability of grub2 to be a quality boot manager ought to work well.  Shouldn't it?  In which case, a 4GB partition that has enough capability to manage the boot manager might be reasonable.

How does that sound?

With respect to UUIDs it is my understanding that they correspond to actual partitions and therefore would become very static by using a separate, very static, partition exclusively as a boot manager.  The idea that this static partition would also be capable enough to update /etc/fstab after an image restore would seem desirable.

---

### Post by yancek on 2016-08-31
> The capability of grub2 to be a quality boot manager ought to work well.   Shouldn't it?  In which case, a 4GB partition that has enough  capability to manage the boot manager might be reasonable.

Not sure what you mean by that?  You can install and re-install various operating systems and get new entries in the grub.cfg file by running:  sudo update-grub.  You need a system installed to do that because the update-grub shell script is in the /usr/sbin directory.  If you open that file in a text editor you will see that it is a one line script pointing to the grub-mkconfig shell script which is also in the same location.  I suppose you could put it in your separate boot partition but just a brief look at the content would indicate that it needs a full system.

If you have a separate boot partition with no OS connected to it you will have to do everything manually.

---

### Post by aajax on 2016-09-21
In the way of closing this out I want to especially thank yancek and oldfred for their help and advice.

I ended up concluding that it was necessary to install a separate Linux system to act as the boot manager per prior discussion.  In order to limit that amount of disk space consumed I opted to go with Debian rather than Ubuntu.  I installed a minimal size Debian system into a small dedicated primary partition.  I used the installation method that puts Grub into the boot sector rather than the MBR.  Given that this system would only be used for booting other systems it looked to me like there was little or no downside to the risks mentioned about electing this approach.  To my way of seeing things leaving the MBR untouched is desirable.  I created a 2GB partition for this purpose but it now looks like 1GB would have been plenty big.

Since then I similarly installed a full version of Ubuntu Desktop on a second SSD drive.  This was also done by electing to place Grub on the same partition (i.e., boot sector rather than MBR).  Of course this instance of Grub is not used since booting is done using the Debian system.

Running update-grub on the Debian boot manager discovered the new version and everything works as desired.

The Debian system serves as something that can also be used for rescue purposes which is more than what I expected to get from a partition dedicated to booting.

Thanks again!

---

