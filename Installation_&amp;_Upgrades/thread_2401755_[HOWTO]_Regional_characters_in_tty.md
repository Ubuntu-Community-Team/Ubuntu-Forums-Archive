---
title: "[HOWTO] Regional characters in tty"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by s-byczkowski on 2018-09-22
The problem considers tty. It's what you get when pressing Ctrl+Alt+number. Not the console app in GUI.
The regional characters keep disappearing from tty after reboot and you have to issue command 
```
loadkeys [country code there]
```
to restore them.
Problem:
[Bug in debian.]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=818065")

The resolution:
```
sudo rm /etc/console-setup/cached_*
sudo setupcon --save-only

```
This will change the buggy line in
```
/etc/console-setup/cached_setup_keyboard.sh
```
as follows(patch format):
```
-loadkeys '/tmp/tmpkbd.iDWdSi' > '/dev/null'
+loadkeys '/etc/console-setup/cached_UTF-8_del.kmap.gz' > '/dev/null'
```
You can change it with text editor if you like, and your regional characters will stay after reboot.

Yep. They did not fix this in debian. Bug in present for couple of years now.

---

