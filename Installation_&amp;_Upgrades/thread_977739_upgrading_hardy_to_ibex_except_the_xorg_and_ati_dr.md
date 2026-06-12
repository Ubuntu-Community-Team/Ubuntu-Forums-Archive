---
title: "upgrading hardy to ibex except the xorg and ati drivers"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by rattamayhorka on 2008-11-10
i try in my laptop intrepid ibex but i can't make my graphic card (ati radeon hd2400) works fine. and i wondering if can i upgrading all the system except the drivers of my graphics card because .
i have installed hardy heron in this moment and works fine for me. but i like to have all the new stuff of intrepid (sorry for my english)

---

### Post by cariboo on 2008-11-10
When upgrading make sure to upgrade the kernel too. As the new drivers will not work with any kernel less than 2.6.27-X. I seen a lot of people that when installing the new kernel they elect to leave grub as it is, so that the newer kernel is not being used. Personally I always do a clean install as opposed to an upgrade, becuase there always seeem to be issues that take more time to resolve then a clean installation.

Jim

---

### Post by torgrot on 2008-11-10
Normally, I would agree that a clean install is better, but in this instance I don't think so.  My experience was that my ATI2400HD was not detected or set up properly from a clean install.  However when I did an upgrade it detected it perfectly and installed the proper drivers.

torgrot

---

### Post by rattamayhorka on 2008-11-10
thanks for the replies but torgrot can you tell me how do you do the upgrade please, it was a distro upgrade or just a few packages... and how i do that.

---

