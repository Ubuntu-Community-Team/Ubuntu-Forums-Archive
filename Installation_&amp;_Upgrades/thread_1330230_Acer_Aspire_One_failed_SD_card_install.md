---
title: "Acer Aspire One failed SD card install"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by alanwalterthomas on 2009-11-18
I thought I had done everything right, but when I reboot I see grub loading & then a message about cannot find the UUID that corresponds to the sd card (/dev/mmcblk0p1 ,my 2GB sd card) then I see the xubuntu mouse logo for ~25 seconds, then a blank screen. REISUB works to reboot so I guess the kernel loaded at least.
I have the AAO with the 16 GB ssd & 1 GB of ram, originally with Linpus lite
I had attempted the follwing:
/boot on SSD
/home on SSD
swap on SSD
/ on SD

From liveusb after installation

sudo mousepad /etc/initramfs-tools/modules
ADD:
mmc_core
mmc_block
sdhci
sdhci-pci

sudo /usr/sbin/update-initramfs.distrib -u

Mount / (SD) & /boot (SSD)

sudo cp /boot/initrd.img-* /media/SSDmountpoint/

sudo mousepad /media/SDmountpoint/etc/initramfs-tools/modules
ADD:
mmc_core
mmc_block
sdhci
sdhci-pci

Then I restarted & went nowhere.

I booted in recovery mode & by taking pictures of the screen managed to capture some possibly informative messages:
...
Begin: Loading essential drivers... ...
[###] sdhci: Secure Digital Host Controller Interface driver (so I think the driver loaded, although I didn't see sdhci-pci in the list)
[###] sdhci: Copyright(c) Pierre Ossman
...(The root filesystem was mounted.)
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system waith for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/(the uuid for the sd card) does not exist. Dropping to a shell!

Now I'm at initramfs. I tried ls /dev/disk/by-uuid & the SD card's UUID wasn't among them, nor was mmcblk0 in /dev/. Any ideas about why adding those mmc modules didn't work? 

Thanks for any help!

---

