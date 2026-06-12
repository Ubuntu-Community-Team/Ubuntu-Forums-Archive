---
title: "Centralising grub menu on screen"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubiubi on 2009-10-06
Hi does anybody know how to centralise the grub menu instead of having it squashed up to the left of the scree? Also, am I right in thinking that karmic beta comes with grub2 as default. I tried following threads to download ne grub2-splash images but I dont appear to have a/etc/share/images/grub file

I created one and managed to download the images, finally! Is this workaround dangerous for the system?

Thanks in advance

---

### Post by VMC on 2009-10-06
> **ubiubi said:**
> Hi does anybody know how to centralise the grub menu instead of having it squashed up to the left of the scree? Also, am I right in thinking that karmic beta comes with grub2 as default. I tried following threads to download ne grub2-splash images but I dont appear to have a/etc/share/images/grub file

I created one and managed to download the images, finally! Is this workaround dangerous for the system?

Thanks in advance

Regarding grub2 and karmic, the answer is yes. Read [this]("https://wiki.ubuntu.com/Grub2") link if you have problems and if you upgraded from jaunty.

---

### Post by ranch hand on 2009-10-06
> **VMC said:**
> Regarding grub2 and karmic, the answer is yes. Read [this]("https://wiki.ubuntu.com/Grub2") link if you have problems and if you upgraded from jaunty.
+1

Upgrades stay with grub-legacy, grub2 is more fun.

I downloaded the backgrounds you are talking about a couple of times and didn't like them.  I just create the /usr/share/images/grub directory and populate it with the images I want to use.  That same "images" directory has the xsplash images too.

I use the same image as background on the menu, xsplash, GDM (gets image from .../xsplash/bg_2560x1600.jpg), xsplash (between login and wallpaper) and finally wallpaper.  FUN.

---

### Post by ubiubi on 2009-10-06
Thanks to you both for your reassurances.
 Now, does anybody know if it is possible to centralise the grub menu on the screen...
 or if [COLOR="Red"]GFX Grub [/COLOR] is applicable for ubuntu 9.10?

Here's hoping!:popcorn:

---

### Post by ranch hand on 2009-10-06
I was looking in the /ect/grub.d/00_header file and saw this on line 37;
```

if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

```
I wonder if giggering with that would help in getting closer to where you want it.  I sure wouldn't change it much at a time.

I would save the file as "00_header.OLD" first and change the permissions so that it is not executable.

Edit and save the file to the original name.  Remember to run "update-grub" or it won't change anything.

---

