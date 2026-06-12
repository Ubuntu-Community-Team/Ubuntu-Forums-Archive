---
title: "Error on Upgrade to 2.6.31-21-generic"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by wblogan on 2010-04-29
Installed updates including 2.6.31-21-generic:

bill@dell-laptop:~$ uname -a
Linux dell-laptop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

After rebooting got the following error msg:

"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-aAjoYWyt8G: Connection refused)"

Reverted to 2.6.31-20-generic:

bill@dell-laptop:~$ uname -a
Linux dell-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Checked dmesg and found the following lines from the boot to the new kernel:
------------
Apr 29 08:25:47 dell-laptop bonobo-activation-server (bill-2586): could not associate with desktop session: Failed to connect to socket /tmp/dbus-aAjoYWyt8G: Connection refused
Apr 29 08:25:54 dell-laptop pulseaudio[2669]: pid.c: Stale PID file, overwriting.
Apr 29 08:25:58 dell-laptop kernel: [   35.372104] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 29 08:26:03 dell-laptop bonobo-activation-server (bill-2926): could not associate with desktop session: Failed to connect to socket /tmp/dbus-aAjoYWyt8G: Connection refused
-------------
Rebooted to 2.6.31-21-generic and got no error; dmesg shows no "Failed to connect to socket /tmp/dbus-aAjoYWyt8G: Connection refused)".

I went to [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) and do not understand what I read there. Since I am getting no more error messages can I assume all is well?

---

