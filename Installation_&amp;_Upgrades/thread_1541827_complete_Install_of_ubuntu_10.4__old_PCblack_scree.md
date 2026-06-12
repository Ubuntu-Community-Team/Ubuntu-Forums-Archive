---
title: "complete Install of ubuntu 10.4 : old PC/black screen"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by lindenb on 2010-07-29
Hi all,

I'm trying to make a complete install of ubuntu 10.4 on an old PC.

When I boot from the CD, a text screen is displayed: "PhoenixBIOS Utility"
```
BIODate: 09/14/99
CPU type:celeron
CPU Speed: 266Mhz
System memory: 640k
BiosVersion:1.0N  -0124-6208
(...)
```The system then asks me if I want to install ubuntu on this PC => yes

I then pressed 'esc' to see the messages:
```
(...)getpwuid_r() failed due to unknown user id(0)
(...) generating locales
(...)scanning disc for index files..
(...) reading packages indexes.. done
(... ...)
(..) skipping nonexistent file /cdrom/dists/lucid/main/binary-i386/Packages
skipping nonexistent file /cdrom/dists/lucid/restricited//binary-i386/Packages
No value set for '/apps/netbook-launcher/favorites/favorites_list'
No value set for '/apps/netbook-launcher/favorites/favorites_list'
No value to set for key '/apps/netbook-launcher/favorites/favorites_list'
init: unreadahead-other main process (878) terminated with status 4
init: unreadahead-other main process (879) terminated with status 4

``` and then the screen goes black.

How can I fix this ?

Many thanks !

Pierre

---

### Post by roger_1960 on 2010-07-29
That sounds like a faulty Ubuntu CD, have you checked the md5sum ?

See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by lindenb on 2010-08-02
Thanks, 
the MD5 was fine
I've been suggested that my PC cannot support this version of ubuntu, I will try something lighter like KUbuntu (?) or TinyCore(?) etc...

---

### Post by ahbart on 2010-08-02
> CPU Speed: 266Mhz, System memory: 640k Is 640k really you system memory? 
That is a long time ago ;-) 
Ubuntu will definitely be a problem for this one. You could try Puppy. Kubuntu is not a light alternative :D. Xubuntu is, but I even think xfce won't work. especially not if 640k is your system memory.

---

