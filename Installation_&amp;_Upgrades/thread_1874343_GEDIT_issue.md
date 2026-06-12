---
title: "GEDIT issue"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by lm77054 on 2011-11-02
I hope I can explain this sufficiently.  I'm working with UBUNTU as a Windows app.  Right now, I'm developing the procedure to insure my UBUNTU config is what I want (see my other one about hardware), building a checklist.  When I attempt to edit the smb.conf file, logged on with my regular ID, I get, as expected, a security error (can't write).  So I open a terminal window, issue the command of sudo su, enter my password, and I get the terminal prompt back.  I then try to start gedit in the terminal window (using "gedit" (no quotes)), and get an error telling me to use gedit --help.  I don't understand why this is happening.  I can use gedit from a terminal window when not using sudo su, but not when I use sudo su.  What am I doing wrong?  Thanks in advance!

---

### Post by papibe on 2011-11-02
The easiest way to use gksudo:
```
gksudo gedit /etc/samba/smb.conf
```
Hope it helps,
Regards.

---

### Post by lisati on 2011-11-02
Further to what papibe said, use "sudo" for command-line stuff that needs admin permissions, and gksudo for GUI-based programs. For more information, have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lm77054 on 2011-11-03
I appreciate the replies.  But one more question has surfaced.  When I use the gksudo.... command, I get the following.  What's up?  I use the UBUNTU 11.10 CD and did a standard install (used the defaults).  Thanks in advance! ========================= (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gedit:1711): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.J2XQ4V': No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9ZIT4V': No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by lm77054 on 2011-11-03
[QUOTE=lm77054;11421115]I appreciate the replies.  But one more question has surfaced.  When I use the gksudo.... command, I get the following.  What's up?  I use the UBUNTU 11.10 CD and did a standard install (used the defaults).  Thanks in advance! =========================  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gksudo:1709): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",  (gedit:1711): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.J2XQ4V': No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9ZIT4V': No such file or directory  (gedit:1711): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

