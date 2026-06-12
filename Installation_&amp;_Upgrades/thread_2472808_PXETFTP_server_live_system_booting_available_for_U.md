---
title: "PXE/TFTP server live system booting available for Ubuntu desktop or server?"
date: 2022-03-13
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2022-03-13
It has been a while, but I got server w/tftp set up ok, as far as I know (I can use tftp client to get a simple text file).
Server used: Ubuntu Desktop 21.10, with tftp-hpa,

After I configure PXELINUX, what files from the Ubuntu ISO shall I copy to the tftp server directory, and any hints for the pxelinux menu entry would be great.

I do know at least the kernel and initramfs files....

Going through this, I found it out of date: [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

The config and defaults are a bit different now for tftp-hpa, but I got it working ok searching around the web and trying stuff.

Realized the home router might not be good enough for the DHCP server, and need to support certain DHCP options and BOOTP. Assume I may need to set up NFS share.

I found some more information on another distro's PXE install readme, and I'm going to follow that.

I doubt the entire ISO could be looped with PXELINUX, not sure about GNU GRUB. It seems to have a tftp and pxe module.

Thanks.

---

