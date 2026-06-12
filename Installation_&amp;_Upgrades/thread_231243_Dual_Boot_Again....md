---
title: "Dual Boot Again..."
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by PCalitrack on 2006-08-07
Hey all,

I am trying to switch from Mandrake to Ubuntu on a dual boot Windows XP system.  My Windows has been installed for a long time, and there is currently a LILO bootloader that runs when I boot up my computer. What I am wondering is if the Ubuntu installation will correctly support my dual-boot and override the current bootloader with a new one for Ubuntu while keeping Windows XP intact. I have read all kinds of articles on setting up an Ubuntu dual boot with Windows and they all have this wierd quark where they don't install grup on the MBR... or something like that. They put it on a floppy and then do something with it later. Will Ubuntu automatically set up my bootloader to do what I want without having to do all that random mumbojumbo in these dual-boot tutorials.

---

### Post by OpsVentus on 2006-08-07
Ubuntu install will look for other OS'es on your system. You have to watch out to install Ubuntu on the correct partition.
You can tell Ubuntu to put Grub on the MBR, this is default(I think).
But there is a chance that Ubuntu doesn't find your Windows install. In that case you will have to do some mumbojumbo to get it right.

Cheers,
Bart.

---

### Post by PCalitrack on 2006-08-07
As an update, Ubuntu successfully installed as a dual boot on my Dell Inspiron 9100. GRUP configured itself correctly and everything. The install program did it all. I'm glad I didn't have to mess with any of that stuff. Thanks.

---

