---
title: "install kubuntu on ubuntu"
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by leongor on 2005-10-31
I have clear installed ubuntu 5.10. I tryed to install apt-get install kubuntu-desktop and after installation and rebooting I have black screen and consol login. KDM I choose earlier, but after rebooting I saw only KDE login screen and GDM loading process and crash of xserver. Rebooting not help me. 
In hoary I installed kubuntu the same way and have't any problems. How can I fix this problem?

---

### Post by frodon on 2005-10-31
Have you installed both KDM and GDM ?

---

### Post by leongor on 2005-10-31
Yes, and I choose KDM as default.

---

### Post by frodon on 2005-10-31
You could try a : ```
sudo dpkg-reconfigure kdm
```I'm not sure it helps

---

