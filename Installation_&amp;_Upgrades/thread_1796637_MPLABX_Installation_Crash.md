---
title: "MPLABX Installation Crash"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by Denizen08 on 2011-07-04
I have been trying to install MPLABX32 unto my XUBUNTU 11.04, but the installation crashes with an error reference to a GTK2.0 component.

```
denizen@ubuntu:~$ sudo chmod 777 mplabx32.bin 
denizen@ubuntu:~$ ls -la
-rwxrwxrwx  1 denizen denizen 218691178 2011-07-04 14:33 mplabx32.bin
denizen@ubuntu:~$ sudo ./mplabx32.bin 
/usr/share/themes/NOX/gtk-2.0/gtkrc:233: Murrine configuration option "gradients" is no longer supported and will be ignored.

```
*I removed some unnecessary entries like the rest of my directory's content.*

How can I resolve this? Would I simply require an installation of a library component for GTK normally not included with the vanilla XUBUNTU install?

---

