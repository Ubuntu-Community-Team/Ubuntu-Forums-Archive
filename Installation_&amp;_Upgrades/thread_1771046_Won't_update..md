---
title: "Won't update."
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by palz2015 on 2011-05-30
I've been having an issue for a long time where Update Manager and Software center simply don't load, it's a segmentation fault in console. I've tried everything, but they just don't load. Now I'm getting "update to natty" messages, and today I clicked update. It starts to update, then just closes! What can I do to update my system?

---

### Post by mörgæs on 2011-05-30
Please boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

and post the error messages, if any.

---

### Post by palz2015 on 2011-05-31
I ran those commands and it updated me to natty (I think). Now my keyboard and trackpad don't work :O. This is a Toshiba Tecra M2.

EDIT: i can get into recovery mode if need be. its when I start the GUI they fail.

---

### Post by mörgæs on 2011-06-01
There have been a number of reports on these kinds of error in 11.04. 

I can not help with this, as I am staying with 10.10, but there are many threads on this topic.

---

### Post by irish newbie on 2011-06-17
i've also had this problem and after searching the web found this

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

alls as should be now

---

### Post by erikthedrink on 2011-06-18
sudo rm /var/lib/apt/lists/* -vf

This alone fixed the problem for me.  Using 10.10.
:D

---

