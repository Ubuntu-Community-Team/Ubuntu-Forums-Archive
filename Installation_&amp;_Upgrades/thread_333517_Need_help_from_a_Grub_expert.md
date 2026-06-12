---
title: "Need help from a Grub expert"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by NobleSavage on 2007-01-07
I have Ubuntu LTS installed on hda6 and I installed Grub to the MBR

I then installed Ubuntu Edgy on hda7 with the alternate disk and did not install Grub to the MBR.

My plan is to install several other distros and chain load them all from one menu, but I have problems now with just these two.

When I try and boot into Edgy from the CLI I get the following:
[HTML]
grub> root (hd0,6)
 Filesystem type is ext2fs, partition type 0x83

grub> kernel /vmlinuz root=/dev/hda7
   [Linux-bzImage, setup=0x1c00, size=0x18db5c]

grub> initrd /boot/int
Error 15: File not found

grub> initrd /boot/initrd.img-2.6.17-10-generic

Error 16: Inconsistent filesystem structure

grub>
[/HTML]

When I try:  grub> configfile (hd0,6)/boot/grub/menu.lst  I get the following:

[HTML]Booting 'Ubuntu, kernel 2.6.17-10-generic'

root  (hd0,6)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x18db5c]
initrd  /boot/initrd.img-2.6.17-10-generic

Error 16: Inconsistent filesystem structure

Press any key to continue...
[/HTML]

When I press a key... then I get a menu and can boot into Edgy on hda7

I'm not sure why I'm getting the filesystem errors? Any ideas?

---

