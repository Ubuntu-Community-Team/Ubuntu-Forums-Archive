---
title: "bind dns cashing name server"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-26
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

do this at your own risk, i had problems and had to remove bind9 and bind9uitls.  its probably a configuration problem

alt + f2

gksu synaptic

run

look for and install bind9 + bind9utils

close synaptic

then open a terminal...

alt + f2

gnome-terminal

run

```

cat /etc/resolv.conf | grep nameserver

```

to tell you what to put in

```

gksu gedit /etc/bind/named.conf.local

```

add this to the file, then change 8888 to your 1st ip, and 8844 to your second dns ip. (or dont and contiune to use googles free dns's)
```

forwarders {
               8.8.8.8;
               8.8.4.4;
           };

```

then in the terminal issue this to fix some details

```

sudo rndc-confgen >> /etc/bind/named.conf.local

```

```

sudo /etc/init.d/bind9 restart

```

---

### Post by jdthood on 2013-01-06
Anyone interested in having bind9's forwarders list dynamically updated, please add your voice to the following (wishlist) bug report.

    [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602)

---

