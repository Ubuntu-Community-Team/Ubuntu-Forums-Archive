---
title: "New GDM indecator-session / apt-get dpkg failed"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wnelson on 2009-09-29
Setting up gdm (2.28.0-0ubuntu8) ...
Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
dpkg: error processing gdm (--configure):
 subprocess installed post-installation script returned error exit status 1

Tried dpkg --configure it failed?

---

### Post by andersju on 2009-09-30
Had the same problem when doing apt-get dist-upgrade as root. Solved it by running **sudo** apt-get dist-upgrade instead, as the logged-in user.

---

### Post by flipsidecreations on 2009-10-02
Thanks, that solved it for me as well.  I am used to running apt as root on my debian servers but I guess Ubuntu prefers that you run it using sudo

---

