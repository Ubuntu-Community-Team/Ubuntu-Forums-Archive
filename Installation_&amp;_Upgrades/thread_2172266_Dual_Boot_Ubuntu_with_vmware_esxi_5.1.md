---
title: "Dual Boot Ubuntu with vmware esxi 5.1"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by ankurk on 2013-09-04
Hi All

I have built a white box with intel i7 3770 and 32gb ram. I want to use both ubuntu and esxi 5.1 How can i get the option to either boot Ubuntu or Esxi. I will install each on different hard drive. What order shall i install them. Any guide/links ?

Thanks
Ankur

---

### Post by kc-koellein on 2013-09-04
I'v enever had ubuntu fail to setup a dual boot with an existing operating system.

I would install VMware first, and then run the Ubuntu install. In fact... this is a pretty cool idea. I go try... right now! :-)

Will report back!

HTH,
K9SPY

---

### Post by kc-koellein on 2013-09-04
...figures.

Lubuntu 12.10 i386 Desktop didn't recognize the VMware install...

It showed all the myriad of partitions that VMware sets up... but said it did not recognize any existing operating system, and only presented options for fresh installs...

Sorry. But at least I destroyed my ESXi server before you had to...

...now I gotta rebuild the damn thing!  :-)

K9SPY

---

### Post by ankurk on 2013-09-07
I Feel Bad hearing that you destroyed your ESXi. But there must me some way to do that. Please let me know if you come across any.

Thanks for You Reply
Ankur

---

### Post by newtrojan on 2014-06-24
Installl ESXi on a USB flash drive and boot from it. 

Thats the advantage of esxi, small foot print.

---

