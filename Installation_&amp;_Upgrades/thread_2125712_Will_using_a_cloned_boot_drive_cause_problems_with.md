---
title: "Will using a cloned boot drive cause problems with my bootloader?"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by Nightmist on 2013-03-14
Hello,

I got a new SSD disk in the mail today. I will attempt to clone my dual boot drive (Ubuntu and Windows 7). Will this work nicely with GRUB?
I'll try to follow this guide, but it doesn't take into account that I'm using GRUB: [http://www.howtogeek.com/97242/how-to-migrate-windows-7-to-a-solid-state-drive/](http://www.howtogeek.com/97242/how-to-migrate-windows-7-to-a-solid-state-drive/)

Thanks.

---

### Post by oldfred on 2013-03-15
Are you going to replace current drive?

IF not you will have issues of duplicate UUIDs. Not sure what issues Windows may have. With Ubuntu it is often easier just to reinstall, so you have a clean updated system. 
But you can change UUIDs, edit fstab and reintall grub2's boot loader to get UUIDs fixed. There are also a couple of other settings somewhere that may also need updating.

 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by darkod on 2013-03-15
I would suggest copy instaed of clone. You create the partitions on the SSD first (the partitions will not have the same size as on the HDD I assume since SSDs are quite smaller) instead of cloning them.

With this step you avoid having duplicate UUIDs even if both the ssd and hdd stay in the computer.

I would copy windows partition from ubuntu live mode too, although ntfs doesn't use ownership and permissions the way linux does, but still it doesn't hurt I think. Use the cp -ax to keep ownership and permissions which is a must for the ubuntu partitions.

After you have copied all, I think windows should work fine. For ubuntu you will have to adjust the UUIDs in /etc/fstab (on the ssd of course) and it's better to enter the installation with chroot to do update initramfs and grub2 reinstall. That makes sure it "gets" the idea it's on a new disk.

If it fails, you still have your original data on the hdd. Never delete it until you see things are working with the ssd for sure.

---

