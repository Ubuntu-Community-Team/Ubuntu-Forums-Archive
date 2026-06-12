---
title: "Ryzen + Gigabyte installation problem"
date: 2017-06-01
forum: Installation &amp; Upgrades
---

### Post by sisyphus84 on 2017-06-01
Hi,

I have built system with "Ryzen 7 1700" and "Gigabyte AX370 K3" mobo. The installation for Ubuntu 16/17 fails with the error: "unexpected IRQ trap at vector 07". Also tried Ubuntu 14.04 but that has problem with drivers; even ethernet which is "Killer E2500" doesn't work. Does any version of ubuntu work with Ryzen?

---

### Post by oldfred on 2017-06-01
At the very least you need the newest Ubuntu.
And even then, it may need newer kernel & drivers from a ppa that has the very most recent. But that can even cause issues as not fully integrated with all applications. 

It must work, he says 17.04 worked even without boot parameters:
[http://www.phoronix.com/scan.php?page=article&item=ryzen-1800x-linux&num=1](http://www.phoronix.com/scan.php?page=article&item=ryzen-1800x-linux&num=1)

When new hardware comes out the vendors only support Windows, and not always that well on Windows.
But Linux has to reverse engineer whatever changes are required, add features to kernels & drivers and then those newer kernels & drivers have to be incorporated into a distribution.

---

### Post by sisyphus84 on 2017-06-02
I've tried 16.04/17.04 and both has the same error. Not sure if it is the board or something else but it just hangs on the first boot screen of the live cd installer.

---

### Post by oldfred on 2017-06-02
Older AMD based Gigabyte needed IOMMU off in UEFI and boot parameter, perhaps newer ones also need it?

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)

---

### Post by Dualism on 2017-06-02
Most have reported needing at minimum a 4.10 and above kernel. I have only gotten my Ryzen 1700 to work with my GA-AB350M-D3H-rev-10 (AM4) with a custom compiled 4.11.2 kernel I found here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1671360/comments/160](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1671360/comments/160)

It's stable, and allows for me to turn on SMT. KVM works beautifully on it. Xen will not boot at all (but it's more a grub2 issue I think).

---

### Post by Superdude_123 on 2017-12-06
Just as a quick note for anyone looking at this in the future, you'll need kernel 4.10+ on the system for the Killer 2500 Ethernet to work. For me, that meant manually upgrading the kernel (via a USB stick) with all the required dependencies.

While I am using a different board(Gigabyte X399 AORUS Gaming 7), the Killer 2500 was the same. Also, to get the RAID working, you'll need the AMD RAID controller drivers from AMD ([https://support.amd.com/en-us/download/chipset?os=Linux+x86_64](https://support.amd.com/en-us/download/chipset?os=Linux+x86_64) , I used the files on the ISO).

After reaching out to Gigabyte for support, the official answer I got back was > We appreciate the feedback, however we do not offer full Linux support on our desktop platform products as it is open source. 

---

### Post by wolfgang-rumpf on 2018-07-03
FWIW, I had issues booting Ubuntu 16.0.4 on a Gigabyte AB350-Gaming 3 when I had two graphics cards (both AMD Radeon RX580's) installed.  Nothing but AMD-VI errors on boot.  Each card worked fine separately, but to get both of them to work I had to disable IOMMU in the bios.

> **oldfred said:**
> Older AMD based Gigabyte needed IOMMU off in UEFI and boot parameter, perhaps newer ones also need it?

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)

---

