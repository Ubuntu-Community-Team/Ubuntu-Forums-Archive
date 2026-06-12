---
title: "GRUB error after inital install"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by neptune on 2006-10-14
Hi all,

My hard drive setup:

1x 200 GB IDE (hda)
1x 160 GB SATA (sda)

Motherboard considers IDE drives primary an SATA secondary.
BIOS has boot order configured to use SATA drive first, then IDE drive next.

During installation, there were no errors or unsual activity - everything went smooth.

Upon initial boot after installation, I get the following message: **"Error 17: Cannot mount selected partition"**

I believe GRUB is installed on MBR of hd0 (which is the IDE drive I think). 'root' is root (hd1,0).
I'll write down the entire boot up screen in a day or two.

I'd appreciate some help in getting my system up and running.

Here's my partition scheme:

```

sda1 - primary -  ext3 -  100 MB - /boot (bootable flag)
sda2 - primary -  ext3 -    5 GB - /
sda5 - logical -  swap -  750 MB - swap
sda6 - logical -  ext3 -   20 GB - /backup
sda7 - logical -  lvm2 - 30.5 GB - vg_linux_01   (lvm group)

hda5 - logical -  lvm2 -   10 GB - vg_linux_02   (lvm group)
hda6 - logical -  lvm2 -   65 GB - vg_storage_01 (lvm group)

vg_linux_01    -  ext3 -   10 GB - /home
vg_linux_01    -  ext3 -   10 GB - /opt
vg_linux_01    -  ext3 -   10 GB - /usr
vg_linux_01    -  ext3 -  512 MB - /tmp

vg_linux_02    -  ext3 -   10 GB - /var

vg_storage_01  -   xfs -   35 GB - /srv
vg_storage_01  - fat32 -   30 GB - /fatty

```

Thanks!

---

### Post by Kateikyoushi on 2006-10-14
Yes it might have installed grub on the PATA drive.

There is a bug on launchpad about it, see if it applies to you and the whether their solution works.
[LINK]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497")

---

### Post by neptune on 2006-10-14
Interesting... if I boot off the Ubuntu LiveDVD, how can I change that device.map file to have the correct settings (if that is the real issue)?

I imagine that booting from the LiveDVD may not have the same /boot mount point as on the local hard drive?

---

