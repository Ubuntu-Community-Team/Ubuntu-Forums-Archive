---
title: "The disk driver / is not ready yet or not present"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by hindozaid on 2011-05-20
Hi,

I was upgrading to Ubuntu 11.04 and the laptop turned off.
Once I rebooted, I got this Message :
```
The disk driver for / is not ready yet or not present 
continue to wait; or press S to skip mounting or M for manual recovery.

```

My laptop Model: Toshiba Satellite A200.

Thanks in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-20
take a live USB installation of Ubuntu 11.04 and boot from that.. 

That upgrade got borked.  It happens sometimes. 

You may be able to repair it, but at least for now you can back it up.

---

### Post by hindozaid on 2011-05-20
Thanx a lot for your reply, 

I booted live now but how to repair?

---

### Post by hindozaid on 2011-05-20
any suggestions?
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=836efee4-2fc1-4f68-91a2-9f836a906ce5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=134d1bdd-9944-4269-8b86-dbe7737eed98 none            swap    sw              0       0
```

---

