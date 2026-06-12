---
title: "MBR Issue"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by DeepSix on 2008-02-05
I'm unsure if this is the correct forum as a disclaimer. Anyway attempting to dual boot Vista/Ubuntu. Started with Vista because it seemed simpler as GRUB just makes itself the bootloader after you install ubuntu, rather then having to reinstall GRUB if you go ubuntu first. So I go along with it, Vista loads smoothly. Go ahead and install ubuntu: doesn't see either OS(no GRUB error). Shruged it off and formated/deleted both partitions via Vista boot cd. Reinstall Vista: "bootmgr is missing". A note although I can not predictively reproduce this, I know theres two instances of Vista in the MBR, one is bootable and one is not, as I said this is not predictively reproducible.

So right now my goal is to delete everything(including the MBR) off the drive and start all over again, problem is I don't know how to do this. Is there a better way?

---

### Post by yabbadabbadont on 2008-02-05
If you really want to wipe the drive and start over, then boot a live CD or DVD and run:
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```

THIS WILL OVERWRITE THE MBR AND THE PARTITION TABLE!

You will, of course, have to replace /dev/hda with the correct device for your drive.

---

### Post by Pumalite on 2008-02-05
You can also get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete everything in your hard drive. Make 2 new partitions. The first for Vista (sda, at the beginning of the drive), formatted ntfs. A second partition for Ubuntu, format it ext3 if you want. Install Vista first. Ubuntu last. Let Grub install to MBR

---

