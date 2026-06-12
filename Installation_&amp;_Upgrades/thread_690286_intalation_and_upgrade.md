---
title: "intalation and upgrade"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by palanca on 2008-02-07
hi 
have sameone to help what I doeng. I install ubuntu in my pc HP-COMPAQ nx7010
and I see this error 

the security update on security.ubuntu.com couldn&#65533;t be acessed so those update 
will note be made available to you this time. you should investigate this later.
commented out entries for security.ubuntu.com have have been added to the /etc/apt/sources.list

---

### Post by taurus on 2008-02-07
It just means that your network connection isn't working during the installing process.  So, after you log in, you should edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src** to enable more/all repos so you can install more stuff over the network.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

