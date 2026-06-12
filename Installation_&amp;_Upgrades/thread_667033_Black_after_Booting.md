---
title: "Black after Booting"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by i.gerardus on 2008-01-13
Hi

I wish to install ubuntu onto my pc, but after the welcome screen where I select to start and install it, the kernel loads to full, and then the screen goes blank and my monitor switches off. When I switch my monitor back on, it is stall all black. 

I have installed ubuntu on my computer before, just with a different disc, and it worked fine. SAdly I had to remove it as my universities' computer network doesnt support ubuntu. Now they do though!. I downloaded a copy ubuntu and burned it as an iso file.

I am using the 64bit version of ubuntu

Here are my pc specs: AMD64 3500+, 120GB SATA, 1GB RAM, RADEON X800GTO

Thanks

---

### Post by zvacet on 2008-01-14
Did you cheked [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) an disc for errors?If everything is O.K. then 
Ctrl+alt+F2

```
sudo dpkg-reconfigure xserver-xorg
```

When you comes to drivers select **vesa** and continue to the end.Restart and you should have basic graphic.After that find driver for your card (restricted manager or something similar,because I don´t use english version).

---

