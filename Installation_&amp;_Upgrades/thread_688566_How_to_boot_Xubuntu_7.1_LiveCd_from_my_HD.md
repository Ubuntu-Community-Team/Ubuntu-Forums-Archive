---
title: "How to boot Xubuntu 7.1 LiveCd from my HD ???"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Martinfdf on 2008-02-05
Hi Im new with Ubuntu (but not with linux). I have an old machine so I decided to try Xubuntu.

Sorry for my english I prefer spanish!.

I would like to know how to boot Xubuntu Livecd but from my hd instead of burning the iso image that I downloaded and booting from the cd.

I understand that into the live cd there's a squashfs file. I have grub installed and I have copied all the contents of the iso image to an ext2 fs called in hda2 but I dont know how to load that squash fs file that is in "/hda2/casper/filesystem.squashfs".

Can anyone help me and tell me how to edit my grub configuration for booting from the hd ???

THIS IS MY MENU.LST (edited by me, but its wrong !!!):
------------------------------------------------------------------------------------
title Xubuntu Linux

root (hd0,1)
kernel /casper/vmlinuz root=/dev/ram0 looptype=squashfs loop=/casper/filesystem.squashfs udev nodevfs cdroot=/dev/hda2

initrd /casper/initrd.gz

-------------------------------------------------------------------------------------
thank you. 

regards martin

---

