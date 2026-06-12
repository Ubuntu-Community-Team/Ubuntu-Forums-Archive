---
title: "How do I boot normally into 11.04?"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-05-12
I reinstalled ubuntu from the live cd.

Now I can not boot normally. I have to do boot via 2.6.38-8 not 9 which is in the grub.

I can only get into Ubuntu if I use recovery  failsafe low graphics mode.

If I use normal mode there is an error: gdm-binary: could not acquire name; bailing out.

**How can I stabilise the boot process so that i do not need to use recovery mode?**

---

### Post by Robbyx on 2011-05-12
I have it working by installing the nvidia drivers through update manager.

**Any ideas how to get to install the 2.6.38-9. i am only seeing -8 in synaptic, but my grub defaults to -9.**

---

### Post by coffeecat on 2011-05-12
At the moment kernel 2.6.38-8 is the latest released Natty version, so I don't understand how you got a -9 entry in grub. A question: do you have the proposed repository enabled? If you do, disable it. It's only for testing proposed packages, not all of which survive the QC process.

Also - open a terminal and run:

```
sudo update-grub
```That might make the spurious -9 grub entry disappear.

---

### Post by Robbyx on 2011-05-12
> **coffeecat said:**
> At the moment kernel 2.6.38-8 is the latest released Natty version, so I don't understand how you got a -9 entry in grub. A question: do you have the proposed repository enabled? If you do, disable it. It's only for testing proposed packages, not all of which survive the QC process.

Also - open a terminal and run:

```
sudo update-grub
```That might make the spurious -9 grub entry disappear.

I have disabled the proposed repository.

The sudo update-grub didn't work for me. Is there a way of deleting that entry?

---

### Post by Robbyx on 2011-05-12
Your advice now works. I had to delete the -9 image in /boot, first, and then run the grub update. 

Thanks for your help

---

