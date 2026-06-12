---
title: "can't install sopcast in lucid"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by 135798642 on 2010-04-30
can't install sp-auth:
```
sp-auth:
 Depends: libstdc++5  but it is not installable
```
while default libstdc in lucid is ++6, plz help me install sopcast,i want to watch chelsea-liv match this sunday :(

---

### Post by 135798642 on 2010-04-30
anyone help me plz :((

---

### Post by lechien73 on 2010-04-30
Hi,

I have Sopcast working fine in Lucid 64-bit. Here's what I did:

[INDENT]sudo add-apt-repository ppa:jason-scheunemann/ppa
sudo apt-get update
sudo apt-get install sopcast-player[/INDENT]

This installs all the correct libraries and the correct version of sp-auth. HTH

Matt

---

### Post by 135798642 on 2010-04-30
hix, 64bit lucid can install libstdc++5, but 32bit lucid can't :( anyone help me plz :(

---

### Post by Taman on 2010-05-01
> **135798642 said:**
> hix, 64bit lucid can install libstdc++5, but 32bit lucid can't :( anyone help me plz :(


try this  [http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)

---

### Post by 135798642 on 2010-05-01
thanks,it's working..

---

### Post by wirespot on 2010-08-29
Here's the full method of installing sopcast on Linux. Open a console:

1) Add the flyguy PPA repo to your system:
```
sudo add-apt-repository ppa:jason-scheunemann/ppa
```

2) Refresh the packages list:
```
sudo apt-get update
```

**If you have 64bit Ubuntu jump to step (4).**

3) Get a libstdc5++ version you can install and install it:
```
wget http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb
sudo dpkg -i libstdc++5_3.3.6-18_i386.deb
```

4) Install sopcast (it will automatically pull in sp-auth):
```
sudo apt-get install sopcast-player
```

---

