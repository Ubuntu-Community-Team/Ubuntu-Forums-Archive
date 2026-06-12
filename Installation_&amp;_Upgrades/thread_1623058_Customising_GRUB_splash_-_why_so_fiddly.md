---
title: "Customising GRUB splash - why so fiddly??"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by youbuntu on 2010-11-16
Okay, so in Linux mint, I customised the GRUB background by simply changing a PNG file path in:

/etc/default/grub

and then doing:

```
 sudo update-grub
```Why do you Ubuntu people make achieving this same goal *such* a fiddle? Someone needs to get on the case, and simplify this whole process. I just want a different background @ GRUB screen - is that hard? I shouldn't have to mess about making .xpm.gz files, and futzing about with different scripts :confused: I JUST WANT A GRUB SPLASH! :D

Thank you

---

### Post by Megaptera on 2010-11-16
Is Burg any use to you:

[http://www.liberiangeek.net/2010/07/manage-burg-boot-loader-ubuntu-10-04-lucid-lynx-burg-manager/](http://www.liberiangeek.net/2010/07/manage-burg-boot-loader-ubuntu-10-04-lucid-lynx-burg-manager/)

---

### Post by drs305 on 2010-11-16
> **glossywhite said:**
> I just want a different background @ GRUB screen - is that hard? I shouldn't have to mess about making .xpm.gz files, and futzing about with different scripts :confused: I JUST WANT A GRUB SPLASH! :D

I don't understand your situation. 

For a basic grub background, open /etc/grub.d/05_debian_theme and change the WALLPAPER path to point to the image you want to use. If it's in a compatible format (png, tga, 8-bit jpeg) and you update-grub it should work.

If you explain further what difficulties you are having in Ubuntu we can offer more specific advice. Ubuntu should be working just as Mint does.

---

### Post by youbuntu on 2010-11-16
> **drs305 said:**
> I don't understand your situation. 

For a basic grub background, open /etc/grub.d/05_debian_theme and change the WALLPAPER path to point to the image you want to use. If it's in a compatible format (png, tga, 8-bit jpeg) and you update-grub it should work.

If you explain further what difficulties you are having in Ubuntu we can offer more specific advice. Ubuntu should be working just as Mint does.

I'm sorry folks, I was being impatient and not reading the guide thoroughly. As you have suggested works very well indeed.

Thank you

---

