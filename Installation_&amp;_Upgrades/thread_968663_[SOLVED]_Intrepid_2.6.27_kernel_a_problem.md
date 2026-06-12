---
title: "[SOLVED] Intrepid 2.6.27 kernel a problem"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Lesouteneur on 2008-11-02
I repeatedly installed Ubuntu 8.10 and Kubuntu 8.10. Neither of them worked. I used different mirrors, torrents, I made a couple of CDs everytime the cd would boot the usplash would hang unless i repeatedly pressed a key through the process of loading. It was very annoying as I needed to do this on every boot. The kernel also apparently didn't take well to my video card, Nvidia 7000M. Kwin and compiz would sometimes have the close minimize and maximize buttons not completely displayed. 

For the time being I have reinstalled Windows Vista, as much as I hate too. I would really like to go back to Ubuntu but this has not been possible at this point. How can I revert the kernel to 2.6.26 and solve my woes?

---

### Post by Lesouteneur on 2008-11-03
Anyone?

---

### Post by Yashiro on 2008-11-03
a) Edit your Grub menu to use the old kernel?
b) No grub? Swap the kernels over, old ones are usually backed up when you do official upgrades.
c) Install Ubuntu 8.04 instead and avoid these teething issues.
d) Chill out.

---

### Post by Lesouteneur on 2008-11-07
I installed Kubuntu 8.04 and then upgraded to 8.10. It still failed because when I picked the old kernel from the menu, it would say there was no "resume image."

---

### Post by Yashiro on 2008-11-08
Machine has  nvidia onboard graphics and you have 4g of ram installed?

You're also installing a 64bit image I presume?

---

### Post by Lesouteneur on 2008-11-08
> **Yashiro said:**
> Machine has  nvidia onboard graphics and you have 4g of ram installed?

You're also installing a 64bit image I presume?

I have nvidia 7000M, which is onboard. I have 2GB ram on an AMD processor. I tried both the 64bit and 32bit versions of Ubuntu and with both I experience the same problem...

---

### Post by Yashiro on 2008-11-08
Only option is to use 8.04 I guess. 8.10 is a pretty cruddy release for certain hardware setups.

---

