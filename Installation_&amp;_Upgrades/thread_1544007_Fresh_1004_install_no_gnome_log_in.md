---
title: "Fresh 10:04 install no gnome log in"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by ryan on 2010-08-01
I just setup a Fujitsu s6231 lifebook with Lucid. When I boot there is no grub menu unless i press the "start" key. Then the only way i can get into the machine is by entering into recovery mode and booting in "safe graphics mode".

Everything works fine once I am able to log on the "safe graphic mode".

If i don't press the "start" key the ubuntu logo will flash for 3 seconds and then the screen goes blank and nothing happens. Any ideas what the problem is and what I can do about it ? tks.

The video card is an Intel 82852/855GM

---

### Post by ryan on 2010-08-02
I found this enrty in the wiki which I will try. 

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Seems this should work as it deals specfically with the intel 855 GM chipset. just came out 3 days ago. Just need to get to a command line with network support to add to my sources list and do the update.

---

### Post by ryan on 2010-08-03
> **ryan said:**
> I found this enrty in the wiki which I will try. 

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Seems this should work as it deals specfically with the intel 855 GM chipset. just came out 3 days ago. Just need to get to a command line with network support to add to my sources list and do the update.
Fixed everything runs great

---

### Post by ryan on 2010-08-03
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

works like a charm:D

---

