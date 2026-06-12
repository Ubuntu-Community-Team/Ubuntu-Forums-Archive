---
title: "How to install FileZilla on Ubuntu 9.10"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by affableindia on 2009-11-19
Hi, i'm Sridhar new to ubuntu. am familiar with MS Windows FileZilla so i tried to install with UBUNTU SOFTWARE CENTER, but its not getting install. i have downloaded source file but i don't know how to install. even i have tried (sudo apt-get install filezilla) its not working

Please help me out

---

### Post by phillw on 2009-11-19
Hi,

```
sudo aptitude install filezilla

```

Will go get it for you.

Regards,

Phill.

---

### Post by affableindia on 2009-11-19
> **phillw said:**
> Hi,

```
sudo aptitude install filezilla

```

Will go get it for you.

Regards,

Phill.
i have tried after installation of ubuntu, so filezilla is not getting installed on that time.

phillw i have tried as per your guidance after  restarting my laptop now its working fine. thank you so much

---

### Post by mickaelb on 2010-04-14
That not work for me on Ubuntu 9.10 so I post the solution I found :

(I have a message sounds like that after the "sudo apt-get" and the line aptitude doesn't work anymore (package non accessible))
> Reading package lists… Done
Building dependency tree
Reading state information… Done
E: Couldn’t find package filezilla

So I install "Ubuntu tweaks".
In this soft you have to go on "Programmes (Programs) >> Sources de logiciels (Software sources)". 
Select the program you want (here : Filezilla) clic on "Synchronize". 
Then go to the first option (of "Programs") named "Application Center", select the soft you want (here : filezilla) and clic on the button "Applicate".
It's now install you just have to go on the menu "Applications >> Internet >> FileZilla" on your desk board.

Many others applications are accessible in Ubuntu Tweaks, enjoy !

---

