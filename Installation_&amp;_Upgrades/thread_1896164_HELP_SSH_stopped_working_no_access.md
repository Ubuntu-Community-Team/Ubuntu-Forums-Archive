---
title: "HELP SSH stopped working no access"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by black1stallion2 on 2011-12-16
Hi, i have a dlink dns-323 nas server i then flashed it with a ubuntu  installer and installed it through ssh i then installed and configured  gnome and a vnc server through ssh i went through the process of apache2  php mysql ftp the usual i thought i would try out webmin i hated it so i  then uninstalled it but since the reboot i havent been able to access  ssh what so ever i scanned ports and ports 21 and 80 are only open then  vnc needs to be enable through ssh after a reboot is there anyway i can  access the dns otherwise its just a heavy paper weight i even tried  rigging up the drive to another machine to access it that way but  nothing would read it and i ping the ip address and in browser the ip  works goes to the webpage but thats it
would really love some help as this box cost me £70 and i use it to run the tvs in the house for all our media

---

### Post by black1stallion2 on 2011-12-16
Hi, i have a dlink dns-323 nas server i then flashed it with a ubuntu  installer and installed it through ssh i then installed and configured  gnome and a vnc server through ssh i went through the process of apache2  php mysql ftp the usual i thought i would try out webmin i hated it so i  then uninstalled it but since the reboot i havent been able to access  ssh what so ever i scanned ports and ports 21 and 80 are only open then  vnc needs to be enable through ssh after a reboot is there anyway i can  access the dns otherwise its just a heavy paper weight i even tried  rigging up the drive to another machine to access it that way but  nothing would read it and i ping the ip address and in browser the ip  works goes to the webpage but thats it
would really love some help as this box cost me £70 and i use it to run the tvs in the house for all our media

---

### Post by Hakunka-Matata on 2011-12-16
if you ssh a machine with 
```
ssh das@192.168.1.24
```
what sort of response do you generate?

---

### Post by black1stallion2 on 2011-12-16
192.168.1.68 connection refused
192.168.1.24 no route to host

---

### Post by Hakunka-Matata on 2011-12-16
if the route is through your dlink router, the router may very well have port 22 closed, that must be open if you're going to use the standard ssh port of 22.

also, are you sure ssh is installed on both machines?,
also I use grc.com/ to  check my ports, ip address, a whole bunch of really fun, serious security stuff:

[www.grc.com/]("http://www.grc.com/")

---

### Post by jonobr on 2011-12-16
SSH runs on port 22 check if thats open.

Also, respectfully, your post is hard to read.
Theres a lot of information in one long sentence.

---

