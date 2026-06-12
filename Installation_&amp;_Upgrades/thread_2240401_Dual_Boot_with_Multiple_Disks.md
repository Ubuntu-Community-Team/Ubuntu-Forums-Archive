---
title: "Dual Boot with Multiple Disks"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by chrisman81 on 2014-08-19
I'm getting ready to set up brand new installation that will include Ubuntu (14.04.1 LTS) and Windows 7.  I have two SSDs -- 128GB Samsung and 256GB Intel.  Which of the following would be the best way to set this up if I plan to use both environments:
[LIST=1]
[*]Install both on the same disk and use the second one for file
[*]Install Ubuntu to one disk and Windows 7 to the other, with a share space set aside on the larger disk
[/LIST]


Also, it's been a while since I installed any version of Linux.  Am I better off specifying my mounts (/, /home, swap, etc...) and sizing them a certain way or letting Ubuntu handle all that for me?  If I'm better off specifying myself, what are the suggested sizes?

For what it's worth, I'll be installing this on a system that has the following components:[INDENT]- GIGABYTE GA-Z87X-UD5H
- Intel Core i7-4771 3.5GHz
- 16GB Corsair DDR3 1600
- EVGAGeForce GT 640 2GB DDR3[/INDENT]

Any help/insight is greatly appreciated.

Thanks in advance.

---

### Post by didier5 on 2014-08-19
Past weeks, I've just done that on a much older hardware. 2 disks of 80 Go.
My installation is a professional environnement; safety is primordial.
( XP on one disk and 12.04 on the other one )
One disk breaks done and I can still work and repair the other one.

XP disk - 19 Go for the OS - then the data.
Ubuntu + dual boot disk - 15 Go for the OS - 1 Go Swap - then the data
( My poor 1Go RAM can be used up to 75% and the Swap 30% - that's
a maximum when I play with youtube - currently Swap is at 0% )

In my case I mirror the data of the 2 disks. Then a backup with a NAS.

Practise prevails, intalling everything it crashed many times and I was happy with that choice.

---

### Post by fantab on 2014-08-19
Boot with Ubuntu DVD/USB and 'Try Ubuntu [without Installing]". Open Terminal [ctrl+alt+T], run the following commands and copy/paste the output here:
```
sudo parted -l
sudo fdisk -l
```

I would keep my Windows and Ubuntu on separate SSDs.
Preferably, Windows on the first SSD or /dev/sda and Ubuntu on the second SSD or /dev/sdb.
For Ubuntu I would Partition as follows: (this is only a suggestion)
1. 30Gb Primary Ext4 / (ubuntu system files)
2. 2-4Gb Primary LinuxSWAP
3. All the remaining GB Primary Ext4 /home...

I'd suggest you specify the partitions and mountpoints yourself by using the "Something Else" option during installation.
I don't think the Ubuntu installer will create /home for you. It just makes '/' and 'swap'. Having a separate /home is a good idea.

Your Graphics card may cause booting issue... it will be helpful if you learn about '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option.

---

### Post by didier5 on 2014-08-19
I don't have the experience of [fantab] and beforehand I should have subscribed here.

Eventually, I arrived to all those things ... after a lot of hours.
 
Ok, "Try Ubuntu" may be easier than to play with another Gparted USB boot. 
By plugging and unplugging USB sticks, I even destroyed a USB stick. 
 
I also passed by "Something else" but I missed to create a separe /home. 
That will be for next time.

---

### Post by oldfred on 2014-08-19
As with both didier5 and fantab:
One more vote for Windows on one SSD and Ubuntu on the other. Then if an issue with one drive you should be able to boot the other drive.

Since you have a Z87 board you can install in UEFI or BIOS boot modes.
Windows only boots from gpt partitioned drives with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
But Ubuntu can boot from a gpt partitioned drive with either BIOS or UEFI, so if concerned you can change or experiment. 
Or I recommend gpt partitioning on at least the Ubuntu drive. Include both an efi partition at beginning of drive for UEFI boot whether using UEFI now or not. And a bios_grub partition if booting in BIOS mode or perhaps if wanting to change back to BIOS boot mode.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

As with fantab's suggestions, I suggest smaller system partitions and larger data or /home partition(s) for both Windows & Ubuntu. But Windows typically needs a larger system partition as it likes to keep more info in its system.

If thinking about UEFI, many useful links in the link in my signature.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Not if it applies to your Gigabyte board or not. Bit IOMMU setting often required.
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

 Gigabyte's ASPM Motherboard Fix: Use Windows
[http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg](http://www.phoronix.com/scan.php?page=news_item&px=MTAwMjg)
Gigabyte GA-Z87X-UD3H, Ubuntu 13.10, and Intermittent External USB Drive Failure 
[http://ubuntuforums.org/showthread.php?t=2194155](http://ubuntuforums.org/showthread.php?t=2194155)

When installing be sure to install boot loaders to same drive as install. Many suggest disconnecting other drive to make sure all of system is on one drive. With Windows make sure UEFI/BIOS has that drive set as default during install and with Ubuntu be sure to choose install of grub to correct drive.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by chrisman81 on 2014-08-20
So, I got windows 7 installed. That's on sdb. I installed Ubuntu on sda as follows:
300MB efi (that automatically reserved another 1MB in front of it)
25GB /
2GB swap
remaining /home

Ubuntu is not recognizing windows. How can I be sure this formatted as gpt and that the boot loader sees windows and allows me to boot to it?

Thanks again.

---

### Post by oldfred on 2014-08-20
Try this:
sudo update-grub

If Windows is in UEFI boot mode it should find it. And it may find it even if not in UEFI boot mode but then not work. Make sure Windows is not hibernated nor needing chkdsk.

And to see all the details of the installs run the BootInfo report and post link from Boot-Repair. Do not run auto fix with Boot-Repair when you have mulitple drives as it just installs grub everywhere. But advanced mode would work if you need it.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by chrisman81 on 2014-08-20
Looks like Windows is indeed in UEFI boot mode, but grub isn't finding it.

I took a peek at the advanced options, and under "OS to boot by default" in the "GRUB location" tab, my options are sda2 (which is Ubuntu) and Windows (via sda2 menu).  So, it looks like it knows Windows is there...

Here's the link to the BootInfo report:  [http://paste.ubuntu.com/8102415/](http://paste.ubuntu.com/8102415/)

Thanks for your help.

---

### Post by chrisman81 on 2014-08-20
I'm looking at the BootInfo report now, and it says that the sdb has msdos partition table.  When I go into Windows, though, it says UEFI...

---

### Post by oldfred on 2014-08-20
Your install of Ubuntu on sda is UEFI boot with gpt partitioning.
And your install of Windows on sdb is BIOS boot with MBR partitioning.
Windows and Ubuntu boot from MBR with BIOS.
Windows and Ubuntu boot from gpt partitioned drives with UEFI.
Ubuntu will also boot from gpt partitioned drives with BIOS, but Windows will not.

You can dual boot only from UEFI/BIOS so you start system in correct boot mode.

You can convert Ubuntu to BIOS boot mode if desired with Advanced Options in Boot-Repair. But you have to create a tiny 1 or 2MB bios_grub partition before conversion so grub can install in BIOS mode correctly to a gpt partitioned drive. It has no format and you set flag with gparted when you create partition. Bios_grub partition can be anywhere on drive.

Where in Windows are you seeing UEFI?
Or are you just seeing in the UEFI menu the CSM/Legacy/BIOS boot option for Windows?
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by chrisman81 on 2014-08-26
I had been seeing the Windows partition identified as UEFI by going to Control Panel --> Administrative Tools --> Computer Management --> Disk Management.

I ended up doing a fresh install of both Windows and Linux (since the systems hadn't been configured much).  That seemed to work.  Then, as I was patching Windows, it shut down unexpectedly during one of the updates, and that screwed up my whole Windows partition.  I reinstalled that, and now I'm back to where I was before -- Linux will boot and Windows won't.  I don't know if it makes a difference, but when I reinstalled Windows, I disconnected the drive with Ubuntu on it and then set the Windows drive up exactly how it was.

I think I'm going to do another fresh install of both Windows and Ubuntu and see how I make out with that. 

Thanks for the help with this issue.

---

### Post by fantab on 2014-08-26
First of all setup your second partition as GPT. It is a very good idea to boot both OS in EFI mode.
Install Windows first and preferably on /dev/sda or your first SSD/HDD.. Update/Upgrade it and configure it. 
If you install Windows in UEFI then you will notice an FAT32 ESP [Efi system partition].

Create a similar partition on /dev/sdb or the SSD where you'd install Ubuntu. The partition size is about 250MB, formatted with FAT32 and has a 'boot' flag.
When installing Ubuntu make sure you direct your Grub install to /dev/sdb's ESP. (We are trying to keep Windows boot on its own ssd and Ubuntu on its own).

After successfully installing Ubuntu you have to go back to the UEFI menu and make Ubuntu SSD as your first boot... by default your first ssd with windows will boot first...

---

