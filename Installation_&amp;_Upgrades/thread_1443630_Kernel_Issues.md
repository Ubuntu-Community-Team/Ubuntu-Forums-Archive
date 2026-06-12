---
title: "Kernel Issues"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by biles on 2010-03-31
Does anyone have a kernel that supports Atheros network cards?  I am using ASUS EEE PC netbooks and none of the kernels I have access to have drivers installed for the NICs.  I am having issues when I try to build my own kernel and maybe someone has a precompiled one?  Either that or if someone has a basic, step-by-step guide to building your own custom kernel.  This is my first time building a kernel and I am kind of lost.  This isn't actually for running Ubuntu I will be using it in an imaging program called FOG.  I just need a kernel that will support these NICs so I am able to do some imaging.  Thank you for any help :)

---

### Post by ajgreeny on 2010-03-31
Lots of kernels support some Atheros cards, but it will depend on the particular card you have.  Certainly kernels from 9.04 and 9.10 support the AR242x 802.11abg Wireless PCI Express Adapter in my wife's laptop.

---

### Post by biles on 2010-03-31
I need to drivers to be preinstalled and they are for the ethernet card not the wireless.

---

### Post by Slim Odds on 2010-03-31
I have a pretty new laptop that has an Atheros gigabit network adaptor and it works fine with 10.04 (though I'm pretty sure that it has been supported for a while).

---

### Post by biles on 2010-04-05
Is there a way to tell which kernel you are using? like kitchensink, karmic, etc...

---

### Post by Slim Odds on 2010-04-05
> **biles said:**
> Is there a way to tell which kernel you are using? like kitchensink, karmic, etc...

the program called "uname" will tell you that

you probably want the -r option

---

