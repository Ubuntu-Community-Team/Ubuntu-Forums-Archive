---
title: "How to enable 2 cpu in ubuntu?"
date: 2005-01-03
forum: Installation &amp; Upgrades
---

### Post by Freemen on 2005-01-03
Hello all

I have install ubuntu the new one. How do I check ubuntu uses 2 cpu's? And if not, then what?? I'm totally new to linux....

/Freemen

---

### Post by jdong on 2005-01-03
You must use a -smp kernel, such as linux-686-smp. Then, take a look at **top**. You should get usage stats from both CPU's.

---

### Post by Freemen on 2005-01-03
I'm a noob, so i need a little more help.

Where do I get a kernel whit smp support, and how do I install it?

/Freemen, total NooB!!!

---

### Post by castrojo on 2005-01-03
Do an apt-cache search for smp and the kernel version, for example:

apt-cache search 2.6.8.1 smp

and you should see a list of available kernels.

EDIT: Then apt-get install the one you want.

---

### Post by Freemen on 2005-01-03
[QUOTE=whiprush]Do an apt-cache search for smp and the kernel version, for example:

apt-cache search 2.6.8.1 smp

and you should see a list of available kernels.

EDIT: Then apt-get install the one you want.[/QUOTE]

I have done this, but can still only see one cpu in system res. What now???  :confused:

I have done this apt-get install linux-headers-2.6.8.1-3-686-smp
Install have downloadet and installt pack..... what have I done wrong.

---

### Post by Sensebend on 2005-01-03
You'll want to install a kernel rather than the headers.

linux-686-smp is the package I think you want. install it with sudo apt-get install linux-686-smp.

---

