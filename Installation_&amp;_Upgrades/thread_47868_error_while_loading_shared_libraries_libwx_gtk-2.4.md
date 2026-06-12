---
title: "error while loading shared libraries: libwx_gtk-2.4.so.0"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by action09 on 2005-07-10
Hi !

Im' using Hoary with sources as in the ubuntuguide (universe/multiverse/backports), i tried to instal amule or xmule too.. and the install went without any problem. (sudo apt-get install amule), but when i try to lunch it nothing happen, so i decided to launch it in a xterm:

action09@WOPR:~$ xmule
xmule: error while loading shared libraries: libwx_gtk-2.4.so.0: cannot open shared object file: No such file or directory
action09@WOPR:~$

tried to make a symlink :
ln -s /usr/lib/libwx_gtk-2.4.so.0.1.1 /usr/lib/libwx_gtk-2.4.so.0

but SEGFAULT when i launch x/a mule.. so i removed the link.

Any idea please ?

Thanks !

---

