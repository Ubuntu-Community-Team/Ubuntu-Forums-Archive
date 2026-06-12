---
title: "Install gone bad - need to fix fstab PLS HELP"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by Joe Ker1086 on 2009-11-28
ok, ill make it short, i have a messed up fstab and need to fix it...i booted into a live cd (fedora) and it is not letting me save the corrections to my fstab. PLEASE HELP! I am so close to fixing this problem and I know what i need to do but cant because it will not save.

---

### Post by Joe Ker1086 on 2009-11-28
ok, nevermind, i got it. This is what I did if anyone else runs into this problem:

[HTML]mkdir /mnt/arch
mount /dev/<root-device> /mnt/arch
mount /dev/<boot-device> /mnt/arch/boot
mount --bind /proc /mnt/arch/proc
mount --bind /dev /mnt/arch/dev
mount --bind /sys /mnt/arch/sys
chroot /mnt/arch[/HTML]

After this

[HTML]nano /etc/fstab[/HTML]

and i was able to edit it. Hope this helps someone.

---

