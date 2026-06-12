---
title: "Tripple-boot with Windows 10 and Mint 17.3"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by zachif on 2016-03-03
I have a desktop with a single 250GB SSD, running dual-boot windows 10 and Mint 17.3.
Windows takes approx. 120GB, and Mint another 30-40GB, I was trying to install Ubuntu 15.10 (64-bit) on a 20GB ext4 partition created in the unused area of the SSD.
Everything went smoothly, until rebooting...
Now, I only have Mint and Ubuntu.  Windows 10 is gone :(
I have tried 'sudo update-grub' (found in a seemingly relevant thread) - but that did nothing to resolve my issue...

HELP please.... :(

---

### Post by grahammechanical on 2016-03-03
The command sudo update-grub would have produced a printout to screen that would have listed all the OS found by Grub os-prober. Did the list include a boot loader for Windows?

Regards.

---

### Post by zachif on 2016-03-03
More info on my partitions, etc:
[http://paste2.org/99EyPUkO](http://paste2.org/99EyPUkO)

---

### Post by zachif on 2016-03-03
> **grahammechanical said:**
> The command sudo update-grub would have produced a printout to screen that would have listed all the OS found by Grub os-prober. Did the list include a boot loader for Windows?

Regards.

$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-32-generic
Found initrd image: /boot/initrd.img-3.19.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Windows Recovery Environment (loader) on /dev/sda1
Found Ubuntu 15.10 (15.10) on /dev/sda8
done

---

### Post by oldfred on 2016-03-04
Grub has not been updated to find Windows 10.
It goes thru all known versions and if no match calls it "recovery".

---

