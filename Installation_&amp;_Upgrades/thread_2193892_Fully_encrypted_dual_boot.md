---
title: "Fully encrypted dual boot"
date: 2013-12-15
forum: Installation &amp; Upgrades
---

### Post by darwinianProduct on 2013-12-15
I'm planning to create a freshly installed fully encrypted dual boot system on a high-end laptop and I hope somebody could point me to the right direction how to do it, as I'm having a hard time finding what is currently the best and easiest way to achieve what I want.

I would like to have my SSD split between Windows 7 and Linux and have my RAID HDDs (with hw controller) as a shared data disc usable from both systems as NTFS formatted Truecrypt encrypted discs. For the Windows side the plan is to put everything into one partition and use Truecrypt system encryption with pre-boot authentication (so Truecrypt takes the MBR).

The Linux side of things is a bit more unclear. I would like to minimize unnecessary partitions to avoid wasting space so I would prefer a single partition or just boot+root partitions, for which boot could be unencrypted if necessary. I don't want a swap partition, I will rather use a swap file if needed. The main questions I have are:

1) Is it so that I cannot use Truecrypt to encrypt the root partition (or to have just minimal boot related things unencrypted and use Truecrypt for the rest)? I would really prefer using one common crypto solution as I will use that anyway to access the shared data discs.

2) Ubuntu (and Mint) installers seem to provide a a full system encryption option (with LUKS/dm-crypt?) in the installer gui already but can it be used to encrypt only the Linux partitions (half of the physical disc) and does it actually encrypt the boot partition as well?

3) Does the built-in encryption play nicely with SSD wear leveling? I know there's some security implications on it but at least I'm not trying to create a hidden OS so as far as I understand it, it shouldn't be that much of an issue.

---

### Post by oldfred on 2013-12-15
I do not pretend to know much about encryption as I do not use it.

We have seen a few users lose dual boot as Linux full disk encryption means full drive encryption or your Windows gets erased. The posts I have seen have both efi (if UEFI boot) and /boot partitions outside of the LVM.

       Restore lost partition that was truecrypt
[http://ubuntuforums.org/showthread.php?t=1874260](http://ubuntuforums.org/showthread.php?t=1874260)
[http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html](http://worldsmostsecret.blogspot.com/2012/04/how-to-activate-trim-on-luks-encrypted.html)

    
 Full Disk encryption
[https://wiki.archlinux.org/index.php/GRUB2#Root_Encryption](https://wiki.archlinux.org/index.php/GRUB2#Root_Encryption)
Dual boot with Windows, Ubuntu encryption install
[http://www.hecticgeek.com/2012/10/how-to-setup-encrypted-ubuntu-installation/](http://www.hecticgeek.com/2012/10/how-to-setup-encrypted-ubuntu-installation/)

One user with truecrypt installed Ubuntu with its boot loader in a flash drive. All auto installs will overwrite the MBR of sda, so your special truecrypt boot loader gets overwritten. This uses used manual install or Something Else and then in combo box for boot loader install on partitioning screen chose to install to sdb which he had as a dedicated boot flash drive.

---

