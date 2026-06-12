---
title: "Install Karmic Koala to HDD via USB Drive - Possible?"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by aCROX999 on 2010-02-11
I want to install Ubuntu to HDD via USB drive but I can't see my HDD. Only the USB drive is there. I don't have any CD left to burn the ISO, so USB drive is my only choice.

Help me please.

---

### Post by darkod on 2010-02-11
Are you running raid or has this hdd ever been used in raid?

---

### Post by aCROX999 on 2010-02-11
I'm not sure. I'm new to this thing. Can you explain more briefly?

Thanks. :)

---

### Post by darkod on 2010-02-11
RAID is a kind of setup where you use 2 or more drives for data redundancy or speed. 9.10 can detect raid settings and usually that is when the installer is not showing a hdd. Even if it is not right now used in raid, if it ever was, there is a chance for that to be the issue.

Boot with the usb stick, Try Ubuntu option, and if you have only one hdd, in terminal do:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

That should remove the raid settings and it should sort out the problem (if that was it).

NOTE: DO NOT run these commands if you are running a raid array, it will destroy the array.

---

### Post by aCROX999 on 2010-02-11
How can I know if my HDD has RAID or not?
 
Thanks. :)

---

