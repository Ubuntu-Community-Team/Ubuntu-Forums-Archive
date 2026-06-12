---
title: "Graphic Card"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Keldar on 2008-02-24
Hello, 

I have installed ubuntu yesterday but my graphic card : "ASUS EAX1600PRO SILENT"  doesn't work. 
I can't change the screen (i just have 1024x768) and i can't have visual effect on my Desktop.

So if you can help me ... 

Thanks ! :popcorn:

---

### Post by Pumalite on 2008-02-24
You have to install with the Alternate CD and configure your xserver at the end of the installation:
sudo dpkg-reconfigure xserver-xorg

---

