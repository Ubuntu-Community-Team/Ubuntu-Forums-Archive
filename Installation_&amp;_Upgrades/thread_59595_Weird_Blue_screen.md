---
title: "Weird Blue screen"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by jzocco on 2005-08-24
i get this weird blue screen when ubuntu trys to load the desktop it looks like a blue flickering box

---

### Post by Lord Illidan on 2005-08-26
Sorry for answering so late, I didn't see your post.

What graphics card do you have?

Try booting up Ubuntu as fail safe, normally the 2nd option in the boot menu, and type this in the terminal..

```
sudo vi /etc/X11/xorg.conf
```

Then press the Insert button on your keyboard.

Navigate around until you come to a section marked Driver, and there should be your graphics card listed over there. Change the driver to

```
Driver  "vesa"
``` 

Then press ESC on the keyboard, and press colon + q ( :q ) to exit

sudo reboot will reboot the pc..

---

### Post by jzocco on 2005-08-27
im running an old dell laptop so it might be to old to handle it its a Inspiron 3700

---

### Post by jzocco on 2005-08-27
i did that and now i get only command line access no gui

whats up with this

---

