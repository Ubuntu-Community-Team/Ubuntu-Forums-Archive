---
title: "Can't add an Ubuntu network printer in windows XP"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by Prisma on 2007-08-09
I have an Ubuntu 7.04 Box with a HP printer installed which prints perfectly. My wife have a XP laptop. I can't add the Linux printer in Windows XP. The laptop is able to see my Ubuntu Box but I am getting an error message in XP stating that there is no printer attached to my Ubuntu Box. Does anybody know how to do this? :confused:

Thanks

---

### Post by hamstersquasher on 2007-08-09
If the printer is physically attached to your linux box then I believe you will need to install Samba.  Samba is relatively easy to install and allows for Windows clients to access file and print shares located on a linux box using the SMB/CIFS protocol that Windows likes.

---

### Post by Gary.M on 2007-08-09
Cups will share it... and its already installed. Search these forums for Cups printer share or similar.

---

