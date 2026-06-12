---
title: "Ubuntu 13.10 -&gt; black screen"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by atomstark on 2013-10-18
Hi,

 I upgraded my system to Ubuntu 13.10 in the morning and since that I can't use my Ubuntu. In fact, when I boot my screen turns black and even Ctrl+ALt+F1 doesn't allow me to see where's the problem.
In Live-USB the problem is the same, I choose "Try without installing" and then the screen turns black. I also tried with Xubuntu 13.10 and the problem is the same. I've an Asus UX31A.


If you guys have an idea I'll be glad. :)

---

### Post by guillaume2 on 2013-10-18
Hi,

I have the same problem with the same laptop.
I have upgraded  xubuntu 13.04 -> 13.10.
I did : sudo do-release-upgrade and answered yes to all configuration file conflicts during upgrade.
After upgrade, I have a black screen after boot.

---

### Post by guillaume2 on 2013-10-18
I managed to successfully boot into xubuntu by choosing an older kernel (3.8), it seems that kernel 3.10 has a problem.

---

### Post by atomstark on 2013-10-18
Unfortunatly the upgrade removed my older kernels I think.

Edit : Actually it removed an older kernel than 3.8. So I could try and it works for me too.

---

### Post by cairn on 2013-10-19
I just upgraded from Ubuntu 13.04 to 13.10 on my Asus UX31A and got the same blank screen issue. Thanks to your suggestions, I was able to boot with the older 3.8 kernel from the GRUB options and things are working fine this way. 

I hope the bug in the 3.11 kernel gets fixed; is there a bug report for this issue?

ETA: I found the appropriate bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229686](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1229686)

---

