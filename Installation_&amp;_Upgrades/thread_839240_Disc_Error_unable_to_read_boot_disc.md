---
title: "Disc Error unable to read boot disc"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by MarkUK on 2008-06-24
Got a little problem thats begining to anouy me badly

I have downloaded 3 copies of 8.04 and burned to 3 different types of media , burning completes fine i can install alongside windows XP Pro from the CD , but it don't seem to want to install . Once i boot from the cd the grub menu comes up , each method i choose gives me "Unable to read data on disc" reboot. same error on check media option as well:confused:

2 writers i have tried , an upto date drive in my laptop and an oldish one on my desktop . 

Beats me , would be greatfull if anyone has any ideas 

Cheers
Mark

---

### Post by Pumalite on 2008-06-24
Do md5sum, burn at 4x or less, clean the lens in your burner, make sure you are burning the iso as 'image' and not as 'data'

---

### Post by MarkUK on 2008-06-24
> **Pumalite said:**
> Do md5sum, burn at 4x or less, clean the lens in your burner, make sure you are burning the iso as 'image' and not as 'data'


How do i do the md5sum ? , don't mean to sound too noobish , but never had to do this before 

Cheers
Mark

---

### Post by Pumalite on 2008-06-24
[http://etree.org/md5com.html](http://etree.org/md5com.html)
7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

---

