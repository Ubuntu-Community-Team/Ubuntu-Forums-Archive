---
title: "Reverse Ubuntu Install?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by reo4ua on 2010-01-02
I dual installed 9.10 on my laptop with an existing xp install.  The ubuntu install was placed on a usb drive.  I somehow messed up my boot record and now I must have the usb drive attached to the laptop or I cannot boot ubuntu OR windows!

What I intended was to attach the usb drive when I desired a linux boot.  Otherwise, have the system automatically boot windows.  

Is there an easy way for a non-techie to reverse this install then reinstall to make it work in the way intended above?

Thanks!

---

### Post by iponeverything on 2010-01-02
You need to go into the XP recovery console and run the utility:

```
fixmbr
```

Use google to find good set of instructions on how to do this..

---

### Post by haribol707 on 2010-01-02
Look up the forum on instructions for how to install grub in ubuntu. That should solve your problem.

> **iponeverything said:**
> You need to go into the XP recovery console and run the utility:
  
```
fixmbr
```Use google to find good set of instructions on how to do this..

---

