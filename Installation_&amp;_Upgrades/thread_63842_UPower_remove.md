---
title: "UPower remove"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by myha on 2005-09-09
Hi all!

Im having a little problem with UPower... I installed it according to [Ubuntu Wiki](https://wiki.ubuntu.com/UPower) , but now I decided not to use it anymore so I want to disable it....
I managed to disable graphic, but in console I still see something like
booting process 20% .....
Is it ok if I simply remove upower10, upower20,... from /etc/init.d  ? I tried chmod o-x but it doesnt help...

Can anyone please tell me how to get rid of it because its pretty annoying...

Thanks, Miha

---

### Post by jasmuz on 2005-09-09
I imagine you installed from a .deb package, right?

If so, just open a console and type sudo apt-get remove upower

That should be it.-

---

### Post by myha on 2005-09-09
Yeah I tried that and it removed upower graphical splash... But outpot in console still remains on system boot and thats whats bothering me...
Will try to install and remove again maybe it will help...

---

### Post by codejunkie on 2005-09-09
[QUOTE=myha]Yeah I tried that and it removed upower graphical splash... But outpot in console still remains on system boot and thats whats bothering me...
Will try to install and remove again maybe it will help...[/QUOTE]
doesnt upower edit your /boot/grub/menu.lst file and add a line about the vga=something removing the entry upower added to that should disable it.

---

### Post by myha on 2005-09-09
I managed to remove it....  :)
```
sudo dpkg --purge upower
``` 

And yes it was something in grub config because when I removed it it changed my grub config a bit... I saw your post too late to look what it was... Thanks anyway!

Miha

---

