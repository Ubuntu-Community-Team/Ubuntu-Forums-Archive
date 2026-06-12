---
title: "Adding 3rd OS to dualboot"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by tubos2 on 2014-06-27
- I have a win7 / ubuntu dual boot desktop system with grub2.

- I would like to add ubuntu server as a 3rd system on another partition on that disk.

- how would i go about installing so that it also shows up in the grub menu?

---

### Post by papibe on 2014-06-27
Hi tubos2.

I triple boot my laptop (Windows7/Trusty/Precise).

It is really simple if you are going to install another distro from the Ubuntu family:

Make the necessary space with gparted, and install the server version (careful to not to overwrite other partitions!). The last step of the installation would be to install grub. You have 2 options here: you could install it from the server installation process (this would probe current OSes), or..

I'd recommend you skip that, and after installing the server edition, boot into the desktop and run:
```
update-grub
```
this would probe the disk for all OSes and will include the server on the grub menu. Also, this way you won't take the risk of installing an older version of grub (even though it would probably be updated later while upgrading your server).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by tubos2 on 2014-06-27
Thx , I'll try it out tomorrow and will report back :)

---

### Post by tubos2 on 2014-06-28
It worked but i now have double entries for my ubuntu desktop in grub.
How can I remove 1 entry?

---

### Post by yancek on 2014-06-28
Did you install the Ubuntu server, then boot to your Desktop install and run update-grub?  Are you sure there are 2 duplicate entries and not a different kernel or a 'recovery' mode entry?  I'd verify that before deleting an entry.

---

