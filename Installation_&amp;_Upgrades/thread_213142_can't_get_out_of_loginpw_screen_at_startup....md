---
title: "can't get out of login/pw screen at startup..."
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by sk0r on 2006-07-10
I am new to ubuntu, and linux as a whole, really...so i installed dapper 6.06 today, things were going smoothly.  Installed "easy ubuntu", checked what i wanted installed.  nice and easy, as the name implies.  so i reboot...enter my login/password as usual...it ACTS like it is going to boot normally, then takes me back to the login/pw screen.  madness.

p4 3.4
1GB RAM
Nvidia 6600GT
160GB sata HDD

any help would be MOST appreciated!

-ron

---

### Post by sgbeamer on 2006-07-10
Most likely a password typo / caps lock or something similar.  It happened to me once.  The easy way is re-install.  The faster, more complicated way is to boot of the cd and do the following once it is up and running from the cd:

Open a terminal window (looks like a DOS prompt icon on the toolbar)

type   "sudo bash"  (this will make you root)

mount your hard disk 
   mkdir /mnt/sda1 (SATA HDD)
   chroot /mnt/sda1
   passwd your_username

you will be prompted to enter your password twice

reboot

---

