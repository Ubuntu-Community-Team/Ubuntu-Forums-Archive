---
title: "Can you boot ubuntu from a Cd with windows vista?"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Alx c on 2007-12-16
I have a DELL Inspiron 6400 windows vista home premium and im trying to install ubuntu (7.10). I downloaded and copied evrey thing corectly but when i restart the computer vista comes up (the cd is inside). Does any one know why? (Ive tryed the cd on a xp computer and it works but i what it on  the vista one).

---

### Post by Sukarn on 2007-12-16
When your computer is starting up, when the first screen appears, press the del key or the F8 key (different computers have different). This will bring up the BIOS.
Look for some setting related to boot priority. Set CD Drive to be the first and your HDD (Hard Disk Drive) to be the second.

---

### Post by Pumalite on 2007-12-16
First, allocate space for Ubuntu with the Vista partitioner. Then install Ubuntu, go Manual and in the space you have, make these partitions:
10 GB for '/'
2x RAM up to 1 GB for /swap(except laptops, where /swap=RAM)
The rest for /home
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
Your CD should be first in boot order in BIOS

---

### Post by Sukarn on 2007-12-16
Wait, you didn't extract the ISO and write its contents to a CD, did you?
You have to use a CD Writing software and choose to write a CD Image in the software and select the Ubuntu iso.

---

### Post by Pumalite on 2007-12-16
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Make sure you burn as 'image' and not as 'data'

---

