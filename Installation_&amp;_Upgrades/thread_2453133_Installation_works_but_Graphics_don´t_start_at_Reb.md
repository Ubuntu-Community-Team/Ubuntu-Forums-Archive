---
title: "Installation works but Graphics don´t start at Reboot"
date: 2020-11-03
forum: Installation &amp; Upgrades
---

### Post by christian92 on 2020-11-03
Hello
I installed Lubuntu on a Stylistic 550. At Installation all is fine, The Lubuntu from Stick run´s fine.

Then when i Boot come´s only a black screen, if i hit ctrl alt F1 i get a console and the System is there, but no Desktop.

I think it´s a Problem with the Graphics driver that´s included in Kernel: gma500_gfx
Now i try to deactivate at Grub.cfg, gma500_gfx.blacklist=yes , but it isn´t better.

Anybody an Idea?

---

### Post by GhX6GZMB on 2020-11-03
Did you remember to select partition format and to set the mount points during installation? 20.04 has a different installer (Calamares) than earlier versions of Lubuntu.
The device you have has Intel graphics that normally run with no problems.

ALSO: from where did you get the .ISO?
lubuntu.me is the official site, lubuntu.net is a cybersquatter.

---

### Post by christian92 on 2020-11-04
Lubuntu.net ... ok the first mistake, should i load from lubuntu.me again and test?
but with 20.xxx i can´t work, i have an 32Bit Proz.

I let the Installation do all automatic, Erase complete HDD and install. No custom entries.

And the Installation work, but only on Terminal. So i Thought the Problem is the Grafic Card.
 If i test the Safe Mode i see a little cut of a Desktop. Only the bottom part, this on the top quarter. Under this only colourd lines... waste.


Edit, Lubuntu.me is a little bit newer:[SIZE=2][FONT=arial] 18.04.5 Bionic Beaver LTS (LXDE)[/FONT][/SIZE]

i had 18.04.4

so i will test with xxx.5 and write the results.

---

### Post by CelticWarrior on 2020-11-04
Don't.

Move to Debian or other distro still supporting 32-bit (very few and the tendency is for none very soon).
Flavors of Ubuntu 18.04 have only a few months of support left, i.e., until April 2021. Better to start off with alternatives.

---

### Post by ActionParsnip on 2020-11-04
MMMMMMmmmmm Intel Atom Z670 CPU. 32bit goodness. Yeah I'd go for a distribution supporting 32bit still
Puppy may support it but I don't know how well the touch stuff is supported there as I don't use touch stuff myself (I think its a bit of a gimmick on laptop systems)

---

### Post by christian92 on 2020-11-04
So, news
Lxle works, but it´s not my Look
Lubuntu don´t work, also the newer version
Puppy Linix has not really support for Touch. Work as a Mouse (only up down and sidewords, but not on the point)

now i search for some debian, thank´s all


latest news, lubuntu starts Desktop too, but it takes an half hour. Then you can type Password and all run´s.
But the next boot same procedure. wait wait, wait
Sparkylinux will not run, because of that i find out

---

