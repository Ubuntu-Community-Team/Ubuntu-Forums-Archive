---
title: "Kernel not updating?"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kienzan on 2008-09-12
Hey Everyone!

This might sound kind of stupid, but I have been updating my Intrepid everyday, but whenever I check the system monitor information for my system, it says the kernel is version 2.6.26-5 generic. I am hearing people are having 2.6.27 and such. Is there something that isn't updating on my system?

Thanks!

---

### Post by bpl07 on 2008-09-12
Have you manually edited your menu.lst in /boot/grub?  If so, during the update it might be asking if you want to keep your manually updated list or install the new one.

---

### Post by kienzan on 2008-09-12
I have been keeping the old one, stupid me! How do I go about updating it?

---

### Post by philinux on 2008-09-12
> **kienzan said:**
> Hey Everyone!

This might sound kind of stupid, but I have been updating my Intrepid everyday, but whenever I check the system monitor information for my system, it says the kernel is version 2.6.26-5 generic. I am hearing people are having 2.6.27 and such. Is there something that isn't updating on my system?

Thanks!

Open synaptic, click reload. Choose custom filters then the upgradable upstream option.

You can then see whats available and click to upgrade. Watch out for it to be removing anything other than older versions of stuff.

---

### Post by kienzan on 2008-09-12
only kopete shows up :(

---

### Post by ronacc on 2008-09-12
you may need to dist-upgrade to get the new kernal ( now at 2.6.27-3 )

---

### Post by kienzan on 2008-09-12
tried sudo apt-get dist-upgrade and nothing upgraded... :(

---

### Post by philinux on 2008-09-12
Have a look in synaptic and see which kernels are actually installed.

linux-image...xxx...

---

### Post by ronacc on 2008-09-12
if you do have the new kernels installed you can manualy edit your /boot/grub/menu.lst to boot the new kernel .  wherever it says 2.6.26-5 change it to the newest version you have in /boot  ( for example 2.6.27-3 ) . you only have to change the numbers , the rest of the lines stay the same .

---

### Post by kienzan on 2008-09-12
I went to synaptic, saw that linux-image was unticked and not green, so I installed. I restarted and says the kernel is still the same. Any command I can do to update?

---

### Post by ronacc on 2008-09-12
look in your /boot dir and see which kernels are actualy there .

---

