---
title: "Ubuntu Desktop version to Netbook version"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by kingsley404 on 2010-11-22
Hello i would like to replace my Ubuntu Desktop version with the Netbook version. I dont mind losing my current data on the desktop version but if there is a way for me not too i would love to know :)

Please and thank you

---

### Post by Jechem on 2010-11-22
search in synaptic "netbook-launcher" and install it. logout then choose netbook edition in the login sreen.

---

### Post by garvinrick4 on 2010-11-22
What version are you using? Do you want "unity" the new netbook interface. (Will not lose anything will have choice of both
desktop and unity at login screen:
#Open a terminal:
```
sudo apt-get install unity
```#Check for what you need by"
aptitude show "package name"
example:
```
aptitude show unity
```or 
```
aptitude show ubuntu-netbook
```#If have not got aptitude installed:
```
sudo apt-get install aptitude
```#Also good for upgrading in safe fashion:
```
sudo aptitude update && sudo aptitude safe-upgrade
```#Google aptitude in Ubuntu if you want to read more is a nice tool:

---

