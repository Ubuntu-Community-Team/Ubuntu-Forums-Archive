---
title: "HDD i nstall results in 'unable to mount CDROM'"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by epiphiny on 2007-05-06
Hi there,

I'm trying to create a new installation for testing purposes on my computer, but it seems that all my cdrw's are dead, and being a poor student I can't afford any more.

So instead, I've copied the contents of the alternative cd to a partition (it happens to be sdb1), and reconfigured grub to boot from it, so that I have an entry reading

```
title Ubuntu intall
	root (hd1,0)
        kernel /install/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
        initrd /install/initrd.gz
```

This boots, Ok, however I get an error that my CDROM drive cannot be mounted, which I cannot seem to bypass.  As I understand it from the installation wiki, this should be a fine method of installation.

What am I missing?

Many thanks,
james

---

