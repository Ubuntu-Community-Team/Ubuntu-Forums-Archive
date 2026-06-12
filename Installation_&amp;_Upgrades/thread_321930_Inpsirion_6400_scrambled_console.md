---
title: "Inpsirion 6400 scrambled console"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by mcglnx on 2006-12-19
Dear All,

After upgrading my Inpsiron 6400 to Edy, I cannot log into the console (Ctl+Alt+F1, F2,....)
The consoles are completly** scrambled!**
You do not see any charater or nothing just horizontal lines of dirrent colors (brown/yellow,...)

The only good news is that it follows the Ubuntu theme :)

Any idea for this?
Thanks,
M

---

### Post by mcglnx on 2006-12-23
ping?

---

### Post by Passenger on 2007-03-18
I've got the same issue. It seems like the splash option in /boot/grub/menu.1st messes up the consoles. Disabling splash (by simply removing it) will give you a usable console.

You can also try to add vga=791 to the boot option to get a 1024x768 console. Obviously framebuffer doesn't know how to start a 1280x800 console. When I run 'hwinfo --framebuffer', it only gives me some 1024 and lower resolutions. Anyone got an idea how to fix this?

---

### Post by mcglnx on 2007-03-25
Sorry for the late answer.

I wanted to keep the splash.
I've updated /boot/grub/menu.lst adding vga=791 at the first kernel lines. Works perfectly!

The fonts are then smaller and with different colors. But I have my terminal backs!

Thanks a lot for this trick. 
Once again something that is not good for the beginner!

M.

---

