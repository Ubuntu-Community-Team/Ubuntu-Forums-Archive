---
title: "Unable &quot;flashplugin&quot;"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Tourdog on 2009-12-29
Netbook Remix 9.10 on Acer Aspire One, 2 gigs.     After marking the 2 files in Synaptics Mgr and switching to "Terminal"  I've tried and got this:

ubuntu@ubuntu:~$ sudo apt-get install flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ 

What am I missing other than being a noob on Ubuntu Linux?  TIA!   :confused:

---

### Post by e-Gee on 2009-12-29
Try install all updates or just try install ubuntu-restricted-exstras and you will get the flashplugins too. And Terminal can't install anything if you have synaptic opened you have to close synaptic first

---

### Post by Tourdog on 2009-12-29
thank you.................  thank You!!!

Tourdog   :)




Thank you "E-Gee" it worked perfectly.  You Gurus are great!

---

