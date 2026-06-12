---
title: "Kernel Panic - not syncing: VFS: Unable to mount ... after ubuntu 20.04 to 22 upgrade"
date: 2022-09-06
forum: Installation &amp; Upgrades
---

### Post by gebbione on 2022-09-06
Today i tried to upgrade from 20.04 to 22 . The process triggered a few errors 

[COLOR=#000000]- converting firefox installation from repo to snap repo failed, got stuck
- upgrading installing usrmerge returned code 1. error installed usrmerge package post-installation script subprocess returned error exit status 1
- installed nvidia-kernel-common-450-server package post-installation script subprocess returned error exit status 1

While i tried to finished the install i saw a few contradicting messages by the installer. First it said that it was going to revert back to previous version but never did. Then said update completed with errors. So i rebooted

Since then i see error [/COLOR]**[Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)]("https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0")**

[COLOR=#000000]
supposed to be fixable as shown here 
[URL="https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0"]https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0
[/URL]but if i try to enter in GRUB options with SHIFT or ESC it does not prompt the menu so I am stuck.

So i thought of running a live install and go and use CHROOT as show here 
[/COLOR][URL="https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd"][COLOR=#000000]https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd
[/COLOR][/URL][COLOR=#000000]but again when i reboot even after updating GRUB and removing the 0 timeout configuration and forcing the menu to prompt i am still not seeing GRUB.

Then i just tried to run the initram upgrade directly using chroot through the live install/usb and here is the error i get.

[/COLOR]
```
[COLOR=#000000]sudo chroot "/mnt/boot-sav/nvme0n1p1" update-initramfs -u -k 5.15.0-47-generic | nc termbin.com 9999
cp: failed to access '/var/tmp/mkinitramfs_8U94J6//usr/sbin/reiserfsck': Too many levels of symbolic links
ln: failed to create symbolic link '/var/tmp/mkinitramfs_8U94J6/sbin/reiserfsck': File exists
cp: failed to access '/var/tmp/mkinitramfs_8U94J6//usr/sbin/reiserfsck': Too many levels of symbolic links
E: /usr/share/initramfs-tools/hooks/reiserfsprogs failed with return 1.[/COLOR]
update-initramfs: failed for /boot/initrd.img-5.15.0-47-generic with 1.
```

[COLOR=#000000]I am currently stuck as I am not sure what to try next. Any suggestions?
[/COLOR]

---

