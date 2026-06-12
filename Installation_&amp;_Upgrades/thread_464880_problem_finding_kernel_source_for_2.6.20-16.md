---
title: "problem finding kernel source for 2.6.20-16"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by mmoalem on 2007-06-05
hi there all - i have feisty upgraded to ubuntustudio and that has been updated with the 2.6.20-16 security updated kernel (it has both generic and low latency) now i have problem with virutalbox and truecrypt - it seems that both are kernel specific and will need to be recompiled. virtualbox runs fine on 2.6.20 -15 generic and low latency but gives an error on the -16 versions, truecrypt runs fine on both generic versions but not the low latency ones...
so i set to compile both on the -16 low latency one which i use by default
now the problem is finding the kernel source and headers
this is the output i get trying to apt-get them:
> michel@laptopubuntu:~$ sudo apt-get install linux-source-`uname -r` linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-source-2.6.20-16-generic

the same output i get under the lowltancy kernel

any ideas what to do next?

---

### Post by Pumalite on 2007-06-05
> **mmoalem said:**
> hi there all - i have feisty upgraded to ubuntustudio and that has been updated with the 2.6.20-16 security updated kernel (it has both generic and low latency) now i have problem with virutalbox and truecrypt - it seems that both are kernel specific and will need to be recompiled. virtualbox runs fine on 2.6.20 -15 generic and low latency but gives an error on the -16 versions, truecrypt runs fine on both generic versions but not the low latency ones...
so i set to compile both on the -16 low latency one which i use by default
now the problem is finding the kernel source and headers
this is the output i get trying to apt-get them:

the same output i get under the lowltancy kernel

any ideas what to do next?

Try with 'kernel-source'. Good luck. If you are going to recompile kernel, you need to make sure you have: make, autoconf, kernel-source or kernel-headers and gcc++

---

### Post by Bachstelze on 2007-06-05
You don't need the full kernel source, only the headers :

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by mmoalem on 2007-06-05
sorry for the double postings... installed headers but still cant find kernel-source and virtualbox still returning the same output...

---

### Post by Pumalite on 2007-06-05
> **mmoalem said:**
> sorry for the double postings... installed headers but still cant find kernel-source and virtualbox still returning the same output...

Found out kernel-source is for Suse; in Ubuntu is enough with kernel-headers. So if you have kernel-headers and all the rest you should be all set to go.

---

