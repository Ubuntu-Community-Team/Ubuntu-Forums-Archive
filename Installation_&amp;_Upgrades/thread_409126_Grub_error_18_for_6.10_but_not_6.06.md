---
title: "Grub error 18 for 6.10 but not 6.06"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by andy gee on 2007-04-14
I have an old beige box, 440MHz and 128Mb RAM. I installed Xubuntu 6.06 on it a while ago. I decided to reinstall with 6.10, and at the first boot up I got a Grub error 18 ('Selected cylinder exceeds maximum supported by BIOS'). Tried installing Puppy Linux, same problem. Tried reducing hda1 partition size - this got me a grub error 17, ('This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB') so there was probably some problem with grub finding the partition. Reinstalled 6.06, no problem. 

I found a way to get over this by creating a boot partition at [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB) but I want to know if there's a way to install 6.10 without doing that, and also why 6.06 seems to be able to do this but not 6.10?

---

