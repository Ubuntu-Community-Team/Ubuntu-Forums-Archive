---
title: "Ubuntu doesn't recognize Windows 8"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by tom327 on 2013-04-28
I am trying to dual boot Ubuntu 13.04 with Windows 8, but the Ubuntu installer claims that there isn't an operating system on the hard drive. How do I get the installer to recognize that Windows 8 is on my hard drive? My computer is UEFI with secure boot on, if that helps.

---

### Post by oldfred on 2013-04-28
You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode. Some do need secure boot off.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by tom327 on 2013-04-28
Okay, thanks. Is there anyway to install without manually partitioning? I heard that there is supposed to be a "Install along side Windows" option, but it doesn't come up for me.

---

### Post by oldfred on 2013-04-28
If you use Windows Disk partitioning tools to shrink Windows NTFS partition to make unallocated, the Ubuntu will have space to install into. Better to do that with Windows than use the installer's tools as Windows still has to run chkdsk or make repairs to its new size.

Then you should get another install option.

---

### Post by tom327 on 2013-04-28
I tried that, but Ubuntu still doesn't recognize Windows. I think I will just go with manual partitioning. Before I do so, I have a few questions:

1. Do I need to create a new EFI partition for Ubuntu, or can I just use the one my computer came with?
2. In the drop down menu for boot-loader location, do I choose the EFI partition, or the partition where i am putting Ubuntu?
3.Other than EFI and the main partition, do I need any other partitions for Ubuntu?

---

### Post by tom327 on 2013-04-28
Okay, I got Ubuntu to dual boot, but now it refuses to connect to the internet, via ethernet or wifi. It can see wifi networks, it just can't connect.

---

### Post by oldfred on 2013-04-28
You can only have one efi partition per hard drive.

If dual booting with Windows it often is best to have a separte NTFS shared data partition and only read data from the Windows system partition.

Most systems just work with Ethernet, but many do have issues with wifi and there are a lot of threads on the specific models that have issues. Both my systems work without issue, so I do not know details.
Best to start a new thread with the model of your wifi & Ethernet chip in the title.

Many knowledgeable on wifi will want this info:
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

### Post by tom327 on 2013-04-29
okay, thanks for the help.

---

