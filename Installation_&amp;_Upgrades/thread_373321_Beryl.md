---
title: "Beryl"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by nerds in parties on 2007-03-01
hello there. I am trying to install Beryl but I have this problem:

$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl

Any suggestions?

(ubuntu 6.10 - i386 - ati radeon x1600)[B]


EDIT:[/B] I installed it and now I can open the beryl-manager. but i saw no difference in the environmnet so i typed to the terminal "Beryl" and look what i got:

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by lukew on 2007-03-01
> **nerds in parties said:**
> hello there. I am trying to install Beryl but I have this problem:

$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl

Any suggestions?

(ubuntu 6.10 - i386 - ati radeon x1600)

You got all the right repos?


Check out this howto:

[HTML]http://doc.gwos.org/index.php/BerylOnEdgy[/HTML]

---

### Post by Waappu on 2007-03-01
Hi

Do you habe Beryl repository in your /etc/apt/sources.list ??

---

### Post by nerds in parties on 2007-03-01
yes i have it there

---

### Post by Bagboy23 on 2007-03-01
Use Synaptic and see if you can find anything in there Beryl related.

---

### Post by nerds in parties on 2007-03-01
> **Bagboy23 said:**
> Use Synaptic and see if you can find anything in there Beryl related.

more specific...?

---

### Post by nerds in parties on 2007-03-01
> **Waappu said:**
> Hi

Do you habe Beryl repository in your /etc/apt/sources.list ??

yes

---

