---
title: "After upgrade, kernel is MIA?"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by Gebstadter on 2008-06-01
Hello all,

I recently attempted to upgrade a Gutsy installation to Hardy through the update manager. This did not work too well. When I boot the machine and hit ESC to get to the Grub menu, the only option available for booting is memtest86+. On probing around inside grub, I see that /boot/ only contains /boot/grub/ and /boot/memtest86+.bin. Neither the old kernel nor the new kernel are anywhere to be found (or else they're lurking somewhere and I just don't know where to look). Is there any better way to fix this than by trying to reinstall Gutsy from a CD?

---

### Post by meierfra. on 2008-06-01
It looks like the upgrade did not finish. Try this

Boot from the Live CD and mount your ubuntu partition. Say it is mounted to /media/disk. Then


```
cd /media/disk
sudo mount -t proc none proc
sudo mount -o bind /dev dev
sudo chroot . 
dpkg --configure -a
```

---

