---
title: "[SOLVED] Installing Ubuntu 8.04 on HP Pavilion 7360"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2008-06-26
I have an old computer made in 1997. Is there anyway Ubuntu 8.04 LTS could run on this computer? Or may be Ubuntu 7.04? I have a copy of 7.04. The BIOS can't boot the Ubuntu live cd.
HP Pavilion 7360, 200MHz Intel Pentium, 32MB EDO memory, 3.8GB hard drive, 16x CD-ROM drive, 33.6Kbps DSVD modem and 2MB EDO video memory.
Thankx for any help.

---

### Post by Pumalite on 2008-06-26
You could try a minimal install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by avtolle on 2008-06-26
If I read the initial post correctly, the computer has only 32 mb ram. Not too much is going to run too quickly (especially with a GUI) on that. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) might offer some help.

---

### Post by sjnovick on 2008-06-26
Try Puppy Linux or DSL (Damn Small Linux).

---

### Post by Spaceman9 on 2008-06-27
Pumalite thankx for the help. That might be the only thing I can do. First I need to make a floppy to boot the cd. I found this [https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager) but it says I need to use a file in Windows to make a boot floppy but I don't have Windows installed on any of my  computers. 

Avtolle thankx for the help. I suppose I don't need a GUI if I just network the old computer with the new computer.

Sjnovick thankx for the help. I know about Puppy and DSL but I really want to use Ubuntu if there's anyway I can. There's also another good, small, linux called Deli [http://www.delilinux.org/](http://www.delilinux.org/)

---

### Post by Spaceman9 on 2008-06-27
Ok, I tried to be a good linux user and find the answer on my own. I searched google for 2 hours and can't fine anything that works. 


I have an old computer that can't boot from a cd to save it's life so the question is how do I make a boot floppy for ubuntu 8.04? There must be some way to do it. Smart Boot Manager is useless because it needs a file from Windows “rawwrite” and I don't have windows on any of my computers. I also tried sbm.bin and it doesn't make a floppy boot disk either.

Is there a way to use bootcd or something else to make a bootable cd for an old computer?

Thankx for any help.

---

### Post by Pumalite on 2008-06-27
Check this. See if it helps you:
[http://packages.ubuntu.com/hardy/klibc-utils-floppy-udeb](http://packages.ubuntu.com/hardy/klibc-utils-floppy-udeb)

---

### Post by Spaceman9 on 2008-06-27
Pumalite thankx for the help but there's a warning on the page:

Warning: This package is intended for the use in building debian-installer images only. Do not install it on a normal Ubuntu system.

Just between you and me this is really driving me nuts. I wonder what IT people do when they have to install linux on an old computer? I bet they buy a new motherboard LOL.

I was thinking tonight an old computer has a way of making a new laptop look like a really good idea. :-)

---

### Post by esbo on 2008-06-28
> **Spaceman9 said:**
> I have an old computer made in 1997. Is there anyway Ubuntu 8.04 LTS could run on this computer? Or may be Ubuntu 7.04? I have a copy of 7.04. The BIOS can't boot the Ubuntu live cd.
HP Pavilion 7360, 200MHz Intel Pentium, 32MB EDO memory, 3.8GB hard drive, 16x CD-ROM drive, 33.6Kbps DSVD modem and 2MB EDO video memory.
Thankx for any help.


I have a HP pavillion although much newer (sempron 3000) and I could not run the live CD ((8.04?), I could run 7.10 though.
Tried to wupu? 8.04 but it fell over in a heap.
Another guy with a similar machine (I think had similar probs but he could not 
even run 7.10).

---

### Post by Spaceman9 on 2008-06-28
> **esbo said:**
> I have a HP pavillion although much newer (sempron 3000) and I could not run the live CD ((8.04?), I could run 7.10 though.
Tried to wupu? 8.04 but it fell over in a heap.
Another guy with a similar machine (I think had similar probs but he could not 
even run 7.10).

esbo thankx for your help. Ok, I'm marking this thread SOLVED. Solved because I'm buying a laptop.

---

### Post by Pumalite on 2008-06-28
That is called progress.
Good luck!

---

### Post by Spaceman9 on 2008-06-28
> **Pumalite said:**
> That is called progress.
Good luck!

It's also called MasterCard :-)

---

