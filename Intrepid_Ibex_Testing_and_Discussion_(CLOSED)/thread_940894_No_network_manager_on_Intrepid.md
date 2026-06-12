---
title: "No network manager on Intrepid"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sipickles on 2008-10-07
Hi,

I have installed Intrepid Server Beta, and added ubuntu-desktop.

Unfortunately I have no network manager icon, nor in the System>Admin.

Synaptic says network-manager is installed but I get this from a command line:

```
simon@server:~$ sudo network-manager
[sudo] password for simon: 
sudo: network-manager: command not found

simon@server:~$ apt-cache showpkg network-manager
Package: network-manager
Versions: 
0.7~~svn20081004t225044-0ubuntu1 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages
                  MD5: e5d5666eb7761fe9937c997f7229a928


Reverse Depends: 
  network-manager-kde,network-manager 0.6.2
  network-manager-gnome,network-manager 0.7~~svn20080928
  evolution,network-manager
Dependencies: 
0.7~~svn20081004t225044-0ubuntu1 - libc6 (2 2.4) libdbus-1-3 (2 1.0.2) libdbus-glib-1-2 (2 0.74) libglib2.0-0 (2 2.16.0) libhal1 (2 0.5.8.1) libnl1 (0 (null)) libnm-glib0 (2 0.7~~svn20080908) libnm-util0 (2 0.7~~svn20080908) libnspr4-0d (2 1.8.0.10) libnss3-1d (2 3.12.0~1.9b1) libpolkit-dbus2 (2 0.7) libpolkit2 (2 0.7) libuuid1 (0 (null)) iproute (0 (null)) iputils-arping (0 (null)) lsb-base (2 2.0-6) wpasupplicant (2 0.6.1~) dbus (2 0.60) hal (2 0.5.7.1) update-notifier-common (0 (null)) network-manager-gnome (16 (null)) network-manager-kde (0 (null)) network-manager-pptp (3 0.7~~) network-manager-pptp (3 0.7~~) 
Provides: 
0.7~~svn20081004t225044-0ubuntu1 - 
Reverse Provides: 

```

Any ideas?
 Thanks!

---

### Post by sipickles on 2008-10-07
I've used the excellent wicd instead. It really should ship with Ubuntu. Leaves network-manager for dust!

---

### Post by paxmark1 on 2008-10-08
Thanks much.  The wicd looks quite intriguing.  I was looking into a clean install of i-386 Intrepid Ubuntu server but I was noticing the differences noted in networking and had some trepidation.  (I plan to then go to kde 3.5. (I can always compile.)  wicd really looks sweet.  

I have had fair success with the jump to kde 4 with intel 740 onboard video and 512 mb ram in a very cheap sff, but lots of flickers, and too much eye candy with even effects turned off.  And slower.  

peace

---

