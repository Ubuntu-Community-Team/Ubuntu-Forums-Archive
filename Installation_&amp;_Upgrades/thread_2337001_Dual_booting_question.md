---
title: "Dual booting question"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by pboev on 2016-09-13
Hello,

I know there are hundreds of threads covering this but nothing seemed to work for me. Here's the issue:

I have a PC running Windows 7 and need to dual boot with Ubuntu. I added a second HDD to install Ubuntu to. While installing it, Ubuntu didn't see Windows and so I didn't have the option to install alongside it so I followed this article: [http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/) 

To sum it up - it tells me to create efi, swap, root and /home partitions and then install the bootloader to the efi partition. I don't want a separate partition for /home so I created just the efi, root and swap spaces. 

After installing it and chosing to boot from the HDD with Ubuntu, the PC booted straight into Ubuntu without GRUB prompting me which OS to boot. If I boot from the Windows HDD, the PC starts up Windows. Occasionally it launches an HP repair utility (I'm using an HP workstation) but if I close it and reboot, Windows starts ok. I noticed this in the BIOS boot menu:
[http://i64.tinypic.com/vimcdf.jpg](http://i64.tinypic.com/vimcdf.jpg)

Under "UEFI" devices, there's only ubuntu and not windows. If I want to boot Windows it has to be as a legacy device. As a first guess, I wonder if it has to do with the fact that windows isn't a UEFI device?

Moving forward, this is the info I get from gparted and parted for the Ubuntu HDD
[http://i63.tinypic.com/153s9ra.png](http://i63.tinypic.com/153s9ra.png)

And for the Windows HDD:
[http://i64.tinypic.com/20hndxt.png](http://i64.tinypic.com/20hndxt.png)

Also, the output from "parted -l" and "fdisk -lu" commands:
[http://i68.tinypic.com/xlcy7s.png](http://i68.tinypic.com/xlcy7s.png)

The "os-prober" command returns nothing.

My finger points to the HP Recovery Partition on the Windows HDD (sdg) and I'm tempted to either delete it or set it as a non-bootable partition. However, I don't really want to play around with it in case that fails. 

Any suggestions how to make GRUB see both Ubuntu and Windows?

UPDATE: I tried Boot Repair as well - no luck.

---

### Post by oldfred on 2016-09-13
That your Windows drive does not have an ESP - efi system partition and that it is MBR says Windwos is installed in BIOS boot mode.
But that Ubuntu has ESP & gpt says it is installed in UEFI boot mode.

You cannot switch boot modes once you start booting. They write data onto drive differently for operating system to use. Or you cannot dual boot from grub only from UEFI.

You can use Boot-Repair to un-install grub-efi-amd64 and reinstall grub-pc(BIOS) to convert Ubuntu to BIOS boot. Then you could dual boot from grub menu.

Do not think there is a way to easily convert Windows to UEFI. Windows only boots with UEFI from gpt partitioned drives and requires additional partitions, ESP, system reserved & now Windows 10 also wants a recovery partition.

How you boot install media for both Windows & Ubuntu is then how it installs. Best to always boot in UEFI or always boot in BIOS boot mode. But HP has not been UEFI dual boot friendly and needs work arounds to boot Ubuntu in UEFI mode.

---

### Post by pboev on 2016-09-15
That makes sense. Thanks for your help!

---

