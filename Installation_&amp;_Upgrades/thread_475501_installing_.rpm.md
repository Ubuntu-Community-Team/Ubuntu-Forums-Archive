---
title: "installing .rpm"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by JLoomis95 on 2007-06-16
I have a file .rpm and dont know how to install it. can anyone help? thank you.

---

### Post by Anonii on 2007-06-16
RPM files are software packages similar to the Debian (.deb) packages in Ubuntu. 

There are applications that can convert them in .deb for easier installation in APT based distros. Read the following guide:
[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)


Good luck.

---

### Post by JLoomis95 on 2007-06-16
thanks

---

### Post by jim_p on 2007-06-16
Since Ubuntu accepts only .deb installation packages, you have to convert it from rpm to deb using alien. 
Install alien with```
sudo apt-get install alien
```

After that you can install the .deb file using Gdebi package installer


(once again... i was too slow)

---

