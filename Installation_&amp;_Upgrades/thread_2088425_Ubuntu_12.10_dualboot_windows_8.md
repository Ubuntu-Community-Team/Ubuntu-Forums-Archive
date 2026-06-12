---
title: "Ubuntu 12.10 dualboot windows 8"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by granul on 2012-11-26
Hi!

I want to install Ubuntu 12.10 dual boot with windows 8 on a laptop, I already created a partition,  I would to know,  before I install, is there anything to do to make sure that grub will install correctly?

thank you

---

### Post by oldfred on 2012-11-26
You need to use the Ubuntu 12.10 64 bit version and be sure to boot it in UEFI mode not BIOS/legacy/AHCI mode.

If you created partition with Windows it will not work for Ubuntu. You have to have Linux partitions for Linux.

Is this a pre-installed Windows 8 with secure boot or your own install?

       [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
    
       Some general info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

    [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Secure boot turned off.
       Acer V5-571P-6815
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

    Some have reported system works with secure boot on or off both during install or after. Others have had issues as it seems to depend on Vendors UEFI implementation.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

---

### Post by granul on 2012-11-26
Thank you
It is an up date from windows 7 to 8, and no problem booting live usb

---

### Post by oldfred on 2012-11-26
So is it BIOS/MBR or UEFI/gpt?

If BIOS then you have to use the available partition as an extended partition and install Ubuntu using logical partitions. Windows requires primary partitions, but Linux works fine from logical partitions.

       MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by granul on 2012-11-26
> **oldfred said:**
> So is it BIOS/MBR or UEFI/gpt?

If BIOS then you have to use the available partition as an extended partition and install Ubuntu using logical partitions. Windows requires primary partitions, but Linux works fine from logical partitions.

       MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

How do I know if it's UEFI?

---

### Post by oldfred on 2012-11-26
If first partition is efi and you have gpt partitioning, then it is UEFI. Windows only boots from gpt partitioning with UEFI.

If you have MBR(msdos) or gpt this will tell your.

       sudo parted /dev/sda unit s print

---

### Post by granul on 2012-11-26
Here is what I have

Number  Start      End          Size         Type     File system  Flags
 1      2048s      35653631s    35651584s    primary  ntfs         diag
 2      35653632s  35858431s    204800s      primary  ntfs         boot
 3      35858432s  1157945343s  1122086912s  primary  ntfs

---

### Post by oldfred on 2012-11-26
That is MBR(msdos) and you only have 3 primary partitions used. So you can shrink Windows using Windows MMC and then install Ubuntu into the unallocated if you just want auto install and default partitions of / (root) and swap. Or you can manually partition with additional partitions in the extended partition.

A shared NTFS partition is highly recommended as Windows does not like writes into its system and now Windows 8 is always at least partially hibernated.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by granul on 2012-11-27
I installed Ubuntu 12.10, the installation went ok but it boot only to windows 8, no grub

---

### Post by granul on 2012-11-27
> **granul said:**
> I installed Ubuntu 12.10, the installation went ok but it boot only to windows 8, no grub

I finaly fix, I use boot repair on a live session, so now I can dual boot ubuntu and windows 8

---

### Post by YannBuntu on 2012-11-28
> **granul said:**
> I finaly fix, I use boot repair on a live session, so now I can dual boot ubuntu and windows 8

Good job :)
For our information, please could you indicate the URL that was provided by Boot-Repair?

---

### Post by granul on 2012-11-28
Boot repair found here

[http://forum.ubuntu-fr.org/viewtopic.php?pid=4725991](http://forum.ubuntu-fr.org/viewtopic.php?pid=4725991)

---

### Post by oldfred on 2012-11-28
Yann wanted your pastebin link that running the BootInfo report gives you. So we can confirm your final working configuration.

You posted the link to the French version of Boot-Repair.

---

### Post by granul on 2012-11-28
> **oldfred said:**
> Yann wanted your pastebin link that running the BootInfo report gives you. So we can confirm your final working configuration.

You posted the link to the French version of Boot-Repair.

Sorry about the french link but I'm french and it is the link that I found. 
How do I ger the bootinfo?

---

### Post by YannBuntu on 2012-11-28
Please run Boot-Repair --> Create BootInfo, and tell us the URL that will appear (something like **paste.ubuntu.com/1234567** )

(ça aurait été plus facile de demander de l'aide sur le forum ubuntu-fr ;) )

---

### Post by granul on 2012-11-28
> **YannBuntu said:**
> Please run Boot-Repair --> Create BootInfo, and tell us the URL that will appear (something like **paste.ubuntu.com/1234567** )

(ça aurait été plus facile de demander de l'aide sur le forum ubuntu-fr ;) )

here it is : [http://paste.ubuntu.com/1395738/](http://paste.ubuntu.com/1395738/)

---

### Post by YannBuntu on 2012-11-29
Thanks.

---

### Post by mordak13 on 2013-02-01
Thanks for the info guys. I will use it to insatll Xubuntu on my son's new Toshiba laptop. I just want to go on record that Windows 8 is probably the most evil one yet. UEFI/Secure Boot seems merely like a way to make opensource people's lives more difficult.

---

### Post by dnguyen1963 on 2013-02-13
Hi guys,

I just bought a laptop for my mother-in-law and it came with Windows 8.  I tried to get to the Bios to change the boot sequence to CD-ROM, but all I saw was the option for turning on/off secure Boot.  There was no option for booting from CD-ROM.  Will I be able to boot from CD-ROM if I turn the secure boot off then restart the computer?  My intention is to remove Windows 8 completely and install Linux on this computer, if I can boot from Ubuntu Live disk.

---

### Post by sirvinniei on 2013-02-13
> **dnguyen1963 said:**
> Hi guys,

I just bought a laptop for my mother-in-law and it came with Windows 8.  I tried to get to the Bios to change the boot sequence to CD-ROM, but all I saw was the option for turning on/off secure Boot.  There was no option for booting from CD-ROM.  Will I be able to boot from CD-ROM if I turn the secure boot off then restart the computer?  My intention is to remove Windows 8 completely and install Linux on this computer, if I can boot from Ubuntu Live disk.
most pcs should already have booting cd-rom above hdd so turning off uefi should be fine.
If it doesn't boot after turning it on try searching your bios for something like: boot priority or boot order and put your cd-rom drive to the top of the list

---

### Post by dnguyen1963 on 2013-02-14
> **sirvinniei said:**
> most pcs should already have booting cd-rom above hdd so turning off uefi should be fine.
If it doesn't boot after turning it on try searching your bios for something like: boot priority or boot order and put your cd-rom drive to the top of the list

Already searched...could not find any option for booting from CD-ROM in the Bios.  There was no boot order option either.  The only option was just a stupid Windows secure boot.

---

### Post by oldfred on 2013-02-14
Because secure boot prevents booting anything but Windows you have to turn secure boot off. Then you may find other settings. 
Some systems have a UEFI on which means secure boot off. There also should be a setting for BIOS/Legacy/CSM for booting without UEFI.

How you boot install media is how it will install. So if you boot in BIOS mode it will install in BIOS, if you boot in UEFI it will install in UEFI. 
To dual boot you want both systems in UEFI, but a few will only install in BIOS mode. Then you can use Boot-Repair to convert from BIOS to UEFI.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by dnguyen1963 on 2013-02-14
Thank you!  I could get to the Bios to turn off Secure Boot, but the popped up message did not give me the confidence to go ahead and turn it off.  It was very cryptic with a warning that Windows 8 might not boot up properly and the computer might not work correctly with Secure Boot off.  I do not understand Windows 8 enough to take that chance. It will be a few weeks before I travel to my in-laws again to look at the computer.  I'll post back.  As long I can boot from DVD, I'll wipe Windows 8 from the computer.  I am not interested in dual-boot.

---

### Post by oldfred on 2013-02-14
Some have erased Windows 8, but a few required Windows 8 for something. Best to at least do a full backup just in case.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by dmccasland on 2013-03-01
I have spent a few days trying to get Xubuntu/Win8 dual boot to work.  This is on a brand new HP Pavilion p6-2316s Desktop with AMD A4 CPU, prob. manufactured in late 2012.  Win8 pre-installed.

I tried **EVERYTHING**!  All the suggestions from all the forums and Ubuntu website pages, boot-repair multiple times with various options, every UEFI setting (Legacy, Secure boot, fast boot off).  (Actually I didn't try rEFInd boot mgr.)  In every case, time after time, I either got some disk-not-found error or black screen (even with nomodeset).  

Even so, whenever I turned off Legacy (ie UEFI boot only) and SecureBoot, Win8 would still come up.  So that was nice.  That is, until I tried to be clever and install Fedora 18.  That not only didn't result in a bootable Fedora, which I would have settled for vs. Ubuntu, but also made Win8 non-bootable :(.  Then I couldn't get the Win8 recovery to work.  

At that point, I was totally sick of the whole thing.  I was willing to dump my copy of Win8.  I did:

dd if=/dev/zero of=/dev/sda bs=512 count=100000

to get rid of the MBR and GPT tables.  Then I knew that the UEFI firmware would no longer find the EFI partiition and boot from MBR/GPT instead.  In BIOS firmware, I turned off SecureBoot and fastboot and turned on Legacy -- that is how they are labeled in American Megatrends BIOS interface -- press Esc during boot to make changes).   I installed Xubuntu normally.  Upon reboot, Grub menu was displayed!  Had to boot through Ubuntu recovery mode in order to take out splash and add nomodeset to /etc/default/grub and run update-grub.  I cheered when it booted fully after just pressing the power switch!  
 
**Notes**
o  The Xubuntu 12.10 install created a new MBR (but not a GPT).  
o  The UEFI firmware seems to have no problem booting Linux with MBR only (and presumably with a GPT layout).  As long as it doesn't see an EFI partition, all is well.
o  If you want AMD/Radeon's display driver, it's easy -- after install, just do apt-get install fglrx and reboot -- that's it!  It installs Catalyst and runs great.

**EFI / Secure Boot / Fastboot stuff on the AMI/HP (as I understand it)**
o  With the AMI Bios firmware on the HP you have some confusing choices. Default is: Secure Boot enabled and Legacy mode disabled.  
o  BTW, unlike previous AMI UIs, this one says "Enable" to mean enable**d**.  *That's right, they use a verb to indicate a state! * That is really dumb!!!  So remember -- in the new AMI BIOS (at least the one on HP desktops), when you see "Enable" it means it's enabled, and "Disable" means disabled. 
o  Secure Boot is an extra feature for EFI boots -- when enabled, AMI will not boot an unsigned OS in EFI mode (not very useful for current Linux installs).  
o  If Legacy mode is *en*abled, the firmware will allow you to boot from EFI or MBR/GPT.   So enable Legacy, and it will try to boot a UEFI-enabled OS first, then it will look for OSes that have a MBR or GPT boot.  You can change boot order on a one-time basis with F9.
o  You can also have SecureBoot disabled and Legacy disabled.  That should work if you have all the OSes wired correctly for EFI boot  -- very unlikely at this point.
o  FastBoot is a nice feature that gets hardware enabled by BIOS before the OS starts, so this is much faster.  But it requires EFI booting.  

So I can't have Win8 on this same box.  Reason I wanted that, I have an old Windows C compiler and some Windows games and the dual-boot capability would have been nice (plus access to NTFS partition from Linux).  I don't know if off-the-shelf Win8 full-version can be installed into a MBR partition, but not willing to pay $199 to find out.  I think Win7 or Vista can be so installed, and I may have some Win7 or Vista media around somewhere.  I tried installing XP SP1 on this new HP and it blue-screens during install prob. because of hardware issues (and you have to turn on IDE emulation in the BIOS even to start the XP install, as XP doesn't understand AHCI).  But I will try SP2 later.  

I did get to try out Win8 for a few hours and liked some of it.  I suggest creating a "Local User" acct and not using the annoying Live.com login.  But mostly it's Win7 with a nifty Start *page* instead of a boring Start menu and some other special effects.  And it supports touch-screen if you have that.  So, fun to try out, but I really just wanted Xubuntu.

The lesson here, as I see it, is not to try install Linux alongside Win8, esp. pre-installed Win8 with AMI BIOS, esp. HP.  You will waste a lot of time (although you may learn a lot, as I did).  And I'm not saying you won't get it to work somehow.  Maybe Ubuntu 13.04 (or later Fedora) will make this easy.  As it is, my current install does not get any of the technical advantages of UEFI and Fastboot, or access to Win8.  

I don't blame anyone for this.  I don't see how Microsoft can be blamed, they are simply adopting some new publicly documented technologies that Intel started.  Not clear what HP did here, maybe nothing or maybe they somehow made it impossible for the Linux/EFI/shim thing to work.  But I don't see how.  Current desktop Linux and new PCs have now diverged and are no longer as compatible as before or as easy to install, either single-boot or dual-boot.

---

### Post by oldfred on 2013-03-01
I cannot recommend un-installing Windows 8. Some systems have the new UEFI integrated with Windows 8 and if you un-install Windows 8 you may not be able to make UEFI settings.

If you do not totally erase a gpt drive, you may have issues. gpt also has a backup gpt partition table at the end of the drive. So if in MBR mode, you have to also erase backup gpt. Fixparts is a utility to remove that.

Ubuntu runs just fine with gpt partitions and BIOS boot. I have two of my drives and even one flash drive with gpt partitions and boot in BIOS mode on my 6 year old computer. You do have to have a tiny 1MB unformatted bios_grub partition for grub2 to install correctly. But Windows only boots from gpt drives with UEFI.

---

### Post by dmccasland on 2013-03-01
> **oldfred said:**
> ... But Windows only boots from gpt drives with UEFI.

Interesting.  I assume you mean Win8 only boots from GPT that have UEFI?  What about Win7 and Vista (obviously XP doesn't apply here).

---

### Post by oldfred on 2013-03-01
I think some versions of Vista would even boot with UEFI, but all versions of Windows have to have gpt partitioning with UEFI. And if you have gpt partitioning Windows will only boot with UEFI. 
Not many motherboards had UEFI until Intel released the i-series chips. And even then most Windows were using the BIOS/Legacy/CSM mode to boot. A few have posted Windows 7 systems with UEFI but those do not have secure boot. Windows 7 will not boot on a secure boot system.

Ubuntu does not care. It boots from BIOS or UEFI from gpt partitioned drives.

---

### Post by s-manuj545 on 2013-08-19
Hi ,even i was stuck with this for some time. Actually after installing  ubuntu on machine which has windows 8 pre installed with UEFI (as oppose  to those with LEGCY BIOS) ,you need to update the grub for ubuntu. 
Here is a link which shows how to do this stepwise.
[http://binarybyte.blogspot.com/](http://binarybyte.blogspot.com/)

---

