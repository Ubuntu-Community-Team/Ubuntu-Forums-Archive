---
title: "Ubuntu 18 Fresh Install Fails to boot after first reboot"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by rgibsoniv on 2018-09-06
Hello all,

I have a Dell Inspiron All in One 3475 Desktop, I am attempting to install Ubuntu onto it, the install succeeds and directs me to the desktop. 

So I did some configuring and installing steam and chrome etc, making some tweaks. And once I restart the PC it will fail to boot into Ubuntu instead flashing the purple ubuntu screen for .5 seconds and then staying stuck at a black screen (monitor is off no display, but mouse and num pad light are illuminated)

I booted into ubuntu live and got this pastebin

[http://pastebin.ubuntu.com/p/Zw3mTsHt3S/](http://pastebin.ubuntu.com/p/Zw3mTsHt3S/)

I tinkered with EFI/ Secureboot settings due to me wanting to install openrazer and other programs without having to fiddle with the EFI and secureboot in terminal (cannot figure that out)

Anyways if anyone can help it would be appreciated

cheers.

---

### Post by oldfred on 2018-09-06
Many Dell need UEFI update from Dell. And if SSD, firmware update for SSD.
Did you change drives from RAID to AHCI in UEFI?

Similar model?
       Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

