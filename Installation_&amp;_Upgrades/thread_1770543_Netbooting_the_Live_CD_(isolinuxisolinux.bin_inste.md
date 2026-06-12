---
title: "Netbooting the Live CD? (isolinux/isolinux.bin instead of pxelinux.0)"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by yeswekey on 2011-05-29
I recently bought a laptop. I want to install Ubuntu 10.04 (Desktop edition).

I wanted to install Ubuntu using PXE, but without internet. Therefore I'm left with an option of booting the ISO over the network.

My host computer has Windows XP Pro. I tried extracting the iso to tftp's root folder, and configured Tftpd32 to use **isolinux/isolinux.bin** as boot file instead of **pxelinux.0**

The bootloader loads but gives an error as shown below:
```
ISOLINUX 3.63 Debian-2008-07-15 isolinux:
Cannot boot from this CD. Please try a BIOS update.
```

I came to know that something called NFS is required to do things like this. I downloaded Windows Services for Unix, and I'm stuck up in the installation procedure. What exactly is "User Name Mapping Server"?

Could someone give me a push in the right direction? I want to boot the Live CD (and hence install Ubuntu) via the network.

I know that its easier using CD or USB drive, but I want to learn how to do this.

---

### Post by parthodaskhan on 2012-01-30
Did you find your answer by this because i got stuck with the same problem.  If you do please let me know.  I would like to know the configuration of your default file.

---

