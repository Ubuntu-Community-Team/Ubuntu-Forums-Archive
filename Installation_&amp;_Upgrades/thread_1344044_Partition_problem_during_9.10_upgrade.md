---
title: "Partition problem during 9.10 upgrade"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2009-12-02
I made the mistake of upgrading online instead of with a iso file on my laptop.  The display went crazy and I pushed a couple of enters. I later installed the upgrade from and iso cd, then discovered that the partitions were all screwed up.
/dev/sda2  extended 13.04G
  /dev/sda5  linux-swap  629.48M
  /dev/sda7  linux-swap   3.11G
  /dev/sda6   ext3   /     9.32G
/dev/sda1     ext3   /home  285 G

The fstab file is
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=c203ba7c-8c04-4f1c-a126-d0589b972575 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=52f61dbe-f1d4-4b29-8d2b-0537287d3d64 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=d3e88639-9230-4ec6-a168-1bffbafbcaf1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdc5      /mnt/backup     ext3 user,auto 0 0 

# For usb in vitualbox
# none /proc/bus/usb usbfs devgid=126,devmode=666 0 0

I have an external 1T drive with a backup of /home and / minus home and a few others like /proc

How do I rebuild my 320g HD and restore?

---

### Post by oldfred on 2009-12-02
Partitions do not have to be in any specific order. The only issue you have is 2 swaps and the smaller is the one you mount as default. If you do blkid to see your UUIDs you can edit your fstab to use the UUID for sda7 and then delete sda5 if you want. You can add that space to whatever partition is next to it if you desire, otherwise it is a small amount of wasted space.

---

