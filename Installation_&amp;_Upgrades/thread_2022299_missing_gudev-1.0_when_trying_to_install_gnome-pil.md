---
title: "missing gudev-1.0 when trying to install gnome-pilot-2.91.93"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by markenaix on 2012-07-10
Hi,

I ran onto the same **missing gudev-1.0** as in this thread:

[http://ubuntuforums.org/showthread.php?p=12085476#post12085476](http://ubuntuforums.org/showthread.php?p=12085476#post12085476) 

when trying to install gnome-pilot-2.91.93 on an Ubuntu 12.04 in a Gnome 3.4.1 session 
even though **gir1.2-gudev-1.0 is installed** and 
I have the **ppa:gnome3-team/gnome3 repository** in my software sources.

Would appreciate your help cause I'm stuck in the ./configure step of the install.

Thanks in advance.

Some extra information:

     Code:
     sudo ldconfig -p | grep -i gudev     
libgudev-1.0.so.0 (libc6) => /usr/lib/i386-linux-gnu/libgudev-1.0.so.0 
     Code:
      sudo pkg-config --list-all | grep -i gudev     
gudev-sharp-1.0                GUdev - GUdev

---

