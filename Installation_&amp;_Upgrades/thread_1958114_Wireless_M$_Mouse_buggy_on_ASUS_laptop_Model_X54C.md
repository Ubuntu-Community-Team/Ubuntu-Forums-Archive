---
title: "Wireless M$ Mouse buggy on ASUS laptop Model X54C"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-04-13
When running 64 bit Ubuntu 11.04.

This is a very nice new Asus laptop.
Setup a dual boot with Win7 and Ubuntu 11.04.

Plugged in that Wireless M$ Mobile Mouse 3500 and W7 recognized it straightaway and it runs well.

However when switching over and running Ubuntu that same M$ mouse acts buggy and freezes the laptop. Sometimes it can be 'fixed' by using the Asus touchpad, other times I have to reboot and run it till it freezes again.

Question is, is there an easy remedy to fix this so the mouse will run trouble free with Ubuntu?

---

### Post by dummy910 on 2012-04-13
try installing the following:  ```
sudo apt-get install gpointing-device-settings
```  then of course type gpointing-device-settings into a terminal prompt, and you should see your wireless M$ mouse, along with your touchpad... just select-highlight the mouse you want to make adjustments to. 
this is the only software that works on my M$ wireless mouse on my Asus G73 Laptop using an Lubuntu 11.10 install.  peace!

---

