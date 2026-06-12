---
title: "Install Problems"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by Anthony Timberlake on 2012-03-23
I am trying to install Ubuntu using Wubi (I previously had an install, something went wrong and I'm trying to install again).  I get to the point where it is extracting and installing, then an error pops up (I've repeated this 3 times now).

What is wrong?  I have tried to get to the error log, but it seems to have deleted before I can get to it.

---

### Post by ranger1021994 on 2012-03-23
> **Anthony Timberlake said:**
> I am trying to install Ubuntu using Wubi (I previously had an install, something went wrong and I'm trying to install again).  I get to the point where it is extracting and installing, then an error pops up (I've repeated this 3 times now).

What is wrong?  I have tried to get to the error log, but it seems to have deleted before I can get to it.

U can instead burn image to USB drive using Unetbootin....
It maybe Wubi error or sumthing...but UNetBootIn is nice utility :) :)

---

### Post by Anthony Timberlake on 2012-03-23
> **ranger1021994 said:**
> U can instead burn image to USB drive using Unetbootin....
It maybe Wubi error or sumthing...but UNetBootIn is nice utility :) :)
I will try this and get back to you.  Thanks.

---

### Post by bcbc on 2012-03-23
> **Anthony Timberlake said:**
> I am trying to install Ubuntu using Wubi (I previously had an install, something went wrong and I'm trying to install again).  I get to the point where it is extracting and installing, then an error pops up (I've repeated this 3 times now).

What is wrong?  I have tried to get to the error log, but it seems to have deleted before I can get to it.
Probably bug [lpbug]862003[/lpbug]. Can't say for sure with the info provided but if it happened right at the end, and it's regarding x:\\wubildr (where x is some drive letter that's a protected or readonly drive) then that's the problem. So you'd just reboot to complete the install.

You can use a USB to install Ubuntu direct to disk or try it in live mode; but not to install Wubi. Wubi is more for trying out Ubuntu and is safe and easy to uninstall.

---

