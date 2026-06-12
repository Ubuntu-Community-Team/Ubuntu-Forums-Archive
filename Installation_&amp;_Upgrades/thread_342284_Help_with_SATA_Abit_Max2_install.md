---
title: "Help with SATA Abit Max2 install???"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by nfear24 on 2007-01-19
I need help getting Ubuntu Edgy 6.10 installed on my Abit Max2 sata board.  It has an onboard Highpoint controller for the sata.  HPT374.    I use Ubuntu for my mail server and webserver and desktop everywhere, but for some reason I cant get it installed on my sata drive.  I dont have raid setup with it.  Just a single sata drive.  It almost gets through the install everytime untill it gets to the grub install.  It trys to right the grub by default to hd0 and its the only drive in the machine right now.  What should I do.  I have searched the forums, but havnt got a working answer.  

Thanks

Nick

---

### Post by nfear24 on 2007-01-20
Man this sucks, still no go for me on the SATA.  I can successfully install if I put in a old ata drive but I sure would like if I could successfully install to a sata.  Ive tried everyting and install keeps failing with grub.  I somehow need to come up with something other than (hd0) ect....  I have tried many to no avail.

Nick

---

### Post by chrismine on 2007-01-20
Did you try sda1?

---

### Post by nfear24 on 2007-01-20
> **chrismine said:**
> Did you try sda1?

Yep and I still a no go.

Thanks Nick

---

### Post by nfear24 on 2007-01-20
If I manually prepare the partitions during boot,  I will create and setup '/' and also a swap.  Then after I create those it goes to the next screen where I select a mount point and partition, but the partion select box is always blank.  I can select '/' but the drop down box next to it is blank.  I cant select a partion from the drive to it.

---

