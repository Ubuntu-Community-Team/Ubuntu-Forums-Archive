---
title: "unable to boot ubuntu 16.04 with Win 10in EFI"
date: 2017-04-17
forum: Installation &amp; Upgrades
---

### Post by michael-n-meyer on 2017-04-17
I am attempting to install ubuntu Gnome 16.04 with Win 10 with EFI boot partition. My root and home are BTRFS partitions because I want to use the Snapper app for automated snapshots of my system. I'm running a new MSI GT62VR laptop with an Intel I7 CPU. I'm running a new MSI GT62VR laptop with an Intel I7 CPU.


I installed Ubuntu through the Live USB as a custom installation. Windows was preinstalled. The reason I went with Custom is because:  
  a. the auto installer wanted to put Ubuntu on a separate, slower hard drive, which is unacceptable for me because I want both OS'es to share the M.2 SSD drive.
  b. My root and home are BTRFS partitions instead of the default EXT4 because I want to use the Snapper app for automated snapshots of my system
  c. I used an EFI enabled USB drive because I wanted the option to dual-boot without switching to legacy Bios each time.
d. If successful with dual boot, I'd like to eventually do a triple boot to Qubes OS for experimental purposes. Ideally, if it performs well with my hardware, I might transition 100% to that OS for everything.


Currently, Windows boots and Ubuntu does not. I've tried everything including the Boot-Repair several times, multiple reinstallations, EasyBCD, and even some manual BCD edits. 

Here is my Boot-Repair read out on pastebin. Any advice appreciated. I am not brand new to Linux, but not a wiz at this either so please provide detailed instructions.

[http://paste2.org/BF1NPJGC](http://paste2.org/BF1NPJGC)
.

---

### Post by oldfred on 2017-04-17
With UEFI you should not need nor use EasyBCD except to repair a Windows BCD.

You should always boot in UEFI mode. 
Somehow you installed a BIOS boot loader - syslinux to gpt's protective MBR. That normally is not used with UEFI, so better to just ignore as dd is dangerous and only way to erase it and only booting in BIOS would attempt to boot using it and that would error out.

You somehow installed grub to the partition boot sector of the ESP, sda1 and added full grub.cfg files for OpenSuse. Not sure if OpenSuse would require those files, but with UEFI doubt it. May need to backup entire ESP, delete it, recreate new FAT32 partition and restore all folders except /grub & /EFI/opensuse.

You also still have the "normal" UEFI boot entries for OpenSuse in /EFI/opensuse  in ESP and entries in UEFI as shown by efibootmgr's list. 
Both opensuse folder & entry in UEFI can be deleted.

Do not know about BTRFS file systems. Have seen one or two other threads where users had issues.

Boot-Repair did seem to want to run either ntfsfix or fsck. Neither does much. 
ntfsfix only turns on chkdsk flag. And Boot-Repair often tries to run it on unformatted partitions like Microsoft's system reserved which must be unformatted.
And fsck is only for the ext2, ext3 & ext4 family of formats. If file repair is required on your BTRFS, you have to use tools from that family.

Other MSI systems has requirements for boot parameters.
 Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)

---

### Post by michael-n-meyer on 2017-04-17
Thanks for the detailed reply. I had a successful dual boot with OpenSuse last night, then deleted Suse because there were a few things I didn't like about it. Let me make sure I understand what you are recommending I do before I fumble more stuff up here.

1. Use Boot-Repair to backup entire ESP partition and save somewhere.
2. Delete ESP partition and make a new FAT 32 with Boot Flag and ESP flag. 
3. Run Boot-Repair and do auto-repair, then go to advanced mode and select repair windows boot

If this is incorrect, please lay out for me. Thanks!

---

### Post by oldfred on 2017-04-17
I did not think Boot-Repair backs up entire ESP.
You can just copy with rsync, cp -a or even any file browser. UEFI boot files do not require any install. 
Entries into UEFI may require install.

Yes delete & recreate ESP.

No need to auto repair with Boot-Repair, but just use advanced mode.
Boot-Repair can do very little Windows repairs, most require your Windows repair flash drive or installer with its repair console.

Advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by michael-n-meyer on 2017-04-17
Thanks OldFred. I deleted ESP, created a new one and reinstalled ubuntu so now it boots into that instead of Windows. I will do a boot repair from windows USB later, followed by boot-repair in Ubuntu and hope that does the trick.

---

