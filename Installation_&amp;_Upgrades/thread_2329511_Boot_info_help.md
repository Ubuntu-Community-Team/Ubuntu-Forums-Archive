---
title: "Boot info help"
date: 2016-07-02
forum: Installation &amp; Upgrades
---

### Post by uchia on 2016-07-02
Hello, 
Can someone please help me fix this boot issue. Following is the boot info link : [http://paste2.org/K5M5c6OC](http://paste2.org/K5M5c6OC)
Tried with Boot Repair using a live CD and it doesn't seem to be any help.
BTW I am ending up in the grub recovery>  prompt and says no file found eventhough i have istalled ubuntu16.04 successfully. I tried with creating a separate /boot partition at start. No help.

Thanks.

---

### Post by oldfred on 2016-07-02
It looks like you did not have Internet working when you ran Boot-Repair. It needs to download new copy of grub from repository. And maybe new kernels.

Best to use Wired Ethernet for install & initial updates.

Boot-Repair also commented out the /boot partition. But then needs to reinstall grub & kernel into /boot folder in / (root). 
 I do not normally suggest having the separate /boot partition as that is one more smaller partition that you have to maintain and watch size on.

Make sure Internet is working and rerun Boot-Repair.

---

