---
title: "Ubuntu Multiboot using YUMI"
date: 2018-11-28
forum: Installation &amp; Upgrades
---

### Post by fishermedders on 2018-11-28
I had a rather simple question, that is that when you 'burn' Ubuntu (in my case 18.04 Desktop) onto a USB Drive through YUMI, it treats Ubuntu like an installation version of Ubuntu, showing the screen with the options Try or install, etc. Is there a way to install ubuntu onto the flash drive so I boot into a setup ubuntu instead of the installer ISO?

Thanks,
Fisher.

---

### Post by sudodus on 2018-11-29
Yes, in two steps. This is easy, if you use two USB pendrives, and difficult if you use one single pendrive. Since basic pendrives are cheap, I suggest that you use one basic pendrive (maybe a USB 2 pendrive with 4 or 8 GB), and one fast USB 3 pendrive. See this link,

[FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

Install Ubuntu into the basic pendrive with YUMI, Rufus or some other tool in Windows or with the Ubuntu Startup Disk Creator, Disks or mkusb in Ubuntu.

Boot from the basic pendrive and install Ubuntu into the fast USB 3 pendrive. The following link may help,

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

### Post by fishermedders on 2018-11-29
Will this solution play nice with the YUMI multiboot?

---

### Post by sudodus on 2018-11-29
**The installed system will be independent of the YUMI system** (and will be installed in another drive).

What I suggest is to

- create a single boot or multi boot pendrive with YUMI

- boot from this pendrive and run Ubuntu

- install Ubuntu into the the other pendrive. (The result will be an installed system in the other drive, installed like into an internal drive, but in the other pendrive.)

---

### Post by C.S.Cameron on 2018-11-29
YUMI is nice because the BIOS only version can have multiple OS, each with it's own unlimited, (>4GB), persistence file.

A better Multi Boot option* is to use a flash drive with a GPT partition table with multiple partitions, (>8GB each), and do a Full install of an OS to each partition.

The Ubuntu based OS's can even share a common Home partition if desired by listing the /home partition path in each OS's fstab. (Best to use custom wallpaper when sharing /home)

*Full installs are more stable than persistent installs and can be updated and upgraded.

For details See [https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083812#1083812)

Simpler BIOS only Full install Multi Booter: [https://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/1076379#1076379](https://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/1076379#1076379)

---

