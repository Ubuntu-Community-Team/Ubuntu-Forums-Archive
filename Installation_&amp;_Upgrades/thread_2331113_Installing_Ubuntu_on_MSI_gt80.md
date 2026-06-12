---
title: "Installing Ubuntu on MSI gt80"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by juliussaldana1995 on 2016-07-18
So a few days ago I bought the **MSI gt80 titan**. First thing I did when I bought it was uninstall Windows and attempt to install Ubuntu, but I've been having a bit of trouble. I guess the problem is that my computer has **2 SATA SSDs** linked in** RAID0**, and this causes Ubuntu's ubiquity installer to crash somewhere in the middle of the install (it actually crashes while installing Grub). Also, due to my graphics, I have to use ```
nomodeset
``` to live boot Ubuntu or install it, otherwise i get a black screen. I've **disabled secureboot, intel speedstep, and fastboot,** and also tried booting with **Legacy** mode and also **UEFI + CSM mode**, and just normal **UEFI mode**, and none of these has prevented the installer from crashing.

I was wondering how I could install Ubuntu with RAID 0 for my 2 SSDs? Or, how could I break the RAID and just have 2 SSDs and then install Ubuntu normally (assuming that RAID is the reason why the installer is crashing)? I'm a bit hesitant to break RAID for a couple of reasons, but if that would be faster and easier I would probably resort to it.

---

### Post by oldfred on 2016-07-18
RAID 0 is not really recommended.
And SSD make system fast, it used to be with older slower drives that those using drive a lot like compiling large programs used RAID 0. But no data was saved to RAID 0 as it can be fragile. Or if you want to keep it, really good backups are required.

It used to be that Ubuntu desktop installer would not work at all with any RAID nor LVM. With 12.04 there was an alternative installer that included the extra drivers, but alt. installer was discontinued. They were going to add everything to desktop, but only LVM is fully working in Desktop installer.
You may be able to install server version and then add desktop of your choice.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Do not know if any of these still apply. Issues are common by vendor as UEFI/BIOS is same with configuration somewhat different for each model.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912) 

I would suggest using UEFI and gpt partitioning.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Different computer, but dual SSD with RAID.
 Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

---

### Post by juliussaldana1995 on 2016-07-19
I just don't understand how I would break RAID and not use it

---

### Post by oldfred on 2016-07-19
With RAID 0 part of data is on one drive and part on other drive. Every other stripe. So when one drive fails every other stripe of data is lost. With SSD you really do not have stripes but same logic.

So you have to fully backup entire system. Remove RAID setting(s) from UEFI/BIOS, remove RAID meta-data from drives or fully erase them.
Then restore system to one drive. Other drive then is available and you could have Windows on one drive and Ubuntu on other drive. And data from each on opposite drive to provide some data redundancy but not really full backup.

Because of the nature of RAID 0 you have to have those full backups anyhow.
With my new Dell with only one hard drive, it wanted me to make a Dell backup, a Windows backup and I then made a full backup using Macrium Reflect. And I did not want Windows, but ended up having to use it for Comcast video. Took several flash drives & DVDs to do all the backups. Then upgraded to Windows 10 and that was more backups. With Ubuntu I know I can easily reinstall system and only have to backup my data and configuration settings, much easier.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

