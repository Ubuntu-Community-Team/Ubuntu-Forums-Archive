---
title: "Grub Installed On Wrong Partition"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by dudemanbubba on 2011-10-19
I upgraded my server yesterday and put 10.04LTS on it from a bootable flash drive.  During the install, I noticed that it indicated it was installing grub onto /dev/sda which I believe was the install flash drive at the time.  Now the machine won't boot without the flash drive plugged in.  I don't want the system relying the flash drive and I was looking for some guidance on how to move the grub from the flash to the main system hard drive.

This server is in another state and I am supposed to be flying out this afternoon...  Any help would be appreciated.

Thanks.

---

### Post by raja.genupula on 2011-10-19
> **dudemanbubba said:**
> I upgraded my server yesterday and put 10.04LTS on it from a bootable flash drive.  During the install, I noticed that it indicated it was installing grub onto /dev/sda which I believe was the install flash drive at the time.  Now the machine won't boot without the flash drive plugged in.  I don't want the system relying the flash drive and I was looking for some guidance on how to move the grub from the flash to the main system hard drive.

This server is in another state and I am supposed to be flying out this afternoon...  Any help would be appreciated.

Thanks.

```
sudo dpkg-reconfigure grub-pc
```
install the grub to your hard disk.
all the best.

---

### Post by dudemanbubba on 2011-10-19
Thank you very much!

---

