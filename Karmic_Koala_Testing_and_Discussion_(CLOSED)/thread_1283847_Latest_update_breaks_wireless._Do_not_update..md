---
title: "Latest update breaks wireless. Do not update."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Grimhound on 2009-10-06
The latest set of upgrades have broken the ability of my laptop to connect to wireless networks. It refuses to connect automatically, and when given direction to connect the method of connection freezes and becomes unresponsive. The Broadcom wifi works by detecting the network and reading as active, yet there is no ability to create a connection.

I really wish they would stop rolling out updates that break half the system every other day. I understand it's a beta, but how are they going to ever manage a stable release for the end of October when there isn't even the illusion of stability or coordination in development? So now in 9.10: CDs, media files, and wireless are nonfunctional. I'm nearing the end of my ability to remain patient.

---

### Post by Bucky Ball on 2009-10-06
Karmic is 'testing'. If you want stability you never should have installed it. 8.04 LTS is rock solid for production machines (advisable) and any machine you need to be stable.

---

### Post by Grimhound on 2009-10-06
> **Bucky Ball said:**
> Karmic is 'testing'. If you want stability you never should have installed it. 8.04 LTS is rock solid for production machines (advisable) and any machine you need to be stable.

I installed it to help in working out the kinks via stress testing and reporting. I just find that day to day things are broken and fixed in a cyclical manner.

---

### Post by slakkie on 2009-10-06
> **Bucky Ball said:**
> Karmic is 'testing'. If you want stability you never should have installed it. 8.04 LTS is rock solid for production machines (advisable) and any machine you need to be stable.

Well, it is good that he notifies others so they can validate the problem and are aware of possible b0rkage.

@OP, please file a bug.

---

### Post by Grimhound on 2009-10-06
> **slakkie said:**
> Well, it is good that he notifies others so they can validate the problem and are aware of possible b0rkage.

@OP, please file a bug.

How do I go about filing an independent bug report without a prompt? Been having an issue with that.

---

### Post by slakkie on 2009-10-06
> **Grimhound said:**
> How do I go about filing an independent bug report without a prompt? Been having an issue with that.

Please read this section: [https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

---

### Post by Grimhound on 2009-10-06
Fixed. See: [http://ubuntuforums.org/showpost.php?p=8059630&postcount=3](http://ubuntuforums.org/showpost.php?p=8059630&postcount=3)

---

### Post by Kapitän Rotbart on 2009-10-06
Did you try a live session of Jaunty to make sure that it was an 'update' that broke WLAN compatibility and not a hardware failure? If you cannot connect in the live session, then it might be hardware. You could also boot a pre-update kernel build from Grub and if that fixes it, just change the defaults in Grub.

---

### Post by blakamin on 2009-10-06
> **Kapitän Rotbart said:**
> Did you try a live session of Jaunty to make sure that it was an 'update' that broke WLAN compatibility and not a hardware failure? 

It's a known bug in network-manager....

---

### Post by DougieFresh4U on 2009-10-06
Haven't updated this partition since yesterday morning. This is what it currently wants to do. I'm gonna wait on this as not sure of the ones it wants to remove. 
There's about 160 to upgrade.

[B]```
The following NEW packages will be installed:
  libode1{a} libpst4{a} python-mmkeys{a} 
The following packages will be REMOVED:
  libcloog-ppl0{u} libgmpxx4ldbl{u} libode0debian1{u} libppl-c2{u} libppl7{u} 


```[/B]

---

### Post by Bucky Ball on 2009-10-06
That's the lucky dip of 'testing' isn't it? Don't know if updates will fix or break?? ... and if that bothers you then ... maybe you should have a stable install like 8.04 on one partition and a 'testing' partition with Karmic for playing with. If you are worried about breaking a 'testing' release I don't get it and makes me wonder why people don't go for a more stable release if breaking is an issue ... :-k  :)

If you want 'cutting edge' be prepared to bleed a little!

---

### Post by rogerdean on 2009-10-06
I think it's fixed now. I just updated and all is well

---

