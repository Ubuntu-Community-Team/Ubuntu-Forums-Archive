---
title: "Installing programs in SD card"
date: 2020-01-03
forum: Installation &amp; Upgrades
---

### Post by etolocka on 2020-01-03
Hi good day!


I am testing lubuntu to install it on a cloudbook with Atom Z8350, a 32GB SSD and a 64GB SD card. It works fine (unless it does not have audio in the headphone output) but I have a doubt: will I be able to install lubuntu applications (for example libreoffice) on the SD card so that the SSD does not fill up? How would it be done?

Thankfully, 
Ernesto.

---

### Post by TheFu on 2020-01-03
Applications are stored in /usr/ , so if you make that a separate mount point and move everything over to a native-Linux file system, the underlying storage won't matter.  But I can't imaging loading so many applications that 32G would be sufficient.  For an OS, 25G should be overkill.  Just put other file systems like /home/ and /var/lib/ onto the other storage.  Of course, using SDHC will be slow and it will likely wear out within a year due to all the writes, but you can do this.  If the 32G gets full, why not just get a 128G SSD and replace it?

---

