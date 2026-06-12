---
title: "Windows 7 running super slow after 12.04 install"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by Gilbt on 2012-11-24
Hi everybody,
I installed ubuntu 12.04 using the "alongside windows 7" option.
It used unpartitioned space to create its own partition and install ubuntu on it. (about 8 gb)
it all worked great for about 24 hours, and then all of a sudden my windows 7 works super slow (up to a point that i just cant use it).
Do you have any idea why that happened? 
Ive read some posts but none of them helped.
I need my windowd 7 working :(

---

### Post by eyfrt on 2012-11-24
Did Windows get any updates before installing Ubuntu? I have noticed that there are some update on Windows 7 which causes slowness. I don't know what update that is, but I have solved that kind of problem  about five times by restoring windows.

---

### Post by Gilbt on 2012-11-24
> **eyfrt said:**
> Did Windows get any updates before installing Ubuntu? I have noticed that there are some update on Windows 7 which causes slowness. I don't know what update that is, but I have solved that kind of problem  about five times by restoring windows.

I restored windows, didnt help :/

---

### Post by monkeybrain2012 on 2012-11-24
Maybe you get a Windows virus.

---

### Post by Gilbt on 2012-11-24
> **monkeybrain2012 said:**
> Maybe you get a Windows virus.

very unlikely.

---

### Post by eyfrt on 2012-11-24
Is windows so slow in safe mode too?

---

### Post by Gilbt on 2012-11-24
> **eyfrt said:**
> Is windows so slow in safe mode too?

Ran some tests, it works ok in safe mode.
any ideas?

---

### Post by darkod on 2012-11-24
Not really. In a proper dual boot, like you have, with every OS on its own partition, once you select windows in the grub boot menu, it has nothing to do with ubuntu.

You better start some windows related troubleshooting including on their forums.

It might also be hardware related and it just happened to show when you installed buuntu by coincidence.

---

### Post by eyfrt on 2012-11-24
> **Gilbt said:**
> Ran some tests, it works ok in safe mode.
any ideas?

What about CHKDSK? But if the "failure" won't show up in safe mode, could it still be file system related problem? Is your keyboard/mouse working properly during slowness? No freezing etc...

---

### Post by Mark Phelps on 2012-11-24
> **Gilbt said:**
> Ran some tests, it works ok in safe mode.
any ideas?

Then, it's something that is being loaded when you are NOT running Safe Mode.

You will need to though a tedious procedure of enabling/disabling individual startup items until you find the one causing the slowdown.

If you want to clean up Win7, you should really check in a Windows 7 forum (sevenforums.com).

---

### Post by Gilbt on 2012-11-27
Ran chkdsk after removing ubuntu, 
Windows went back to working ok.
Ill reinstalll ubuntu soon and see how it goes.
Thank you everyone for your help!:)

---

