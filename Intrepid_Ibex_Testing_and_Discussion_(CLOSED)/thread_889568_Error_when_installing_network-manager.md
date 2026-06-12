---
title: "Error when installing network-manager"
date: 2008-08-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xan.scale on 2008-08-14
```
xan@pro:~$ sudo apt-get install network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libnl1 libnm-glib0 libnm-util0 network-manager-gnome
The following NEW packages will be installed:
  libnl1 libnm-glib0 libnm-util0 network-manager network-manager-gnome
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/759kB of archives.
After this operation, 5399kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package libnl1.
(Reading database ... 62433 files and directories currently installed.)
Unpacking libnl1 (from .../archives/libnl1_1.1-2_i386.deb) ...
Selecting previously deselected package libnm-util0.
Unpacking libnm-util0 (from .../libnm-util0_0.7~~svn20080720t224551+eni1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libnm-glib0.
Unpacking libnm-glib0 (from .../libnm-glib0_0.7~~svn20080720t224551+eni1-0ubuntu1_i386.deb) ...
Selecting previously deselected package network-manager.
Unpacking network-manager (from .../network-manager_0.7~~svn20080720t224551+eni1-0ubuntu1_i386.deb) ...
Selecting previously deselected package network-manager-gnome.
Unpacking network-manager-gnome (from .../network-manager-gnome_0.7~~svn20080721t051503-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libnl1 (1.1-2) ...

Setting up libnm-util0 (0.7~~svn20080720t224551+eni1-0ubuntu1) ...

Setting up libnm-glib0 (0.7~~svn20080720t224551+eni1-0ubuntu1) ...

Setting up network-manager (0.7~~svn20080720t224551+eni1-0ubuntu1) ...
 Adding system startup for /etc/init.d/NetworkManager ...
   /etc/rc2.d/S30NetworkManager -> ../init.d/NetworkManager
   /etc/rc3.d/S30NetworkManager -> ../init.d/NetworkManager
   /etc/rc4.d/S30NetworkManager -> ../init.d/NetworkManager
   /etc/rc5.d/S30NetworkManager -> ../init.d/NetworkManager
/var/lib/dpkg/info/network-manager.postinst: 35: /usr/share/update-notifier/notify-reboot-required: not found
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.7~~svn20080720t224551); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i dont know why...

---

### Post by mikeyphi on 2008-08-14
Open a terminal and enter:
sudo dpkg --configure -a

that might sort the issue.

---

### Post by xan.scale on 2008-08-14
```
xan@pro:~$ sudo dpkg --configure -a
[sudo] password for xan: 
Setting up network-manager (0.7~~svn20080720t224551+eni1-0ubuntu1) ...
 System startup links for /etc/init.d/NetworkManager already exist.
/var/lib/dpkg/info/network-manager.postinst: 35: /usr/share/update-notifier/notify-reboot-required: not found
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.7~~svn20080720t224551); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 network-manager
 network-manager-gnome

```

ehmmm ... no...

---

### Post by mikeyphi on 2008-08-14
Just one more suggestion - reboot your system and then run that configure command again.

---

### Post by xan.scale on 2008-08-14
ok, do it...

the same...

---

### Post by Senor Hubris on 2008-08-16
run (as root):  apt-get install update-notifier

You can tell from the error message that it wants update-notifier to be installed...so you need to install it.

---

