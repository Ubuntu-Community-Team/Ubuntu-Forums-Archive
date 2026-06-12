---
title: "Error: This is not a bootable disk after cloning."
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by z7APXKm on 2018-04-16
[http://paste.ubuntu.com/p/yq9S7cdgdx/](http://paste.ubuntu.com/p/yq9S7cdgdx/)

SO the story is that I bought a 120GB SSD to replace the root (OS) partition on my old 2TB WD disk.  Have cloned just the partition across, leaving the /home partition on the old disk.  (Eventually I would like to reclaim the space from the old /root partition on the old disk).

The grub boot repair tool seemed to want a separate boot partition on the new disk (which didn't exist previously), which I've created at the start of the disk.

I ran the grub boot repair tool to completely reinstall grub and rebuild system files.  It completes quite happily, recognising the fact that there is an install of 16.04 on my new disk.  However when I reboot I get the BIOS level message "This is not a bootable disk. Please insert a bootable floppy and press any key to try again."

I was hoping to avoid a complete reinstall of the OS.  Can anyone offer me hope?

Logs are in the link above.

Thanks for your time.

---

### Post by oldfred on 2018-04-17
This is why it often is just easier to reinstall. Especially if you have a separate /home.

```
 /dev/sda1        [COLOR=#ff0000]bcf49742-2afd-45ba-bf2c-8d696e5b1ed5[/COLOR]   ext4       
/dev/sda3        54c7735e-b714-4f38-8f5c-825d96868f12   ext4       home
/dev/sda5        a6a56937-4a1d-4ab2-9359-ba96ce07be43   swap       
/dev/sdb1        [COLOR=#ff0000]bcf49742-2afd-45ba-bf2c-8d696e5b1ed5[/COLOR]   ext4        


```

You have duplicate UUID, that is not allowed and can lead to major issue if system boots into one, and then into the other. That may depend just on which drive comes up first in BIOS. And once out of sync it become very difficult to repair.

Easier to just reinstall to new partition, restore list of installed apps. And with separate /home partition, you just use it in new install.
But you still should have good backups.

You may be able to change UUID of new partition. Then reinstall grub, edit fstab and find any other places / (root) UUID is used. But if later issues, it is because you missed one.
Some other places that have UUID.
 more /var/cache/debconf/config.dat  | grep /dev/disk
UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid 

      
 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

As to BIOS issue, some BIOS require a boot flag. They must assume Windows as it has to have a boot flag. Grub does not use a boot flag and does not need one.
But just to make BIOS happy add a boot flag to any primary partition.

---

### Post by z7APXKm on 2018-04-18
Your explanation is much appreciated, in the end I came to the same conclusion and reformatted the disk before reinstalling.  I've mounted the old OS at /mnt/oldOS so I can restore what I need.  It's getting there now :-)

---

