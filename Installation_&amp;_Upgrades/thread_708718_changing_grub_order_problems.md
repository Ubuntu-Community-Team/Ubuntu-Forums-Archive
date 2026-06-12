---
title: "changing grub order problems"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Neon612 on 2008-02-26
I know the command to go in and change the GRUB boot order:
*sudo gedit /boot/grub/menu.lst*

And i know what i need to change. 

But when i hit enter after typing the sudo command into the terminal it asks me for my password, but will not let me type anything in. The only key that works is the enter key!

I've gone into the boot grub directory without using the terminal window, found the menu.lst file and made the correct changes but it will not let me save it. Gives me some error like you aren't able to change this file or something along those lines.

Is there anyway to fix this so I can setup Windoze as the first OS to boot to?
Thanks

---

### Post by taurus on 2008-02-26
You won't see an echo when you type in your password so make sure you type the right one and hit Enter.  On the other hand, you should use gksudo instead of sudo when you use gedit editing.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Neon612 on 2008-02-26
Thank you it worked great

---

