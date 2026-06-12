---
title: "Ubuntu 13.04 Installation Help"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by jpr654 on 2013-12-25
Hi,

I want to dual boot Windows 8.1 and Ubuntu on my Dell Inspiron. Not being completely new to the process, I created a partition (294GB), and formatted it in ext4. I then created my Ubuntu 13.10 Live CD and booted off of it. When I got to the ubuntu installation screen, the program did not recognize that I have Windows 8.1 running on my Inspiron; the only option I have is to either erase my whole drive (which I do NOT want) and put ubuntu on it, or "something else". What do I do now? Can someone walk me through how to configure the grub and partition I want to place ubuntu in?

Thanks so much!

---

### Post by fantab on 2013-12-25
With Windows 8 most of the OEM's use UEFI with EFI System Partition [ESP] to boot.
Win8 has introduced a couple of features that need special attention if you need to dual boot it with Linux/Ubuntu. These are 'Secure Boot' and 'Fast Startup'.
To be able to dual boot Windows 8 both 'Secure Boot' and 'Fast Startup' should be disabled.
While 'Fast Startup' can be disabled from within Windows, 'Secure Boot' can be disabled from the UEFI (previously known as BIOS), depending on the OEM implementation of 'Secure Boot'.
(Ubuntu can install and boot with 'Secure Boot' enabled but it is recommended that you disable it. Don't get fooled by the term 'Secure Boot' it isn't so much a security feature but a marketing catch word by MS. It is 'secure' to disable 'Secure Boot').
How to disable 'FastStartup': [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
How to disable 'SecureBoot': Disabling 'Secure Boot' varies from OEM to OEM, you have find out how to do it on Dell Inspirion (Your Model).

If your Inspirion came with pre-loaded SSD then the chances are that you have IntelSRT enabled. To be able to dual boot Ubuntu you need to disable it in the UEFI.
IntelSRT uses the SSD as a 'cacheing device' and supposedly speeds up Windows. However in its implementation IntelSRT use some sort of Hybrid RAID, and this won't let Ubuntu install on the HDD.
How to disable 'IntelSRT':[http://superuser.com/questions/476777/properly-disabling-intel-srt](http://superuser.com/questions/476777/properly-disabling-intel-srt)

You have to also disable Intel 'Fast Boot'... This feature is nothing but makes the UEFI/BIOS skip certain hardware checks during boot, so that you boot 'faster'. You need to disable this feature as well to boot Ubuntu.
How to disable Intel 'Fastboot': [http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm)

Also with the implementation of UEFI, GPT [GUID Partition Table] is introduced replacing MBR/'msdos' partition table. Windows can only boot from UEFI if the HDD has GPT table. Ubuntu can boot both in UEFI and BIOS modes from GPT.
[Advantages of GPT]("https://wiki.archlinux.org/index.php/GPT#Advantages_of_GPT").

When installing Ubuntu the installer needs to see some free space on the HDD/SSD to be able to complete installation either as 'Unallocated Space' or a 'Linux Partition'.
So you will need to create space for Ubuntu on your HDD. You can do this by SHRINKING one of your Windows partition.
How to 'Shrink' Windows Partition: [http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/](http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/)

It is important how you boot your Ubuntu install DVD/USB. If UEFI then it should boot in UEFI mode only. To know the difference between UEFI boot and BIOS boot see the link below:
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode)

If you are not sure which partition in Windows to Shrink then post the output of the following commands run from Terminal in Live Ubuntu DVD/USB:
```
sudo parted -l
```

Also let us know if your system has '[Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")'... you may have take some additional steps for it.

Good Luck.

---

### Post by jpr654 on 2013-12-25
Thanks so much for the response! I'm having trouble disabling the secure boot feature; I have a Dell Inspiron 15R Special Edition model. Any suggestions on where to start looking at how to disable this feature? I can't seem to find anything on the internet. EDIT: I found under boot options how to disable secure boot; now, do I want to change boot mode to legacy or UEFI?

---

### Post by fantab on 2013-12-25
I think you will have to use your F2 key to enter into UEFI/BIOS setup then using navigational keys select 'boot' from the menu. You will probably find 'secure boot' there.
However, refer to your Inspirion manual to find exact keys and ways to navigate to 'secure boot' in UEFI.... 

Additional Recommendations:
1. Make good backups of Windows, and also make a '[Windows System Repair Drive]("http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB")' before you change anything on the HDD. 
2. Make a Backup of your Windows FAT32 EFI partition in particular and all Windows partitions in general (After you have 'Shrink' the partition), using **[this]("http://www.macrium.com/reflectfree.aspx")** ([more info on this]("http://kb.macrium.com/KnowledgebaseArticle50074.aspx")) or any other tool.

Edit: added intended link to 'more info on this'.

---

### Post by jpr654 on 2013-12-25
Ok. I've successfully disabled secureboot and fast startup. I don't have SSD, so I don't need to worry about SRT. However, I'm struggling to disable fastboot.  Following the instructions, I cannot find anything under boot that resembled fastboot. I did find a number of options that seemed to relate to intel under advanced in the BIOS settings: Intel(R) SpeedStep, Virtualization (enabled), Integrated NIC (enabled), USB Emulation (enabled), USB Powershare (enabled), SATA Operation (AHCI), Adapter Warnings (enabled). My suspicion is that the Intel(R)SpeedStep is the speedboot and I should disable that. Suggestions?

---

### Post by oldfred on 2013-12-25
The fastboot may just be called the fast startup. It may be slightly different by different vendors. But the issue is the always on hibernation with Windows.
Windows also needs chkdsk after any resize, so you need to reboot into it to make sure it has run that before installing Ubuntu.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Other Dells. Most Dells seem to be similar for installing, with just some different options or screen sizes.
      
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

Someone posted that all the features of Sputnik are now in 13.10, so you do not have to add it.

---

### Post by fantab on 2013-12-25
No, Intel Speedstep is not 'fastboot'.
>                      Enhanced Intel SpeedStep Technology allows the  system to dynamically adjust processor voltage and core frequency, which  can result in decreased average power consumption and decreased average  heat production. By decreasing power and heat on desktop PCs, system  builders can (depending on system configurations) potentially lower  acoustics, and even develop more innovative small form factor designs.  Additionally, this feature can help address power concerns in companies  with sites approaching the limits of bounded electrical infrastructures.  Combined with existing power saving features, Enhanced Intel SpeedStep  Technology can provide an excellent balance between providing power when  you need it and conserving it when you don&#8217;t.


It is possible that you may not have Intel Fastboot. Just skip that step.
Like oldfred recommends, do a 'CHKDSK' on Windows file system, especially if the partition you 'Shrink' is C:

---

### Post by jpr654 on 2013-12-25
Awesome! I successfully dual-booted Ubuntu 13.10 and Windows 8.1. Thanks everyone for your help!

---

### Post by fantab on 2013-12-25
That is good news.
Mark the thread as "Solved" using Thread tools.

---

