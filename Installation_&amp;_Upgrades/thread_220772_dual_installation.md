---
title: "dual installation"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by paparucino on 2006-07-22
Hi guys,

I've a 250giga HD and since I think it's too much for ubuntu :) I tried to install Kubuntu. During the installation I was asked to resize the disk, I made it, but I wasn't able to put the / (root) on the second partition and Kubuntu wanted to overwrite the ubuntu partition.
How can I have 2 root mount points so to install other pieces of linux?

Denghiù

---

### Post by GuitarHero on 2006-07-22
You really dont need to do that.  Ubuntu and Kubuntu are essentially the same OS with a different Desktop Environment.  Just install ubuntu, then do sudo apt-get install kubuntu-desktop
Then you can select which DE you want to use at login.  Actually ive heard using aptitude instead of apt is best for this so you remove all the dependencies when you uninstall kubuntu if the need ever arises.

---

### Post by paparucino on 2006-07-22
> **GuitarHero said:**
> You really dont need to do that.  Ubuntu and Kubuntu are essentially the same OS with a different Desktop Environment.  Just install ubuntu, then do sudo apt-get install kubuntu-desktop
Then you can select which DE you want to use at login.

You're right, but suppose I want install Mepis o mandriva or ... the problem is there.
 
>  Actually ive heard using aptitude instead of apt is best for this so you remove all the dependencies when you uninstall kubuntu if the need ever arises.
Well.. I prefer synaptic

---

