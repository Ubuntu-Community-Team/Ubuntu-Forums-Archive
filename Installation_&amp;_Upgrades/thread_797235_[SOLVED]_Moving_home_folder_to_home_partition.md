---
title: "[SOLVED] Moving home folder to /home partition"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by DachaArh on 2008-05-17
I have 8.04 installed via easy install (wubi) and  wan't to move my home folder to home partition, bacause I wan't to install ubuntu again - full installation.
I have freed one hard drive partition to be home partition 70GB. and formated it via **gparted live Cd**.
Now when i eneter ubntu I see  that partition but I can't write on it, and on properties it says permissions can't be determinated.
I tried to install gparted in ubuntu and format it again but I can't do anything with partitions in gparted, and I typed gksudo gparted but it's still the same.
Can someone help me start using that partition, so I can move all my home there, and then fuly install ubutnu.


And one more question, can I have my ubuntu fully installed and then to resize some partition, without loosing data ?

---

### Post by iaculallad on 2008-05-17
For moving your home folder, visit [this]("http://ubuntuforums.org/showthread.php?t=147299").

Yes, you can resize partitions. But if you mean resizing your root (/) partition, you could do this outside of your normal boot environment. Try using GParted which comes with your Ubuntu LiveCD.

~ Caution: Make sure you backup all your important staffs before trying to resize partitions.

---

### Post by DachaArh on 2008-05-17
if I copy all to new /home partition and then try to install ubuntu will I lose all my data from /home?

thanks ?

---

### Post by iaculallad on 2008-05-17
> **DachaArh said:**
> if I copy all to new /home partition and then try to install ubuntu will I lose all my data from /home?

thanks ?

Install Ubuntu first then move/copy your home-folder to your new /home-folder.

---

### Post by DachaArh on 2008-05-18
this is solved
I have managed to install ubutnu ;)

---

