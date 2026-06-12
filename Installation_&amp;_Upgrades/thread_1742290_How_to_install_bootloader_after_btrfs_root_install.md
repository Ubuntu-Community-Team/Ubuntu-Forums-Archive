---
title: "How to install bootloader after btrfs root install?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by donniezazen on 2011-04-28
Hi,

I did a fresh install of Natty with btrfs / and / home partitions. I used alternate CD. I had to skip bootloader installation. I get grub-rescue screen. If someone can guide me how to install bootloader in this particular case would be great. Thanks.

> As of 11.04-beta1, it is possible to use only btrfs file systems with the caveat that grub _MUST_NOT_ be installed to the boot sector of the btrfs volume containing /boot. See also Ubuntu Grub2 Bug 757446 and Ubuntu Grub2 Bug 759772. You must install it to either the parent (sda rather than sda1; MBR/Reserved Sectors) _OR_ use a dedicated /boot partition as shown in the following example (in Fresh Install on 10.10 Maverick).

Thanks.

---

### Post by Arand on 2011-04-29
I would create a separate /boot partition upon installation in your case...

- arand

---

### Post by donniezazen on 2011-04-29
> **Arand said:**
> I would create a separate /boot partition upon installation in your case...

- arand

I was able to install btrfs on Lenovo S10e flawlessly without /boot partition. Will there be any difference between a non /boot partition and /boot btrfs system?

Thanks.

---

### Post by Arand on 2011-04-29
As far as I know, you will end up getting a grub2 warning which you will need to tap through on each boot, if you don't make a separate /boot.

I would assume that in general it is a bit more fault-proof as well, not to keep all eggs on one basket.

If you want to install grub in the current setup though that should be possible, simply boot a liveCD, chroot into the system and reconfigure/reinstall grub2:```
sudo mount /dev/sdXY -o defaults,subvol=@ /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
## Or more consisely: for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/$i;  done

sudo chroot /mnt

dpkg-reconfigure grub-pc
## Select sdX
exit
```e.g. if main disk is sda, and btrfs / is on sda5, substitute X=a Y=5

- arand

---

