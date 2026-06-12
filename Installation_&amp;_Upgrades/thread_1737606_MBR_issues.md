---
title: "MBR issues"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Dovelea on 2011-04-23
Have been using Ubuntu on external Hard drive and windows7 on a Acer laptop.

Today windows did some upgrade which I left running while I went out, Laptop re-booted in to Acer erecovery mode. I was able to access command prompt via windows install and re-installed MBR for windows 7, laptop now works fine.

The external drive when plugged in does not start with dual boot but error of no operating system, how do I get windows to now recognise my external Ubuntu drive ?

Many thanks in advance.

---

### Post by Hedgehog1 on 2011-04-23
You will need to reinstall GRUB, as the windows update overwrote the MBR (as you guessed by the thread title :D )

Please boot off your LiveCD/LiveUSB, select 'TRY'

Determine what partition holds your Ubuntu root.  In the examples below, they assume that /dev/sd**a5** is your Ubuntu partition.  Yours may be /dev/sd**b5** or /dev/sd**a3** or /dev/sd**b3** or whatever...  Use that.  Also note that your drive MAY be /dev/sd**b**.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

---

