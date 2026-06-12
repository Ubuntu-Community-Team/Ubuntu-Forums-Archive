---
title: "Unlabeled Hard Drives after installing 13.10"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by john_kouts on 2014-02-03
Hi,

I tried to install Ubuntu 13.10 alongside Windows 8.1 from bootable USB. I firstly made (unallocated)space (10GB) from windows disk management tool as most tutorials advice and then restarted the laptop in order to install Ubuntu. Successfully, the 'install alongside windows 8" selection appeared so I clicked on it. After successfully installing  Ubuntu, I realized that, when I click to open one of my hard drives nothing happens. In addition, I couldn't install any update because of "lack of enough free space" (which actually I had). So I changed back to Windows and released that: From the 10gigs of the Ubuntu partition, Ubuntu decided to make a partition of size fitting exactly Ubuntu's installation (5.91gigs) and leave the rest 4.09gigs as another blank partition. **Both of them are unlabeled. **This means that I cannot access them through Ubuntu, are not visible in Windows 'my computer' and generally, I can't do anything with them (see attachment). Finally, I Google my problem and couldn't find something similar. [B]Can you help please? Any way to label & merge? 
[/B]
P.S:  Since they decided to cancel Windows installer as in 12.04 was, was it so difficult to develop an easy and intuitive way to install them alongside Windows????

---

### Post by ubfan1 on 2014-02-03
10G is too small.  You probably have a root (/) partition and a swap partition in that 10G.  It should run though.  Labels are not needed.  Boot from the live media and select "Try", then start a terminal and run sudo fdisk -l   to see the disks from Ubuntu.  Maybe you could run boot-repair to fix the booting, but really, I'd delete both partitions, free up more space, and start with enough space.  20G minimum.

---

### Post by oldfred on 2014-02-03
It is normal for  Windows not to see Linux partitions. It does not work well with Linux.

Using only 10GB is the lower end of what I suggest for / (root) partition. On newer drives with more room I suggest 10 to 25GB for / and 2GB as a minimum for swap. I do not like auto installs although for newer users that do not understand partitioning that is often the better way to start out. And if dual booting with Windows it is usually better to have another NTFS data partition or d: in Windows.

Never create new partitions in Windows as it may convert to dynamic partitions. But use Windows partition tools to shrink the Windows partition.

Wubi's last supported version is 12.04 as all new Windows 8 systems use UEFI with gpt partitioning. And wubi is not compatible with gpt and UEFI. And with gpt it is easy to add new partitions as the new (soft) limit is 128 partitions, not the old 4 primary partition with MBR(msdos). And UEFI is supposed to fully support multiple booting, but some vendors have modified UEFI to only work with Windows. Boot-Repair has a work around for those.

Use Windows to shrink your Windows install a bit more. 
You can use gparted on live installer to modify or delete Linux partitions.

Do not use an option that says overwrite Ubuntu. There is a installer bug where with Windows 8 may be hibernated or fast boot on and the installer does not see Windows so the entire drive is erased.
Best to have good backups of Windows. 

Is your Windows UEFI or BIOS?

Post  this from terminal in live installer.

sudo parted -l

---

### Post by john_kouts on 2014-02-04
> **ubfan1 said:**
> 10G is too small. You probably have a root (/) partition and a swap partition in that 10G. It should run though. Labels are not needed. Boot from the live media and select "Try", then start a terminal and run sudo fdisk -l to see the disks from Ubuntu. Maybe you could run boot-repair to fix the booting, but really, I'd delete both partitions, free up more space, and start with enough space. 20G minimum.


Can you provide me with a tutorial about deleting both partitions? I have also to modify something concerning the 'select the operating system' screen when I turn on my laptop I guess.
In addition, a good tutorial on successfully installing Ubuntu 13.10 again is very welcome!

Thanks!

> **oldfred said:**
> It is normal for  Windows not to see Linux partitions. It does not work well with Linux.

Using only 10GB is the lower end of what I suggest for / (root) partition. On newer drives with more room I suggest 10 to 25GB for / and 2GB as a minimum for swap. I do not like auto installs although for newer users that do not understand partitioning that is often the better way to start out. And if dual booting with Windows it is usually better to have another NTFS data partition or d: in Windows.

Never create new partitions in Windows as it may convert to dynamic partitions. But use Windows partition tools to shrink the Windows partition.

Wubi's last supported version is 12.04 as all new Windows 8 systems use UEFI with gpt partitioning. And wubi is not compatible with gpt and UEFI. And with gpt it is easy to add new partitions as the new (soft) limit is 128 partitions, not the old 4 primary partition with MBR(msdos). And UEFI is supposed to fully support multiple booting, but some vendors have modified UEFI to only work with Windows. Boot-Repair has a work around for those.

Use Windows to shrink your Windows install a bit more. 
You can use gparted on live installer to modify or delete Linux partitions.

Do not use an option that says overwrite Ubuntu. There is a installer bug where with Windows 8 may be hibernated or fast boot on and the installer does not see Windows so the entire drive is erased.
Best to have good backups of Windows. 

Is your Windows UEFI or BIOS?

Post  this from terminal in live installer.

sudo parted -l

I let you know when I log on in Ubuntu again. The difference about UEFI & BIOS is on the 'select the OS' screen? (purple Ubuntu screen & Black/white BIOS style one?)

---

### Post by oldfred on 2014-02-04
Lots more info in link in my signature. You choose to boot with UEFI or BIOS mode from UEFI/BIOS menu of bootable devices. Once you start to boot in one mode you cannot change.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

