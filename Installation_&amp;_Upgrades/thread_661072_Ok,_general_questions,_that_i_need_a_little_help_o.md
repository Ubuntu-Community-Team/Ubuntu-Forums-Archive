---
title: "Ok, general questions, that i need a little help on..."
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by APVangeliLMS on 2008-01-07
it seems that i cant find any threads like this, so i'll ask myself.

i have windows vista home premium, on my hp laptop, and when i boot up, i noticed that when i press f2, it shows where i can choose my operating system, the only one installed is windows vista. if i installed ubunto, would i be able to press f2 at the beginning of boot, and choose vista again, like if i want to use my ms office? then choose ubunto if i want to use that when im in the mood?

any help is appreciated.

also, i've seen that there are some problems on hp laptops, could anyone post the pro's/con's of installing on hp laptops?

---

### Post by adprice on 2008-01-07
Unfortunately, its not quite that simple.  If you only have 1 hard disk you'd have to repartition it so you can install both OSes.  Also, theres the matter of choosing a boot loader and configuring the dual boot, etc.  If you search the forums there should be a bunch of howtos on dual booting.  As for hp laptops I don't know.  I have a gateway and Ubuntu installed without any difficulty.

---

### Post by APVangeliLMS on 2008-01-07
but i dont need to install vista, its installed already. and whats the reportion thing?:(

---

### Post by forestpixie on 2008-01-07
if you've 1 drive with vista on it - you'll need to have a partition for each - partitioning basically splits the physical drive into smaller pieces

you need to have a look into dual booting - this is a good start

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

and if you have a search here you'll find an enormous amount

---

### Post by erfahren on 2008-01-07
repartioning is basically just creating space on your hard drive for Ubuntu. 

Ubuntu comes with it's own bootloader (called GRUB). It's installed by default but you can opt-out on installing it - it is recommended that you use it though. It's configurable through Ubuntu (like which OS to boot by default, how long the count-down time the menu is displayed, etc.)

My question: on your notebook - when you open up "My Computer" does it show that you have just a C: drive or do you also have a D: drive (like for data backup)?

here's a couple of sites that will help learn about dual-booting (the first one covers installing with the Alernate CD (or text-based installer) but it has a lot of other information which is relevant (it covers partioning and GRUB for instance):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This page covers installing dual-boot with Windows using the Live CD
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

you can also check the Laptop Testing Wiki to see if it has any information on your laptop. You can also just Google the model of your laptop along with "ubuntu" (or just the generic word "linux") to see if anyone has anything to say about it specifically:
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

