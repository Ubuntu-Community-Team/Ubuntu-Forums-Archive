---
title: "Black screen boot"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by jaysons on 2007-11-30
I got an answer form somebody on fixing my looooong boot screen: 
For black screen:

- change splash resolution in /etc/usplash.conf file (try with 1024x768)
- add "vga=791" to your active kernel line in /boot/grub/menu.lst
- sudo update-initramfs -u -k `uname -r`

Then reboot your system.

So when I try sudo update-initramfs -u -k (what is uname)?? -r   I keep getting illegal options....

I also need to know where exactly to add the "vga=791" what line is the active kernel line? is that at the bottom of menu.lst???

thanks!!..

---

