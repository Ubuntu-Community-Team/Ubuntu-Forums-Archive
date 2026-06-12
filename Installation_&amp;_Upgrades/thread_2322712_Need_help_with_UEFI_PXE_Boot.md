---
title: "Need help with UEFI PXE Boot"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by Vasco_Reis_Silva on 2016-04-30
So, I've successfully configured BIOS PXE Boot to serve Ubuntu and Clonezilla live images over my network, however, I'm struggling with UEFI boot. 

I'm using an OpenWRT router for DHCP, TFPT, NFS and all the setup, using syslinux pxelinux.0 and other necessary files, but I can't seem to find the correct files and code in dnsmasq to boot in UEFI.

The code syntax in OpenWRT is the following:

>  option tftp_root '/mnt/sdb1/PXEboot'
 option dhcp_boot 'pxelinux.0'

I've tried using examples such as [this]("https://wiki.kubuntu.org/UEFI/SecureBoot-PXE-IPv6") with no sucess.

Any ideas?

Thank you!

---

### Post by wildmanne39 on 2016-04-30
Thread moved to installation and upgrades so you can get the help you need.

---

### Post by oldfred on 2016-04-30
Do not know anything about network booting.

But multiple users with UEFI have not had correct UEFI boot and UEFI went to next boot in UEFI boot menu and that was PXE boot.
My UEFI has network boot option.

sudo efibootmgr -v
Boot0004* UEFI:Network Device    BBS(131,,0x0)

---

