---
title: "Installing 12.04 after Windows 7 --&gt; no bootloader"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by pat13 on 2014-02-11
I have been installing Ubtuntu 12.04 on a maschine with preinstalled Windows 7.

I was following the Ubuntu tutorial for doing so:

    [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

(reduced the disk size, created mepty space on my HD)

I followed the default installation steps ("Install Ubuntu side by side with windows 7"). Everything wnet smooth. However when I had to restart, Windows 7 started directly. There was no bootloader.
It seems like the Ubuntu installation did not install or configure the bootloader correctly.

Did I miss anything?
---
Some extra info:
- My Computer is a Lenovo ThinkCenter M72e, Windows 7 was preinstalled, I erased it and reinstalled (kept the partitions)
- Partitions:
     _- SYSTEM_DRV (1.17 GB, NTFS, System, Active, Primary Partition)
_- C: (345.06 GB, NTFS, Boot, Page File, Crash Dump, Primary Partition) 
_- Lenovo_Recovery (19.53 GB, NTFS, Primary Partition)
_- Free Space was 100 GB, after installation of Ubuntu 12.04 this became:
___- 96.17 GB (EXT4)
___- 3.82GB (Swap)
- I installed Ubtunt 12.04.4, Desktop, AMD 64

---

### Post by sudodus on 2014-02-11
Maybe you installed the bootloader to the Ubuntu partition instead of the head of the drive, **/dev/sda** for the first drive (and no partition number). See these links

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by pat13 on 2014-02-11
Ha, thank you a lot it is fixed with your help!

I installed Boot Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) on a USB-drive with the Linux Live USB creator tool ([http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)), started from the drive and followed the instructions for the "Recommended Repair".

It felt a bit strange to need to copy instructions from the dialog to the terminal, but in the end it all led to the good.

On a general note: why was the Linux installation not able to do this right from the beginning?

---

### Post by sudodus on 2014-02-11
At the partitioning page of the installer, did you selected one of the guided options or 'Something else' to do it manually?

In the guided options, the installer *should* have done it correctly by itself, but there are many manual options, for example to tell the installer to write the bootloader to the wrong place.

---

