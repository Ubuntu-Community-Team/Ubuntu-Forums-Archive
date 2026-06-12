---
title: "GRUB error, No such partition!"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by stormforce133 on 2011-06-17
Hi!
This is my scenario:
Internal HDD removed, broken.
External 500GB (USB) HDD:
/sda1         ntfs (only data, no OS)
/sda2         extended
  -sda5       /boot       100mb
  -sda6       /             12gb
  -sda7       swap        2gb

I get GRUB error while booting, i've tryed grub-update, but i get the same error always. Also tryed with otrer distros (Fedora, Mint)
Any advice?

PD: I've installed Ubunut AFTER removing the internal HDD.

Thanks!

---

### Post by mister_playboy on 2011-06-17
Could you tell us exactly what error GRUB gives?

---

### Post by oldfred on 2011-06-18
The update-grub only works to rewrite menu on a working system. You may need to reinstall grub2's boot loader to the MBR.

But you have a separate /boot. Many instructions leave off the extra mount you have to do with /boot or just have it as a foot note.

to reinstall grub2 with the livecd:
$sudo mount /dev/sda6 /mnt
$sudo mount /dev/sda5 /mnt/boot  
sudo grub-install --root-directory=/mnt/ /dev/sda

If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda

---

