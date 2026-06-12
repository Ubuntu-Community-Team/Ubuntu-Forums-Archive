---
title: "dual booting with PCBSD"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by geovino on 2010-02-23
The new PCBSD 8 came out and I wanted to dual boot with Ubuntu 9.10.

I'm using parted magic to resize the hdd and give PCBSD a 96 gb partition. I don't know what file system it uses but I figure once I point it to the new partition it will format it and install. 

Since I want to use the Ubuntu grub for the boot loader I was told not to check off the PCBSD bootloader during the install. 

How do I list the PCBSD in the sources.list so Ubuntu still boots up first and lists PCBSD as the second choice?

---

### Post by oldfred on 2010-02-23
I just did a quick google search and found this site on ver7

[http://www.osnews.com/story/20351/Review_PC-BSD_7](http://www.osnews.com/story/20351/Review_PC-BSD_7)

It says it must be a primary partition and uses grub. Does the newer version still use grub legacy? If so I would consider installing grub legacy to the PBR partition boot sector and chainbooting. The ZFS format may confuse any direct booting??

---

### Post by geovino on 2010-02-23
> **oldfred said:**
> I just did a quick google search and found this site on ver7

[http://www.osnews.com/story/20351/Review_PC-BSD_7](http://www.osnews.com/story/20351/Review_PC-BSD_7)

It says it must be a primary partition and uses grub. Does the newer version still use grub legacy? If so I would consider installing grub legacy to the PBR partition boot sector and chainbooting. The ZFS format may confuse any direct booting??

I edited the /boot/grub/menu.list and it was empty. I added the PCBSD entry to it. I'll reboot in a while and see if it works. Thanks. :)

---

