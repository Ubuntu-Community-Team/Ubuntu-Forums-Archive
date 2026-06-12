---
title: "Ubuntu installation"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by Haji Akhundov on 2008-03-07
I can't install ubuntu because i get this X server error all the time... what is that? can somebody  help me?  :confused:

---

### Post by prshah on 2008-03-07
Please give more information: Hardware, Ubuntu version and exact error message

Cheers,
PRShah

---

### Post by Haji Akhundov on 2008-03-07
The error is: Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. 
My version is: 6.06 LTS
Hardware:
 HP Pavilion dv9500 Notebook PC
Intel Core2 Duo 2.2Ghz
Ram: 2GB
Nvidia GeForce 8600M GS

---

### Post by wpshooter on 2008-03-07
Are you trying to install from the Desktop (live CD) version or from the ALTERNATE (text based CD) version ?

First of all I would suggest that you move up to Gutsy 7.10 instead of Dapper 6.06.

---

### Post by uberlube on 2008-03-07
> **wpshooter said:**
> Are you trying to install from the Desktop (live CD) version or from the ALTERNATE (text based CD) version ?

First of all I would suggest that you move up to Gutsy 7.10 instead of Dapper 6.06.

+1

---

### Post by prshah on 2008-03-08
setup your X using "sudo dpkg-reconfigure xserver.xorg" not sure if it works in 6.06... as suggested, better to uprade to 7.10
Cheers,
PRShah

---

### Post by Haji Akhundov on 2008-03-10
thanks alot. i will try that.

---

