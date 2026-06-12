---
title: "Install on a Standalone LAN Harddisk"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by control_guy on 2008-04-07
Hello All

I would like to know if it is possible to install Ubuntu on a standalone external Ethernet-based hard disk serving as either SMB/FTP/DHCP-Server?

It is possible for me to install GRUB locally on my (primarily) Windows machine. After booting off the local hard disk, I would like to use the remotely installed Ubuntu. Is it possible? If yes, could someone kindly guide me to a resource that describes this procedure?

Thanks

---

### Post by dstew on 2008-04-07
> I would like to know if it is possible to install Ubuntu on a standalone external Ethernet-based hard disk serving as either SMB/FTP/DHCP-Server?If I understand correctly, you want to boot Ubuntu onto your Windows machine, keeping the kernel images and root file system on the server, correct? This is known as running a "thin client". To do it, your Windows machine needs to have a BIOS that is netboot-capable, usually a PXE-BIOS. See if you have a netboot option of some kind on your BIOS boot menu. Sometimes it might be labeled as PXE, or network boot, or network re-install boot.

If your BIOS is netboot capable, then you can use grub to boot a kernel over the network. See the [grub manual section on network booting]("http://www.gnu.org/software/grub/manual/grub.html#Diskless"). However, if your BIOS is not network-boot capable, grub is too small to get its stage2 and configuration files over the network by itself. It need help from the BIOS.

Here is an [Ubuntu Thin Client How-To]("https://help.ubuntu.com/community/ThinClientHowto"). It looks a little old. Here is an [Ubuntu document on netbooting]("https://help.ubuntu.com/community/Installation/Netboot"). I used this one to install over a network. See [this thread]("http://ubuntuforums.org/showthread.php?t=690483&highlight=powervault") for my experience. You can install or run using the same overall scheme.

On the other hand, if you want to install Ubuntu as the *operating system* on the network server, you can do that too. Usually, a network server without any CD-ROM drive or bootable USB drive has a PXE BIOS, so you can install Ubuntu that way.

---

### Post by control_guy on 2008-04-08
Thank you.

You understood me correctly. I meant a thin-client. I have checked that my computer BIOS is netboot-able. I shall give it a try once I get my LAN-based drive.

---

