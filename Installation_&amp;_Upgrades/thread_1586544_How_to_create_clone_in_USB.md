---
title: "How to create clone in USB"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by spandey on 2010-10-02
Hi,
I have Ubuntu 10.04 installed in my desktop and is working fine. I would like to clone the Ubuntu with all my settings etc to a USB Flsah drive so that I can take it with me during travel. 
I don't want to reinstall in USB FLASH rather I want asis Desktop Ubuntu in USB FLASH.

Hope it makes sense.

---

### Post by C.S.Cameron on 2010-10-02
dd will work if the flash drive is larger than the hard drive;
```
sudo dd if=/dev/sda of=/dev/sdb
```
confirm sda is your HDD and sdb is your flash drive.

You might also want to take a look at remastersys.

---

