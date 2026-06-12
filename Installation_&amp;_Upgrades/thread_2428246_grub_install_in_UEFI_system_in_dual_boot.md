---
title: "grub install in UEFI system in dual boot"
date: 2019-10-01
forum: Installation &amp; Upgrades
---

### Post by jacopastorius82 on 2019-10-01
hi all. I have windows 10 installed with 100 Mb efi partition detected by the partition manager in the ubuntu 18.04 installer. During the partitioning, while installing ubuntu, I installed grub in that partition which has the correct boot efi flag. At the first boot grub loaded correctly showing me ubuntu and windows, but after entering windows, grub does not appear anymore and windows starts.
What could be the issue? thank you

---

### Post by ubfan1 on 2019-10-01
You should be able to select ubutnu (grub/shim) from the EFI menu (some function key/esc/del/... key at power-up) to select the boot device/os.  Look at the boor order from a terminal with the command  sudo efibootmgr -v , and change it to put the default you want first in boot order.

---

### Post by jacopastorius82 on 2019-10-01
I reinstalled grub with these
```

sudo mount /dev/sdXXX /mnt
sudo mount /dev/sdXX /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdX
update-grub  
```
and grub loaded correctly at reboot. But booting windows again made grub disappear again

---

### Post by oldfred on 2019-10-03
What brand/model system?

Some only save changes made to boot order from inside UEFI, not from efibootmgr. 
Grub uses efibootmgr to change & install grub to UEFI and that works for most systems.

Some users with HP have reported that updates to UEFI resolved issue also.

---

