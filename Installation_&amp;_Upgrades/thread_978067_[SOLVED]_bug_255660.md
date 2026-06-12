---
title: "[SOLVED] bug 255660"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by miousername on 2008-11-10
i've found a solution for the bug 255660 whit this issue:

nautilus: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined
symbol: cairo_format_stride_for_width

(The solution works also if gnome doesn't restart after un upgrade, for example from hardy to intrepid, or from gusty to hardy)


I've read the solution that it said to delete the library in /usr/local/lib, it wasn't necessary. You can open the terminal and type:


$ sudo ldconfig -v /usr/lib

Now reboot or type ctrl+alt+del to restart the X server, the command  fix temporarily the bug. If you want to fix the bug forever you've type in a terminal:

$ sudo gedit /etc/ld.so.conf.d/libc.conf 

Now,edit in this way:

# libc default configuration
#/usr/local/lib

save and exit. Type in a terminal:

$ sudo ldconfig -v /usr/lib


Now you can use /usr/local/lib to install your extra library because ldconfig when run after un installation of any package doesn't rebuild the ld.so.cache with the library in /usr/local/lib ^_^

---

