---
title: "boot manager"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by mucmicu on 2008-05-10
Hi there

My boot manager (default, after Ubuntu 8.04 install) is in text mode. How can I have it in graphical mode?

---

### Post by mucmicu on 2008-05-10
I find how to do it:
```
wget -c http://easylinux.info/uploads/ubuntu.xpm.gz
chmod 644 ubuntu.xpm.gz
sudo cp ubuntu.xpm.gz /boot/grub/splash.xpm.gz
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo update-grub

```

---

### Post by y2ken on 2008-10-28
OK, I'm a Ubuntu / Linux noob. 
How do I use this code?

Is there a way to install it through the Package Manager?

I recently installed a third party app called WICD, it gave me a URL *[deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras]* that I entered into the Package Manager and everything installed very easily.

---

### Post by oldos2er on 2008-10-28
Copy and paste each line one at a time into a terminal.

---

### Post by y2ken on 2008-10-30
Thanks for the help! It worked fine but the result wasn't what I was expecting. All it did was include a splash screen graphic behind the text choices. I was looking for a actual graphical choice menu. I've heard of a boot manager called GAG, I have to check it out. Thanks again for your help!

---

### Post by Mark Phelps on 2008-10-30
Did you just want a graphical display, with selections you can choose using the mouse? OR did you want a completely different boot manager that uses a graphical display?  Installing GAG results in the latter, not the former.

---

