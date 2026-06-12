---
title: "lost boot partition on drive failure"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by mitomac on 2011-01-01
Greetings,

We had a drive failure on /dev/sda.  Everything 'except' boot was on raid5 across sda, sdb, sdc, sdd.   I know how to repartition a new drive and rebuild the raid etc, but I don't know how to regenerate the files that reside on the boot partition.  I really don't want to re-install as we have lot of custom code and software that may depend on our current libraries and build environment.  Any advice would be appreciated.   

Best,

mitomac

---

### Post by lithopsian on 2011-01-01
/boot contains kernel images, (almost certainly) initramfs images, system maps, and a few other less important kernel boot files.  All these may have to be recovered from the CD although you can also download them.  You will need as an absolute minimum a kernel image (vmlinux) and an initramfs (initrd.img) to boot.  Once you are booted up again, a forced reinstall of your current kernel image package should give you the miscellaneous files.

Most important, /boot contains a grub directory but this can easily be recreated.  Create yourself a good /boot partition and run update-grub to recreate your grub data. From the Live CD obviously :)

Hint for the future: place custom code on a separate partition, something like /opt is often convenient.  Then it is much simpler to do a full reinstall without losing anything hard to replace.

---

