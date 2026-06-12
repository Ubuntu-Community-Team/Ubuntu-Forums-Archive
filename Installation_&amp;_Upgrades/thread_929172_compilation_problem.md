---
title: "compilation problem"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by rania kamal on 2008-09-24
i install ns2.33 on my ubuntu and i have to do some changes on ns2.33 files, so i must do compile after my changes.
after i run configure and make appear to me some problems:-

rania@rania- desktop:~ /ns-allinone- 2.33/ns-2. 33$ make
make: CXX@: Command not found
make: *** [common/packet. o] Error 127


i don't know why the compilation doesn't work although i have gcc, g++ install

---

### Post by cariboo on 2008-09-24
Make sure you have build-essentials installed:

```
sudo apt-get install build-essentials
```

Having gcc installed is not enough.

Jim

---

### Post by rania kamal on 2008-09-28
i already install it, when i install ns2.33

---

### Post by rania kamal on 2008-09-28
to be sure that i will install build essential again and this what appear to me:-
  
rania@rania-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libpcap0.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
rania@rania-desktop:~$

---

