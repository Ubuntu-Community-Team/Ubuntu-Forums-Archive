---
title: "Installing Grub with / on raid1"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Pigeon. on 2010-12-05
Having just had terrible problems doing the above I think I should write down how I eventually sorted it for the world before I forget :)

Situation: a fresh **installation** (not "install", as people so illiterately tend to write these days - "install" is a verb, there's no such thing as "an install") of Xubuntu 8.04 hardy (yes, I know that's old to be installing now, but on later versions I found that I couldn't set up imwheel / couldn't get redshift to work / couldn't switch VTs with Ctrl-Alt-Fn / had the system lock up completely as soon as it started X, so I gave up and went back to the last one that did work...)

...A fresh installation of Xubuntu 8.04 with / on a software raid1 set /dev/md3. The installer failed to install grub, so I had to install lilo instead - that worked, but the boot process would drop to an initramfs shell after failing to mount /dev/md3 on /root with "device or resource busy", and it was necessary to mount it by hand to continue to boot. So I wanted to install grub...

grub-install failed to work, reporting "The file /boot/grub/stage1 not read correctly".

Entering "find /boot/grub/stage1" from the grub shell resulted in "Error 15: File not found".

To fix this I did the following - not sure if all steps are necessary, but it's working now...

/dev/md3 consists of two drives, /dev/sdi and /dev/sdj.

- Edit /etc/fstab and replace the UUID reference for / with /dev/md3

- Delete /boot/grub/default and /boot/grub/device.map, then run update-grub

- Start the grub shell

grub> device (hd0) /dev/sdi
grub> root (hd0,0)
(response: Filesystem type is ext2fs, partition type 0xfd)
grub> setup (hd0)

This worked.

If I was going to pick one bit as the crucial step it'd be "device (hd0) /dev/sdi".

Hope someone finds this useful :)

---

