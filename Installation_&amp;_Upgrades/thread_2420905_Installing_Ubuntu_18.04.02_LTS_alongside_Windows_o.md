---
title: "Installing Ubuntu 18.04.02 LTS alongside Windows on Dell laptop for dual boot"
date: 2019-06-12
forum: Installation &amp; Upgrades
---

### Post by jeremy314 on 2019-06-12
Hello,

I got a new laptop, a Dell Precision 5530 with Windows 10 on it. I would like to install Ubuntu 18.04.2 LTS to have a dual boot option :)

First time I do it, so I started following instructions I found on the Internet here [https://www.groovypost.com/howto/dual-boot-windows-10-linux/](https://www.groovypost.com/howto/dual-boot-windows-10-linux/)


Here is what I've done:

- Got the image
- Created a bootable copy on an USB stick
- Updated the BIOS so I can boot from the USB stick

Launching Ubuntu from the USB stick works but I don't see the page I'm supposed to see from the instructions (expected), I actually get (actual) which seems to indicate that Windows 10 is not detected?

Since it was not working I tried a few things (incrementally) but got the same results.
- Suspended BitLocker protection in Windows
- Disabled Secure Boot in the BIOS
- Turned off device encryption in Windows
- Set UEFI Boot Path Security to Never in the BIOS
- Disable Intel SGX in the BIOS


I'm now out of things to try...

What am I missing?
Any recommendations? I read somewhere to install 16.04 first and then upgrade?

Thank you all,
Jeremy

Expected
[ATTACH=CONFIG]283421[/ATTACH]

Actual
[ATTACH=CONFIG]283422[/ATTACH]

---

### Post by yancek on 2019-06-12
Ubuntu has it's own site with documentation on dual booting with windows 10 which is better than any third party site.  See the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your windows partitions may not be seen by the installer because they are hibernated.  This is the default with windows 10.  Turn off anything related to hibernation or fast boot.  Also, better to use the manual install method called Something Else in Ubuntu although this should not be necessary.  Probably would be a good idea to shrink the largest windows partition from windows Disk Management and reboot and run chkdsk from windows as a precaution before beginning the Ubuntu install.

---

### Post by oldfred on 2019-06-12
In addition, Dell need a few more settings.
Dell usually has RAID or Intel SRT on, that has to be changed to AHCI.
Most Dell need UEFI update & SSD firmware update (if SSD), even if new. Make sure you have most current versions of firmware.

       Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254) 
    
Most Dell have similar UEFI, so similar issues. Bigger difference if Intel or AMD based.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)

---

### Post by jeremy314 on 2019-06-18
Thank you all for your replies. It was very helpful. Thanks to you I managed to do it, here are the steps I've done.

NOTE: Forgot to mention that the storage is on SSD

- Under Windows went to "Dell Command and Update" and updated the BIOS SW


- Followed all the instructions from:

[https://www.dell.com/support/article/us/en/04/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en)

In the BIOS, changed the SATA Operation from RAID to AHCI. 
From there was able to install Ubuntu but Windows couldn't boot unless I changed the SATA Operation back to RAID.


- Converted Windows to AHCI by following instructions from:

[URL="https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on"]https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on

[/URL]

Now the PC can dual boot!

---

