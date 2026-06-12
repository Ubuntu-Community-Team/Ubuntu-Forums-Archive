---
title: "system backup?"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by brenbart on 2006-06-23
I've installed Dapper several times on my Compaq presario 1200.  A couple of time successfully!

The install from the alternate Install CD seems to work successfully but when I try either 'sudo apt-get update' or from Synaptic it seems to screw the system.  (I reboot, get to the login screen, enter username and pass and get dumped right back to the login screen.)

Aside from the issue of Xorg dying after an update, how can I create a system backup so that I can back out the update?

What I would like is something like a group of files I could backup then if this happens just go to a terminal and overwrite the various configuration files.  It seems like there should be some sort of automated way of doing this but I'm new to linux.

What files/directories contain the essential operating system config files?

---

### Post by cacharreo on 2006-06-23
Usualy they are inside of /home , /usr and /var

---

### Post by cacharreo on 2006-06-23
Look this:
[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

---

### Post by aysiu on 2006-06-23
I would use this: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by brenbart on 2006-06-23
cacharreo and aysiu,

Thank You!!!

These are just the references I needed!

Brenbart

---

