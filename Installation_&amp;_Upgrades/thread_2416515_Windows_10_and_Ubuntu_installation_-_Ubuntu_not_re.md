---
title: "Windows 10 and Ubuntu installation - Ubuntu not recognizing windows."
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by jam7755 on 2019-04-10
Hi,  I am new to ubuntu and have been trying to install it on my Windows 10 machine.  The problem I am running into is that when I run the install program it does not see windows as an existing operating system.  I shrank the size of the Windows boot partition so that now there is more than enough room for the Linux boot partition.  I also set the bios not to boot in fast mode per some information I found on another web site.   Unfortunately this has not helped the situation.  My hardware is 16 months old and it is a system I built myself, so no annoying vendor add on software.  It is a UEFI BIOS but Windows shows it as legacy BIOS.  Based on that I even follow instructions on how to install Ubuntu on a legacy BIOS system to no avail.

If anyone can help me out I would appreciate it.

---

### Post by oldfred on 2019-04-10
What brand/model motherboard? What video card/chip? And SSD?

Have you updated UEFI for motherboard?
If SSD updated firmware for SSD?

Microsoft has required vendors to install Windows in UEFI boot mode since 2012 & release of Windows 8. Users  do have option to install in the now 35 year old BIOS/MBR configuration, but that is more for large users/corporations that want same configuration across hundreds or even thousands of systems, and some may be older hardware and some newer.
How you boot install media, UEFI or BIOS, is then how it installs for both Windows & Ubuntu.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jam7755 on 2019-04-13
Oldfred, I finally got the time to get this information for you.  It is listed below.  Note that I built this system myself so no vendors like DELL or HP involved.

Mother board: ASUS ROG STRIX X370-F
BIOS version:  8103 X64.  Not most recent version.
Video card: ASUS Geforce gtx 1050TI
SSD: Samsung 860 EVO. Windows 10 is installed on this and this is where I am trying to put Ubuntu.  I have not updated the firmware.

Link to Boot-info summary report:  [http://paste.ubuntu.com/p/yG2Z7h2ZZH/](http://paste.ubuntu.com/p/yG2Z7h2ZZH/)

---

### Post by oldfred on 2019-04-13
> Windows not detected by os-prober on sda2.
Most often that is because you still have Windows fast start up on.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You also have very new UEFI based hardware, but installed Windows in the now 35 year old BIOS/MBR configuration. Microsoft has required vendors to install in UEFI boot mode since Windows 8 in 2012. But users still can use BIOS/MBR.
How you boot install media UEFI or BIOS, for both Windows & Ubuntu is then how it installs.

UEFI and BIOS do not mix. Either reinstall Windows in UEFI mode or boot Ubuntu in BIOS boot mode to install. Note Windows 10 is not dual boot friendly with old BIOS on one drive. Best to have one system on one drive and one on the other if you really want BIOS.
Either way make sure you make a Windows repair flash drive or have installer with repair console.

With nVidia you will need nomodeset to boot install media and first boot of install or until you install nVidia driver from Ubuntu repository.
       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
For UEFI install see link in my signature, below.

 Some issues are by brand/ model of CPU and some generic to chip version.
So Asus issues all the way back to Z97 may be similar.
      
 MSI Tomahawk Z370 GTX 1070 TI [SOLVED] Grub error during install two NVMe drives
[https://ubuntuforums.org/showthread.php?t=2398599](https://ubuntuforums.org/showthread.php?t=2398599)
Asus X299 Wired Internet issue, UEFI system clock
[https://ubuntuforums.org/showthread.php?t=2395036](https://ubuntuforums.org/showthread.php?t=2395036)
[https://ubuntuforums.org/showthread.php?t=2397473](https://ubuntuforums.org/showthread.php?t=2397473)
MSI X370 Gaming Plus used rEFInd
[https://ubuntuforums.org/showthread.php?t=2378837](https://ubuntuforums.org/showthread.php?t=2378837)
Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)
BIOS only install Asus Z97-a
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)

---

### Post by jam7755 on 2019-04-13
Thanks for all of the info.  Fast boot mode has been disabled since I  posted this thread.  I just looked at the BIOS and the launch CSM boot  device control is set to "UEFI and Legacy OPROM".  The Boot from network  devices is set to "legacy only".  Boot from storage devices is set to  "legacy only".  Boot from PCI expansion slots is set to "legacy only".  Now the questions at the front of my mind are:



[LIST=1]
[*]There is an option to set the CSM device control to UEFI only.  Would you recommend I change it to that?
[*]Should I change the other three settings to UEFI only as well?
[/LIST]

---

### Post by oldfred on 2019-04-13
You have Windows installed in BIOS/CSM/Legacy boot mode. 
You cannot easily convert it, you have to reinstall if you want Windows in UEFI boot mode.
You need to be consistent, always BIOS or always UEFI.

I had to turn off all legacy settings and only use  the UEFI only setting to get Ubuntu to boot in UEFI mode. But you cannot mix UEFI & BIOS on same drive.
I also turn off totally network boot as I will not use it and do not want  system looking for network when I will not use it for booting.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations

      [/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 
    [URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]
[/URL]

---

### Post by jam7755 on 2019-04-20
It's up and running now!  Actually it has been for a week now.  Thanks for your help, oldfred.  I still have to tweak things a bit but I am essentially at the point I wanted to be.

---

### Post by oldfred on 2019-04-21
Glad you got it working.

---

