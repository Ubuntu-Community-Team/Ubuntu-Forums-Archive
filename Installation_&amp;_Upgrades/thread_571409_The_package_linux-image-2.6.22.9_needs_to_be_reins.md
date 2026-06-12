---
title: "The package linux-image-2.6.22.9 needs to be reinstalled, but I can't find an archive"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by isidro on 2007-10-09
Hi All,

Am installing Beryl on Feisty according to HowToForge instructions. Everything goes fine until I get:

hans@hans-desktopbis:~$ sudo apt-get install beryl beryl-manager emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.22.9 needs to be reinstalled, but I can't find an archive for it.

How do I replace/install this file??

Thanks in advance!!!

---

### Post by MetalMusicAddict on 2007-10-09
Isnt that a Gutsy kernel? And I dont think it exists there anymore either.

---

### Post by isidro on 2007-10-09
A generic feisty kernel update via Kernelcheck was attempted but aborted (power outage!). I understand the update is not installed unless the process is fully completed.
I have to figure out how to determine what kernel I'm using without rebooting. Will revert to the list!

---

### Post by isidro on 2007-10-09
the kernel is 2.6.20-16 generic

cheerio

---

### Post by master_kernel on 2007-10-10
Seems like you have to clear the linux-image-2.6.22.9 file out of the apt cache.

---

### Post by brendonsoh on 2007-10-13
I HAVE THE SAME PROBLEM!!!

I've been having it for a few months....I cant install anything new because that shows up whenever I open any type of package manager (Apt, add/remove programs, synaptic)

It would be really helpful if someone could tell me how to get rid of it

---

### Post by jedthehumanoid on 2007-11-01
Ok, i just had the same problem. Found a solution and thought I'd post it here.

First of all try with: 
```
sudo dpkg -r linux-image-2.6.22.9 
```
if that doesn't work (probably won't) you'll have to force it:
```
sudo dpkg -r --force-remove-reinstreq linux-image-2.6.22.9
```

PS.BE CAREFUL not to force removal of linux-image-2.6.22-whatever-kernel-you're-actually-using
because tab-completion will automagically suggest that one =)
(didn't try, but I'm guessing it's not good) :)

---

