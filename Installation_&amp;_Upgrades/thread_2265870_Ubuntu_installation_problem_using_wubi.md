---
title: "Ubuntu installation problem using wubi ?"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by asif_khan2 on 2015-02-18
I hav ubuntu 14.04.1 ISO and i am trying to install ubuntu through wubi.
But after installation, what i get is non-graphical interface. I tried other versions like kubuntu. I couldn't even install fedora using live usb. Also if it is of any use,my windows is installed in legacy mode . Below is the interface i get. Can anyone help me out ?

![enter image description here][1]


  [1]: [http://i.stack.imgur.com/JnFYP.jpg](http://i.stack.imgur.com/JnFYP.jpg)

---

### Post by oldfred on 2015-02-18
Last supported version of wubi is 12.04. It does not work with new UEFI systems, so new users with new systems cannot use it anymore at all.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Do you have all 4 primary partitions in use with BIOS/MBR?

Post this from terminal in live installer:
sudo parted -l

---

