---
title: "Restore BURG after installation win7"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by Badhon_raj on 2011-07-16
I've searched around but did not get any good tutorial that can explain me hoe to do this. I installed ubuntu 10.10 in hd0,sda7 file system ext4. I installed burg for better ui. Everything was working fine since I reinstalled windows in c: drive (that is hd0,sda1). How can I restore burg? Can any one help me with this?
Thanks in advance.

---

### Post by nzjethro on 2011-07-16
The problem is that Windows has a boot loader/MBR which will override Grub.
To solve the problem, check out [this guide]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") for how to reinstall Grub2 after installing Windows. Then, when Grub2 is in place, reinstall Burg the same way that you installed it in the first place.

---

