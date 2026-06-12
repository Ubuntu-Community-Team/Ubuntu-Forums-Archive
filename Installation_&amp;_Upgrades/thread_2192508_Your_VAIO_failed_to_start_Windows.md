---
title: "Your VAIO failed to start Windows"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by joachimlefever on 2013-12-08
Hi everyone

I'm trying to install Xubuntu 13.10 but it keeps failing.
First I want to say that I'm new to Linux, so please keep that in mind when trying to help me.
I am NOT trying to create a dual boot setup. I only want Xubuntu 13.10.

I downloaded Xubuntu 13.10 and created a bootable USB stick following this guide: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
I installed Xubuntu with default partitions.

When I boot I always get this: [http://i.imgur.com/Blm6Ocn.jpg](http://i.imgur.com/Blm6Ocn.jpg)

I did:
```
sudo mount /dev/sda2 /mnt
```

```
sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/run /mnt/dev/run && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
```

```
sudo chroot /mnt
```

```
update-grub
```

```
sudo nano /etc/default/grub
```

Change:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Into:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=noncq"
```

```
update-grub
```

Rebooted & still the same problem...

---

