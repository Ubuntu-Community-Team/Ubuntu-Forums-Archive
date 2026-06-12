---
title: "Windows 7 has wiped out  MBR"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by khalid.A on 2010-06-03
I've installed ubutnu 10.04 (dual booting, windows 7 installed first). I just created a new partition for ubuntu and then installed it, and everything worked fine. Now, whenever I start Win7, I find that the MBR is overwritten by Win7. To fix it, I need to boot from ubuntu live cd and do the following to recover it.
```
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sda
```
This recovers GRUB but once I start Win7, Win7 wipes off the MBR again. I hate booting from ubuntu live cd to write the commands each time to recover GRUB. Any solution will be appreciated.

---

### Post by darkod on 2010-06-03
This seems to have a fix if you have Dell:
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

There is some stupid Dell piece of software that deletes part of grub2 every time windows is run.

I have seen HP machines also doing that, don't know if the same type of fix can help if you have HP.

PS. And since you already know that your root partition is /dev/sda5, from live mode you can reinstall grub2 with only:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by khalid.A on 2010-06-03
Thank you darkod for helping me. I've just deleted Dell Data center and now Win7 doesn't eat the MBR. Therefore, for everyone who bought a new Dell computer, you need to uninstall the Dell Data center to keep yourself from losing the boot loader.

---

