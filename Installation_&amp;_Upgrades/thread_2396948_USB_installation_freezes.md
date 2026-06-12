---
title: "USB installation freezes"
date: 2018-07-23
forum: Installation &amp; Upgrades
---

### Post by RedChili on 2018-07-23
Hi!

I have, for the first time ever, bought a really expensive laptop because I need some good performance for editing videos. And now naturally I can't install Ubuntu on the laptop.

The laptop doesn't have a DVD so I try to install via a live USB stick. But shortly after Ubuntu starts, the whole process is freezing. I get the same results both if I choose to install directly from Grub, or if I choose to try a live version. The live version also freezes after about 30-40 seconds.

I tried to search and found an old thread that suggested to amend the boot process as follows:

> Then choose the Ubuntu, or Install Ubuntu (it depends, you will see it hopefully), go to it with the arrows and press the 'e' key.
Here go to the line which contains quiet splash at the end and add  acpi=off after these words.


However, this doesn't help at all. I still get the same freeze.

I'm trying to install Ubuntu Mate 18.04.

The laptop is a HP Pavilion Power 15-cb084no, Intel Core i5 processor model number i5-7300HQ, 8 GB DDR4 ram, Nvidia GeForce GTX 1050 4 gb, and Win10 pre-installed.

---

### Post by ubfan1 on 2018-07-23
Have you been using the "nomodeset" boot option for your Nvidia hardware (you should)?  Lots of help on that topic at askubuntu.com.

---

### Post by RedChili on 2018-07-23
Thanks! It appears that this has solved the problem for me. It's running the installation now.

---

