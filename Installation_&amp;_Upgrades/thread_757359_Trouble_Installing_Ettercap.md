---
title: "Trouble Installing Ettercap"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by shmoe010 on 2008-04-16
I got all the libraries that I need for ettercap from Synaptic and ran the config successfully but it would not allow me to run a 'make' command in the directory. So I decided to try getting by apt-get and here's the output:

root@garlinux:/home/george# sudo apt-get install ettercap-gtk
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

The only post I found about it said to install it as root, which I did. What else can I do?

---

### Post by Partyboi2 on 2008-04-16
make sure you don't have add/remove or synaptic package manager open when you install from terminal.

---

