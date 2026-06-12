---
title: "Unbuntu 10.4 wont boot after disconnecting optical drive!"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by nickspider on 2010-08-24
Running Ubuntu 10.4, loaded it with external optical drive, everything works fine with the cd/rom still attached (no cd in it) but when I disconnect it, it no longer boots. I've made sure the boot order is correct. It stops after the bio screen, Ubuntu screen never comes up, stalls at blank screen with flashing cursor in upper left. If I reconnect cd/rom it works fine.
Let me know what other information would be helpful.
Thanks for your time!

---

### Post by walterav on 2010-08-24
> **nickspider said:**
> Running Ubuntu 10.4, loaded it with external optical drive, everything works fine with the cd/rom still attached (no cd in it) but when I disconnect it, it no longer boots. I've made sure the boot order is correct. It stops after the bio screen, Ubuntu screen never comes up, stalls at blank screen with flashing cursor in upper left. If I reconnect cd/rom it works fine.
Let me know what other information would be helpful.
Thanks for your time!

Any master/slave jumpers on the disks if IDE?

---

### Post by nickspider on 2010-08-24
It is a sata cd/rom. I have no raid array one single 1 tb drive. Which is also sata.

---

### Post by nickspider on 2010-08-25
**BUMP** 
I cannot figure this out. I have tried everything I can think of, someone please help me!
If you need more info let me know!~

---

### Post by ronparent on 2010-08-25
Go ahead and boot into your sytem with the optical drive plugged in. Go to this site and download the bootinfo script: 

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Run it and post the output here. This should tell us what you have to do next.

---

### Post by techxcell on 2010-08-25
> **nickspider said:**
> **BUMP** 
I cannot figure this out. I have tried everything I can think of, someone please help me!
If you need more info let me know!~

Post here the contents of your /boot/grub/grub.cfg please.

---

