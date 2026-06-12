---
title: "grub2 background with text colors?"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by johnl on 2009-10-24
I see that the config setup for grub2 is very different than the old grub.

I managed to set a background image in /etc/grub.d/05_debian_theme, and set a higher resolution in /etc/defaults/grub after checking the vbeinfo.  That all works great.

However, the actual boot text is now somewhat unreadable on top of the image.  Is there a way to specify that I would like the same 'monochromatic' white text, white selection rectangle as without a boot image, only with the boot image in the background?

---

### Post by Elfy on 2009-10-24
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming)

look dopwn a bit for Set menu font & highlight colors

---

### Post by philinux on 2009-10-24
Might be buried in here.

[http://ubuntuforums.org/showthread.php?t=1182436&highlight=grub2+theming](http://ubuntuforums.org/showthread.php?t=1182436&highlight=grub2+theming)

---

### Post by johnl on 2009-10-24
Great, thank you! Not sure how I missed that :)

---

