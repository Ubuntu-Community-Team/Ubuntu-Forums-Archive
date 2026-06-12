---
title: "how to customize my net installer initrd"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by batingo on 2014-03-22
I'm trying PXE to install ubuntu on my bare-metal servers, and I have some problem in the installation process.
[LIST=1]
[*]I tried whole auto install from PXE on VM, it's work !!
[*]I tried to install the server from CDROM, everything fine.
here is the most important NIC information 
> [COLOR=#000000][FONT=&#24494]01:00.0 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=&#24494]01:00.1 Ethernet controller: Intel Corporation I350 Gigabit Network Connection (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=&#24494]82:00.0 Ethernet controller: Intel Corporation 82599EB 10-Gigabit SFI/SFP+ Network Connection (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=&#24494]82:00.1 Ethernet controller: Intel Corporation 82599EB 10-Gigabit SFI/SFP+ Network Connection (rev 01)[/FONT][/COLOR]


> 
here is the driver info. for nics
[COLOR=#000000][FONT=&#24494]igb: Intel(R) Gigabit Ethernet Network Driver - version 4.1.2-k[/FONT][/COLOR]
[COLOR=#000000][FONT=&#24494]ixgbe: Intel(R) 10 Gigabit PCI Express Network Driver - version 3.11.33-k[/FONT][/COLOR]



[*]then I tried to boot from PXE to install the server, I copied the kernel file and initrd.gz from CDROM/install/netboot/ubuntu-installer/amd64.
[*]I tried 12.04.1, the installer didn't load the driver module igb for the I350 nic, but is loaded the ixgbe for the 10-G nic, and I add the insmod=igb in the pxeconfig, seems not work, it didn't load the module automatically. after boot, I tried to insmod manually, the installer busybox didn't have ifup/ifdown/ifconfig tools, how do I bring the interface up ?
[*]I tried 12.04.4, the installer load igb and ixgbe module automatically, but the interface still down, so the the installer can not load DHCP or static IP from preseed file.
[*]I know how to pack/unpack initrd, but I don't know which file to modify to let the installer can auto load some modules that I specified, and bring up my NIC.
[*]the installer is too "lite" for me, for example, the installer only build in with nano, but I'm familiar with vim, if I want to add some other elf binary like vim/curl/ifdown/ifup/ifconfig in to the installer, how to do to solve the libraries dependence issue?
[*]I want to know more about the installer boot/installing detail, hope someone kindly tell me if any website/book that I can study.
[/LIST]
thanks.

Vistac

---

