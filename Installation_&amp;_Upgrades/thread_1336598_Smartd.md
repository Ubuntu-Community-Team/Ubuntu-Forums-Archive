---
title: "Smartd?"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by badger_fruit on 2009-11-24
Hey guys
I have a few 1TB WDC "Green" hdds and one is in the process of failing as I write this.
Although I have contacted the supplier and they are willing to test/replace, the faulty disk is on OpenSuse and it was thanks to SMARTD that it was spotted in time to save my data.

I'm running Mythbuntu 9.04 and don't think SMARTD is installed.
**How can I install it so it will monitor the disks in my Mythbuntu box?**
Many thanks for any replies!

---

### Post by phillw on 2009-11-24
Palimpset   is the monitoring tool, however it is subject to a bug report for erroneous positives.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

Regards,

Phill.

---

### Post by badger_fruit on 2009-11-25
> **phillw said:**
> Palimpset   is the monitoring tool, however it is subject to a bug report for erroneous positives.

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136)

Regards,

Phill.


Thank you for the help Phil - forgive an ubuntu newbie asking but how do I install this?
I tried "sudo apt-get install Palimpset"but was told no such package :(
Please note, this is a headless server to access it I mainly use SSH rather than VNC or the GUI.  Thanks again.

---

### Post by listener on 2009-11-25
> **badger_fruit said:**
> Thank you for the help Phil - forgive an ubuntu newbie asking but how do I install this?
I tried "sudo apt-get install Palimpset"but was told no such package :(
Please note, this is a headless server to access it I mainly use SSH rather than VNC or the GUI.  Thanks again.

I have it installed on Jaunty as smartmontools.  I do not use it on karmic but it is in the repo by the same name.  Not certain how close this is to the exact back-end palimsest uses.  

good luck

---

