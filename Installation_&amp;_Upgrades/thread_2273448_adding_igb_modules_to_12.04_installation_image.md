---
title: "adding igb modules to 12.04 installation image"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by seelig on 2015-04-13
Greetings,

I need a **Ubuntu server 12.04 i386 image**, with **kernel modules for the intel I210 network device**.

```
# lspci -nn | grep Eth
01:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
```

I need the modules during the install process because else the packages which require network won't install.


I found some how-tos on the customization of ubuntu install images, but couldn't get through with any of them, because most reference a **casper** directory which should contain the **.squasfs** files for the initial ramdisk. This directory misses on the old 12.04 image I have and on the newest 12.04.5 image.

Any ideas?

---

### Post by mörgæs on 2015-04-14
Hi, welcome to the fora.

Has the package been added to 14.04.2? How does it work if you try installing this one?

---

### Post by seelig on 2015-04-15
I had it installed because initially I couldn't get the 12.04 image to install. I don't remember if the network did work I'll check this today.

---

