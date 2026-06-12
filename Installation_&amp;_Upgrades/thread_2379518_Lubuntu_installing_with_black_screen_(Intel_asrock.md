---
title: "Lubuntu installing with black screen (Intel asrock p4vm800)"
date: 2017-12-06
forum: Installation &amp; Upgrades
---

### Post by skifua on 2017-12-06
I try to install Lubuntu 17.04 on Intel asrock p4vm800. After choosing "Try lubuntu" I see black screen with red lines on the half of my display. I tried to write nomodest in boot line but it's start also with black screen.  
What I can to do? 
(sorry for my english - it is no my native)

---

### Post by mörgæs on 2017-12-06
This and similar cards are losing support:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/)

As you can see there is a reason why it's deprecated. If you want you can probably install 16.04 but it might be a security breach.

---

### Post by skifua on 2017-12-06
> **mörgæs said:**
> This and similar cards are losing support:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276/)

As you can see there is a reason why it's deprecated. If you want you can probably install 16.04 but it might be a security breach.
thank you, I'll try to install 16.04. 
Buy the way - latest version of Puppy has the same problem.

---

### Post by mörgæs on 2017-12-06
Yes, everything using kernel 4.10 or above has.

---

### Post by skifua on 2017-12-08
> **mörgæs said:**
> 
As you can see there is a reason why it's deprecated. If you want you can probably install 16.04 but it might be a security breach.
today I try to do it, but I saw next problems:
[ATTACH=CONFIG]277769[/ATTACH]
this is my CPU [ATTACH=CONFIG]277770[/ATTACH]
and finally [ATTACH=CONFIG]277771[/ATTACH]

p.s.Now there is winXP on this PK with squid. I need only squid and epoptes on this pk (it will be work without monitor). Maybe there is another linux, that i can install and it will work only as proxy server in local network.

---

### Post by mörgæs on 2017-12-09
With only 0,5 GB of memory It might be better to try the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

---

### Post by skifua on 2017-12-10
> **mörgæs said:**
> With only 0,5 GB of memory It might be better to try the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").
Can it works if it has hardware errors? I can try it tomorrow on my work

---

### Post by mörgæs on 2017-12-11
Sorry, though Lubuntu can do a lot of good stuff it can't fix hardware errors.

---

### Post by skifua on 2017-12-11
> **mörgæs said:**
> With only 0,5 GB of memory It might be better to try the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").
success! Today was start Lubuntu. Thank you for help) 
[ATTACH=CONFIG]277808[/ATTACH]

---

### Post by mörgæs on 2017-12-12
Good but please remember that there is a reason why the drivers were removed from 17.04 onwards. You are less secure than normal when running this software.

---

