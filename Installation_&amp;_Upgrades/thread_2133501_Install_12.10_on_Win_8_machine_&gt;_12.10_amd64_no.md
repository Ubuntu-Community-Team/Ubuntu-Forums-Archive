---
title: "Install 12.10 on Win 8 machine &gt; 12.10 amd64 not loading with Boot Security Enabled"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by dcunited on 2013-04-08
I recently bought an Asus laptop with Windows 8 preinstalled and had hoped to dual-boot it with Ubuntu 12.10.  I created a USB but my USB only boots when I have Boot Security disabled.  In that mode, I am unable to resize the Win8 partition to create room for Ubuntu. When I enable Secure mode, it allows me to choose the try live option but does not actually boot once I choose it.  Any suggestions?  I have used [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) as my guide but, since it will not boot with security enabled, I am stuck.

---

### Post by oldfred on 2013-04-08
I think most users have had to turn secure boot off to get any external device to boot. Can you boot a Windows Repair flash drive. Some have reported that does not work either so if Windows does not boot, you cannot repair system. Make sure you have the newest UEFI/BIOS installed as vendors are making lots of updates.

Use Windows Disk tools to resize the Windows partition and reboot so it can run chkdsk or make other fixes to its new size.

A few computers will only boot in BIOS mode, better to install in UEFI mode, but if necessary Boot-Repair can convert a BIOS install to UEFI.

 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

