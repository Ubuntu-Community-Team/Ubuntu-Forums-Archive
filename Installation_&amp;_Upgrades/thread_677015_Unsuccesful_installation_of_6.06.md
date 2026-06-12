---
title: "Unsuccesful installation of 6.06"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by Holy-Fire on 2008-01-24
Hi. I've tried to install Ubuntu 6.06 Desktop i386. During the installation I get the message "Failed to start the X server (your Graphical Interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?". Answering "yes" seems to just give me some information about the version I am using.
Does anyone know what the problem is?
I am using ASUS P5B-V with an Intel Core 2 Duo E4500.
Thanks.

---

### Post by PmDematagoda on 2008-01-24
What is the VGA card that you use?

---

### Post by Holy-Fire on 2008-01-24
I'm using the motherboard's integrated VGA card - "Intel Graphics Media Accelerator X3000". The chipset is Intel G965.

---

### Post by zvacet on 2008-01-24
Boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

when it comes to the drivers select **vesa** and continue with reconfiguring to the end.When it  is finish type **startx** and you should have elementar grapfic.Now you can go for your video card drivers.I think they are under system<administration restricted drivers manager.

---

### Post by Holy-Fire on 2008-01-26
Ok, thanks.

---

