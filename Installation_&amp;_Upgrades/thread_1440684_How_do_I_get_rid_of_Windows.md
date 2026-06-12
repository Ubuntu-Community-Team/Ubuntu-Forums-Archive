---
title: "How do I get rid of Windows?"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Paul2795 on 2010-03-27
I am trying to install 9.10 on an Ipex Celeron 500 I was given. It has Windows XP on it, which I want replace with 9.10, but the problem is, it is taking up too memory for the 9.10 installation to work and will have to be cleared from the hardrive before the 9.10 installation can go ahead. Can anyone help?

---

### Post by kvarley on 2010-03-27
If you have **backed up all your data**, run the live disc, open up terminal and type:

> sudo gparted

GParted will let you format your hard drive and then the installer will have space.

---

### Post by zvacet on 2010-03-27
>  it is taking up too memory for the 9.10 installation to work 

How much ram do you have?Maybe you can try something lighter like [Xubuntu.]("http://www.xubuntu.org/")

---

### Post by Mark Phelps on 2010-03-27
> **Paul2795 said:**
> I am trying to install 9.10 on an Ipex Celeron 500 I was given. It has Windows XP on it, which I want replace with 9.10, but the problem is, it is taking up too memory for the 9.10 installation to work and will have to be cleared from the hardrive before the 9.10 installation can go ahead. Can anyone help?

Unless you're trying to install Ubuntu INSIDE XP using Wubi, memory has nothing whatsoever to do with it.  You're confusing memory with disk space.

Just boot from the Ubuntu CD and choose the "Use entire disk" option.  That will reformat your hard drive and use it all for Ubuntu.

---

