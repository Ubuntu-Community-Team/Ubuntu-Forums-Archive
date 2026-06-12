---
title: "Live CD, Tecra 8000"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by kimusabi on 2007-08-18
Heya,

I'm attempting to install 6.06 (Dapper) on my Toshiba Tecra 8000. It's been done before with Feisty (little unsure how though...I was tired at the time).

It tends to do well up and until loading the hardware modules, or some such. I've tried some boot parameters (noapic and others) yet that only results in a slower boot time.

So..ideas please? :)

---

### Post by Pumalite on 2007-08-18
What are the specifications of a Toshiba Tecra 8000?

---

### Post by kimusabi on 2007-08-18
> **Pumalite said:**
> What are the specifications of a Toshiba Tecra 8000?

CPU: PIII
RAM: 128MB
HDD: 20GB
GPU: Neomagic I think.

---

### Post by floke on 2007-08-18
I've successfully installed Feisty on this machine - but needed to use the alternative installer - all worked fine though.

---

### Post by kimusabi on 2007-08-18
> **floke said:**
> I've successfully installed Feisty on this machine - but needed to use the alternative installer - all worked fine though.

Aye? Mind telling me how you did so? That -is- what this thread is about :mrgreen:

---

### Post by floke on 2007-08-18
Well I just ran the alt (text based) installer - allowed it to use the whole drive - and all's peachy!

---

### Post by floke on 2007-08-18
My bad - I think it was an 8200 not the 8000 - but I think the hardware's the same - except the 8200 has wireless.

---

### Post by Pumalite on 2007-08-18
With that amount of memory I would advise you to install Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
It will install easier and it will run faster in your system.

---

### Post by kimusabi on 2007-08-18
The alt installer? I assume you mean a different ISO where it doesn't boot into the live session? if so I'm a little stuck at that...no free CDs to burn laying around xX.

---

### Post by Pumalite on 2007-08-18
You could attempt booting and installing from Live CD by making a 500 MB swap partition ahead of time.

---

### Post by kimusabi on 2007-08-18
> **Pumalite said:**
> You could attempt booting and installing from Live CD by making a 500 MB swap partition ahead of time.

I tried that. Thank Tux for GParted. 

But it hangs when booting from the Live CD when loading the Hardware Modules...I don't see how that would effect it..

---

### Post by Pumalite on 2007-08-18
It's then obvious that you need the Alternate CD. The OS doesn't like your graphics, your hardware or both. That's what the Alternate is for.

---

### Post by kimusabi on 2007-08-18
x_X. Looks like I'll have to wait till Tuesday to get some CDs then...fun.

---

### Post by logos34 on 2007-08-18
> **kimusabi said:**
> x_X. Looks like I'll have to wait till Tuesday to get some CDs then...fun.

Does you have windows installed or is it just a blank 20gb drive?

---

### Post by kimusabi on 2007-08-18
Apart from the partitions I made myself, it's all empty.

---

### Post by logos34 on 2007-08-18
the reason I asked is I was going to suggest an install from hard disk (not cd required), but you need windows or some version of linux already installed, so I guess that's out...

---

### Post by gn2 on 2007-08-18
> **kimusabi said:**
> Heya,

I'm attempting to install 6.06 (Dapper) on my Toshiba Tecra 8000. 

If it's a Tecra 8000, that's a Pentium2 machine and it may struggle.
.
Your best bet is to download the Alternative Xubuntu CD and use these instructions to install: 
[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

