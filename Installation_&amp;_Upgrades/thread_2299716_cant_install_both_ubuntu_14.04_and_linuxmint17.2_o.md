---
title: "cant install both ubuntu 14.04 and linuxmint17.2 on my dell optiplex 780"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by nnamdi on 2015-10-20
Good Evening Everyone

when i try to install ubutu or linuxmint on my system(dell optilex 780) and the hard disk size is 1tb. it does not see my hard disk dont know why and i chaned some many hdd even tried installing via cd and usb still same issue, but i run gparted on my system using the live cd and usb installation kit  i can see and mount the hard disk, format to any file system too. i was able to crop an image of the error message when i click the add button.

thank you in advance

---

### Post by nnamdi on 2015-10-26
hello everyone 

i was able to solve the issue with the command below


**sudo dmraid -E -r /dev/sda**

this is my source [http://forums.linuxmint.com/viewtopic.php?f=46&t=200416](http://forums.linuxmint.com/viewtopic.php?f=46&t=200416)


thank you 

nnamdi

---

