---
title: "Blocked by the current security policy"
date: 2018-08-31
forum: Installation &amp; Upgrades
---

### Post by OiPenguin on 2018-08-31
Hi,

After a regular update of my 18.04 installation on a Lenovo Yoga 720 I was suddenly greeted at boot with an error saying *Ubuntu has been blocked by the current security policy*. I've used ours to trouble shoot, including using boot-repair both in automatic and advanced mode with different settings, plus attempted to do it manually and attempted to install rEFInd without succcess. I desperately need help to restore my system and hope someone may be able to help based on the boot-repair output to pastebin:
[http://paste.ubuntu.com/p/JNJzMX99cF/](http://paste.ubuntu.com/p/JNJzMX99cF/) 

Thanks,

Lars

---

### Post by OiPenguin on 2018-08-31
Problem solved. My solution was to make a new small partition before the uefi-partition. With boot-repair, I was able to install Grub2 on that partition. I hope it keeps working. I need a few updates and reboots over the coming weeks to trust my system...

---

