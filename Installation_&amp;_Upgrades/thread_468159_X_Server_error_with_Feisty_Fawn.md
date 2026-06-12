---
title: "X Server error with Feisty Fawn"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by mckinneycm on 2007-06-08
I've tried multiple ways to install Feisty Fawn:

1. Straight install from Live CD.
2. Upgrade from 6.10 using the 7.04 CD.
3. Upgrade from 6.10 using  $ gksu "update-manager -c"

No matter what method I use, the installation looks fine. Then when it reboots after it's done, I get a blue screen with an error saying that it cannot load X Server (Video Graphics Card). Is there anyway to get aroud this error so that it will load?

---

### Post by NeoLithium on 2007-06-08
Depending on your graphics card, you may have to install the proper drivers.  What card do you have?  Have you tried to reconfigure the x-server?  You can try with the following commands
```

sudo dpkg-reconfigure xserver-xorg

```
Just answer the questions that you know, and leave the rest as default.

---

### Post by mckinneycm on 2007-06-08
I have the 'ATI Mobility FireGL V5200'. I went through the setup and rebooted. It does the same thing. When I look at the output from the X Server it says 'Fatal Error: No screen found'. Any ideas???

---

### Post by NeoLithium on 2007-06-08
There's a section on Ubuntu guide about installing ATI drivers, perhaps this will help you out: 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28ATI.29)

---

