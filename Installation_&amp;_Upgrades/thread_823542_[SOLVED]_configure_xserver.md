---
title: "[SOLVED] configure xserver"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by MEETyA on 2008-06-09
Hello,

I just installed Hardy on my computer, but I've got a problem with my resolution. I activated the nvidia-driver in restricted drivers and rebooted. After this step I allways had to reconfigure my xserver. But now this step doesnt work.

When I run sudo dpkg-reconfigure xserver-xorg the tool seems to hide most menu-points. Im only able to configure my keyboard.

I read that I should use sudo dpkg-reconfigure -plow xserver-xorg instead of the other command but this makes the same output. How can I configure my resolution and all that stuff? My x.org-file isnt used completly.. Some entrys are missing (like the resolution, driver and modules). I edited it manually but this doesnt make any changes.

Thanks for your help

---

### Post by Pumalite on 2008-06-09
Can you get into Recovery Mode?

---

### Post by MEETyA on 2008-06-09
you mean STRG + ALT + F11 ? This doent work.. I just see one blinking _ there and nothing happens

---

### Post by Pumalite on 2008-06-09
If you can get a command line with Ctrl+Alt+F1; try xfix

---

### Post by dstew on 2008-06-09
Xfix will re-create a basic, functional xorg.conf, but to really configure the Xserver you need to use displayconfig-gtk. Once you have the nvidia driver loaded from the Hardware Drivers menu, press alt-F2 to get a command line, then enter```
gksudo displayconfig-gtk
```You will be able to configure your display there. It is best to find your display maker and model number, and it will automatically give you the depth, resolutions and refresh rates that your monitor will support. There are also a variety of generic monitor and LCD choices as well.

That said, there is no guarantee that the restricted driver will work properly with your particular machine. The restricted driver pretty much blows up mine, so I have to settle for basic effects only.

---

### Post by MEETyA on 2008-06-09
Hey,

thanks for your help. The commandline says that the command xfix doesnt exist. Not as user and not as sudo

---

### Post by MEETyA on 2008-06-09
Okay it finally works :D

Thanks for your help :)

---

### Post by dstew on 2008-06-09
How did you get it working? Please post so others can have a reference.

---

### Post by MEETyA on 2008-06-10
As you have suggested it. Thats why I thanked you for your post.

---

