---
title: "Edit cfg files from live cd"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by futureman on 2007-02-23
First off I'm running kubuntu 6.10 32bit, I was installing nvidia-glx drivers for my GeForce4 Ti 4200, I installed it from adept, then changed my xorg.conf from nv to nvidia, then when i restarted my computer the nvidia logo popped up and the the screen went blank. Currently I'm running from the livecd and would like to know how to get into my xorg.conf file from the livecd environment so I can change it back to nv, I beleive I need to mount the hard drive but don't know how to do this, Then I'll keep trying to get these nvidia drivers to work.

---

### Post by taurus on 2007-02-23
From a terminal, do

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming / is on /dev/hda1)
kdesu kate /mnt/ubuntu/etc/X11/xorg.conf
```

---

### Post by futureman on 2007-02-23
thanks for the help, it was hdb1, any pointers for getting my nvidia drivers set up?

---

### Post by taurus on 2007-02-23
You can try this guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

