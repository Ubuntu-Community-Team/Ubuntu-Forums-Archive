---
title: "[SOLVED] Xming + PuTTY = GConf Error"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by swalker on 2008-09-29
Running gedit on an up-to-date Intrepid install from a Windows XP PuTTY terminal results in:```
$ gedit
GConf Error: Failed to contact configuration server; some possible causes are
that you need to enable TCP/IP networking for ORBit, or you have stale NFS
locks due to a system crash. See http://www.gnome.org/projects/gconf/ for
information. (Details -  1: Failed to get connection to session: Failed to
connect to socket /tmp/dbus-14nvbNVlCy: Connection refused)
```

Any ideas what I need to change on this install to get functional X11 forwarding? It isn't an issue on the alpha 6 live CD so I'm assuming something changed locally.

```
Xming - 6.9.0.31
Xming :0 -clipboard -multiwindow -dpi 120
```
```
PuTTY - 0.60
Enable X11 forwarding is enabled
MIT-Magic-Cookie-1 is selected
```
```
$ grep X11Forward /etc/ssh/sshd_config
X11Forwarding yes
```

---

