---
title: "Corrupted kernel image on boot partition?"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by theycallmebruce on 2008-01-07
Hi all.

We had a power failure over the Christmas break. We have an excellent UPS which gives the servers enough time to be shut down gracefully, but this mechanism failed for reasons not relevant to this thread.

As a result of this power failure, there was some file system corruption on our Ubuntu (Feisty Fawn) server.

After running the file system checker on reboot, all seemed well. However, on the next reboot, the system would not boot. Grub complained of a crc error, presumably meaning that the kernel image on the boot partition is corrupted.

Fortunately, after installing the 2.6.20-15 to 2.6.20-16 kernel update last year (via the update manager), backups of the old kernel image were made. Grub was automatically updated to add an entry into the boot menu for the old kernel image, and I can succesfully boot the system using this image.

However, I would like to repair my boot partition by restoring a valid 2.6.20-16 kernel image, preferably in a way which will not confuse future automatic updates. Can anybody suggest what is the best way to approach this?

Thanks!

---

