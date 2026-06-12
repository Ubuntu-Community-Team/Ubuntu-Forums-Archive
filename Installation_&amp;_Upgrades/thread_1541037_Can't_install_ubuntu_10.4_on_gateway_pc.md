---
title: "Can't install ubuntu 10.4 on gateway pc"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by tcmct on 2010-07-28
As the title states, I am having trouble installing ubuntu on a new to me gateway computer. The spec's are as thus: Intel Celeron Cpu 2.4GHz, 1.25 GB DDR RAM, 250 GB ATA 5200rpm HD.

I have tried installing Ubuntu 10.4, Ubuntu 9.10, Xubuntu 10.4 and Lubuntu 10.4. Neither Ubuntu 10.4 or 9.10 would boot from live cd and after full install would freeze on the loading 5 dot screen with no messages. Xubuntu would freeze sooner. Lubuntu would go live but after a full install would come up with this error, "(process:219): GLib-WARNING **: getpwuid_r(): failed due to unknown user id". 

All of the cd's work fine on my laptop and I have checked them for defects. I have tried safe graphics mode a changing around a few options. So I was wondering if this computer just won't take Ubuntu or is there a work-around on the command line?

Try to go alittle easy on me I've only been working with Ubuntu for about 6 months.

Thank you for any help you may offer!

---

### Post by davidmohammed on 2010-07-28
suggest - press e to edit your grub.

find the line with quiet splash

remove quiet splash and boot.

do you see any errors?

other boot options you can use 

nomodeset
i915.modeset=1
i915.modeset=0
noapic
nolapic

i.e.

add one or more of these BEFORE quiet splash

---

### Post by tcmct on 2010-07-28
I tried nomodeset before quiet splash and it worked. Thanks!!

---

