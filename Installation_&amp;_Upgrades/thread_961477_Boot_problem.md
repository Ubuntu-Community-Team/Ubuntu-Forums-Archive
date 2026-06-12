---
title: "Boot problem"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by richsheil32 on 2008-10-28
Silver surfer never done this before. I have down loaded Ubunta 8.04 burnt it to a CD using Nero as a Data disc.Have fitted second HD to my computer. I bought a book Linux in Easy steps but the disc wont boot into ubunta it just keeps loading XP. My emai [email]richsheil32@merseymail.com[/email] Please help. Richard

---

### Post by Pumalite on 2008-10-28
Boot your Live CD; go to the Terminal and type:
sudo fdisk -lu
('Enter')
Copy and paste the output here

---

### Post by richsheil32 on 2008-10-28
Sorry do not understand Terminal Richard

---

### Post by caljohnsmith on 2008-10-28
Can you boot any CD from your CD/DVD drive? If not, you may need to set your BIOS to boot your CD/DVD drive before your Windows drive.

---

### Post by Pumalite on 2008-10-28
To access BIOS; hit 'Del' or 'Tab' repeatedly at boot. Once in BIOS; go to 'boot' and change the boot order, making CD/DVD first

BTW, Applications>Accessories>Terminal

---

### Post by richsheil32 on 2008-10-28
Boot order is CD first. Couple of weeks ago I down loaded Ubuntu 8.04 And Damn Small Linux and successfully loaded both not at the same time. I removed DSL. I then bought a new 60Gig HD as Master and the old 5Gig  HD as Slave. Re installed XP on Master. Tried installing Ubunta on 5Gig which computer had recognised as drive (I) wouldnt boot. Downloaded Ubuntu again from Ubuntu web site. Still wont boot. Would appreciate any help Regards Richard

---

### Post by Pumalite on 2008-10-28
With 256 MB of RAM or less; try Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

### Post by oilchangeguy on 2008-10-28
> **richsheil32 said:**
> Silver surfer never done this before. I have down loaded Ubunta 8.04 burnt it to a CD using Nero as a Data disc.Have fitted second HD to my computer. I bought a book Linux in Easy steps but the disc wont boot into ubunta it just keeps loading XP. My emai [email]richsheil32@merseymail.com[/email] Please help. Richard

you need to burn it as an iso file. NOT a data disc.

---

### Post by richsheil32 on 2008-10-28
how do I burn an ISO File Please

---

### Post by Pumalite on 2008-10-28
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

