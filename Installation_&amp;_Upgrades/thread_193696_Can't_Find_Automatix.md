---
title: "Can't Find Automatix"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by CarlosinFL on 2006-06-10
I was following the "HOT TO" for automatix however I don't seem to have it installed nor can I find it using APT-GET.

```
root@mobile:~# Automatix
-su: Automatix: command not found
root@mobile:~# apt-get install Automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Automatix
```

Any suggestions?

---

### Post by deadgobby on 2006-06-10
[QUOTE=Carlwill]I was following the "HOT TO" for automatix however I don't seem to have it installed nor can I find it using APT-GET.

```
root@mobile:~# Automatix
-su: Automatix: command not found
root@mobile:~# apt-get install Automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Automatix
```

Any suggestions?[/QUOTE]
 You missed a step. try input the following.

[COLOR="Blue"]wget [http://beerorkid.com/arnieboy/automatix_6.1_i386.deb](http://beerorkid.com/arnieboy/automatix_6.1_i386.deb)
sudo dpkg -i automatix_6.1_i386.deb[/COLOR]

then type in
[COLOR="Blue"]Automatix[/COLOR]

---

