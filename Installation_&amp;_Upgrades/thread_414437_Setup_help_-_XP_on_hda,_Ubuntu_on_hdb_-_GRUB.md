---
title: "Setup help - XP on hda, Ubuntu on hdb - GRUB"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by benzooor on 2007-04-19
So I'm attempting to install ubuntu on my secondary hard drive which had previously been used only for data storage.

I started by defragging to get all the existing data at the front of the disk, resized my NTFS partition, created a 15GB ext3 partition, a 2GB (I have 1GB ram) swap partition, and a 8GB FAT32 partition to share;

All this was fine and dandy, installed ubuntu on the ext3 partition.  Now, I was somewhat following the guide on linuxdevcenter ([http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3")), and therefore didn't write grub to the HD, but was supposed to write it to the LINUX partition.

Well, I goofed and accidently isntalled it to /dev/hdb4 (the share partition);

After following the rest of the instructions, using
```
# dd if=/dev/hdb2 of=/mnt/share/ubuntu.bin bs=512 count=1
```

to create an UBUNTU.BIN file on the share drive which I then copied to the C:\ drive in windows and pointed my BOOT.INI to.

When attempting to boot to it, I got a blinking cursor, realized my mistake, and then used the system rescue CD to install grub on /dev/hdb2;

I used the same code to create another UBUNTU.BIN; and now encounter the following error when attempting to boot it;

```
GRUB:Geom_error
```

Any suggestions on how to get this to work?  My goal is to have a menu displayed on startup which would allow me to choose linux or windows.  If I install GRUB to my primary hda, will it be able to see my linux partition on hdb?  If so, how would I go about setting that up?  Also, should I install GRUB from the ubuntu live CD or the system rescue  CD?  Does it even matter?

Thanks in advance,
Ben

---

### Post by benzooor on 2007-04-19
bump?  Any ideas?

---

