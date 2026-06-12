---
title: "Overwrite Existing Boot Loader with New Install on Different Drive"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by bryansimmons on 2016-10-14
[SIZE=3][FONT=times new roman]Currently have an M.2 drive ([COLOR=#0000ff]/dev/nvme0n1[/COLOR]) with Ubuntu 14.04.  This is the primary drive and second in boot order after the CD-ROM drive.  Have formatted a previously installed backup drive ([COLOR=#ff0000]/dev/sda1[/COLOR]) for 16.04. Would prefer not to install another boot loader program since this already exists on [COLOR=#0000ff]/dev/nvme0n1[/COLOR] but the installation program does not appear to provide that option.  One of the options is to install the 16.04 boot loader on either[COLOR=#0000ff] /dev/nvme0n1[/COLOR] or [COLOR=#ff0000]/dev/sda1[/COLOR].  If installed on [COLOR=#0000ff]/dev/nvme0n1[/COLOR], overwriting the existing boot loader, will this adversely affect the 14.04 installation on [COLOR=#0000ff]/dev/nvme0n1[/COLOR]?[/FONT][/SIZE]

---

### Post by yetimon_64 on 2016-10-14
> **bryansimmons said:**
> [SIZE=3][FONT=times new roman]...  If installed on [COLOR=#0000ff]/dev/nvme0n1[/COLOR], overwriting the existing boot loader, will this adversely affect the 14.04 installation on [COLOR=#0000ff]/dev/nvme0n1[/COLOR]?[/FONT][/SIZE]

No, it won't adversely affect the 14.04 installation (unless there is a serious fault during installation, which can occasionally happen. A backup of the 14.04 install is a good idea in case of such errors though, just in case). 

When installing 16.04 the 14.04 installation will be detected by the os-prober function of the 16.04 grub bootloader and a boot entry will be generated and displayed for the 14.04 install from the new boot screen.

Once 16.04 is installed and you can boot into it, it is very easy to hand back the grub bootscreen to the 14.04 install with a few terminal commands if you have customised the current 14.04 grub screen etc. Or you can just leave it with the 16.04 install as you will have access to both from the new grub boot screen. Cheers, yeti.

Edit: I'm glad oldfred spotted the device numbering I missed in the next post. Don't install grub to a partition. Read the next post carefully please OP.

---

### Post by oldfred on 2016-10-14
You never install grub to a partition.
And with UEFI grub always installs to drive seen as sda. But with NVMe drives it has worked as first or sda drive.
Usually drive order is set by port order. But my M.2 drive (not NVME) was seen as sda, and HDD as sdb.

Best to have SSD as first drive, HDD as second drive, then other drives like DVD, etc. And again port order is important.
I skipped a port and flash drive that was sdf, on reboot would be sdb, with all drives moved up a letter. While system mostly works by UUID, you may use device and then I had to be very careful.
Another system I had SSD, DVD, HDD and while HDD was sdb, it was hd2 in UEFI/grub when manually trying to set parameters to boot ISO. I moved DVD and then had no issues.

If you disconnect an UEFI drive, UEFI forgets all the entries from the ESP - efi system partition on that drive. Most will rediscover if you cold boot a couple of times, but some require you to use efibootmgr to reset entries.

---

