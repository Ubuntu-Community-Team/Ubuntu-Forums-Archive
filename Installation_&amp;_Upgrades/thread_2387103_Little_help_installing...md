---
title: "Little help installing.."
date: 2018-03-14
forum: Installation &amp; Upgrades
---

### Post by Zaphan58 on 2018-03-14
Hi all, I've got a new Dell laptop I want to install Ubuntu on. Looking at the drive in Windows it has 5 partitions which are below. I am presuming I can get rid of them all apart from the EFI one? My understanding is that since I have an SSD this is needed? Will the Ubuntu install give me the option of which partitions I want to keep?

EFI System partition (500MB)
OS (462.91GB)
Recovery partition (486MB)
Recovery partition (11.83GB)
Recovery partition (1.09GB)
Unallocated (13MB)

Thanks

---

### Post by oldfred on 2018-03-14
Best to do a full backup of Windows.
We have many users who make leap to all Ubuntu, then find one game or application that only works in Windows that they must have.

Dell needs some settings changed in UEFI to work in UEFI boot mode. How you boot install media is then how it installs. You want UEFI.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Even if model not exactly the same, issues are common across many models by vendor.

 Dell XPS 13 with Factory 16.04 fixes/issues
[https://ubuntuforums.org/showthread.php?t=2357424](https://ubuntuforums.org/showthread.php?t=2357424)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)

General UEFI install info in link below in my signature.

---

### Post by Zaphan58 on 2018-03-15
Thanks, yes I have been trying to make an image of the windows install in case I want to go back.  But the Windows drive image tool keeps failing :/ 

Thanks for those links I'll have a good read.

---

