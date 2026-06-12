---
title: "I'm upgraded now, but without a GUI"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Spoken on 2008-05-27
so i upgraded from 7.04 to 7.10 last night, but when it got to the final step and restarted and rebooted.  It pulled me into what looks like "dos mode" or command lines. and said the following output.
===============================
kinit: No resume image, doing normal boot...

Ubuntu 7.10 dell tty1

dell login:

================================

i assume my upgrade isnt detecting the restricted drivers for my intel media accelorator 3100x (which is blacklisted)

so what do i need to run in the command line to install the restricted drivers?

---

### Post by zvacet on 2008-05-28
After login type 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select **vesa** driver which will give you basic graphic and after that you can go for your video card driver.

---

