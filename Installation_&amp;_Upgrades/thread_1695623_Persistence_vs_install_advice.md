---
title: "Persistence vs install advice"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by teachop on 2011-02-26
I have an Eee PC with a dead Hdd.  I brought it back to life by installing Ubuntu 10.10 on a 16GB SD card.  It works 100% but is sluggish.

Now I am wondering, from the standpoint of reducing SD card access and writes, would it have been better to create a Live Disc on the SD card with persistence options?  What I am thinking is that a Live Disc is designed to run out of RAM, and would thus reduce the activity on the SD card.

The only thing this netbook will get used for is the internet.  It is a netbook, so the performance is limited, but as far as netbooks go, it is top of the line with dual core and discrete nvidia graphics.

---

### Post by ajgreeny on 2011-02-26
An SD card is always going to be slow compared with an SSD drive, as they are not really made for that purpose.  However, I think you are correct that a persistent live installation would reduce the write cycles, though I also think there are ways to edit the /etc/fstab file in a full install to reduce them as well, by using the **noatime** option.

Have a look at [https://help.ubuntu.com/community/AspireOne/110L](https://help.ubuntu.com/community/AspireOne/110L) where there is a section on SSDs; not an EeePc but still relevant.

---

### Post by teachop on 2011-02-26
> **ajgreeny said:**
> ... there are ways to edit the /etc/fstab file in a full install to reduce them as well, by using the **noatime** option.

Have a look at [https://help.ubuntu.com/community/AspireOne/110L](https://help.ubuntu.com/community/AspireOne/110L) where there is a section on SSDs; not an EeePc but still relevant.
Thank you for the link, good stuff!  I have edited fstab as recommended there, while I ponder switching to a persistent live install.

---

