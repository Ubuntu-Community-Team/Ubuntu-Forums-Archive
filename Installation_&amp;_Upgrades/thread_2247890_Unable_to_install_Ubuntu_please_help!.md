---
title: "Unable to install Ubuntu please help!"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by saul-palma on 2014-10-11
Hello everyone, I need some help installing Ubuntu I have tried for quiet some time now to install Ubuntu on my system, all to no success. I've read many articles related to common installation problems and to the best of my abilities tried to execute the solutions they offered but still I couldn't make it work now I turn to you all in the hopes that I might be able to succeed with your help. Any help will be greatly appreciated, I thank you in advance! 

My system specs; Motherboard: EVGA P55 FTW 200, Graphics Card: NVIDIA GeForce GTX 260

[IMG]http://s18.postimg.org/jorkhrnhl/UNI2011_0879_161123.jpg[/IMG]

BIOS Setting

Main Menu:

[IMG]http://s30.postimg.org/gros27z6o/20141011_011449.jpg[/IMG]

**Advance BIOS Features **

[IMG]http://s30.postimg.org/7y72clqzk/20141011_011524.jpg[/IMG]

- IDE Configuration

[IMG]http://s22.postimg.org/63qtnbu2o/20141011_011246.jpg[/IMG]

- Boot Settings Configuration

[IMG]http://s24.postimg.org/d9rrgycpg/20141011_011308.jpg[/IMG]

- AHCI Configuration

[IMG]http://s3.postimg.org/qlpy5z8aa/20141011_011322.jpg[/IMG]

- USB Configuration

[IMG]http://s27.postimg.org/a0y8lvm2r/20141011_011332.jpg[/IMG]

[B]Advanced Chipset Features

[/B][IMG]http://s10.postimg.org/e8tclek1l/20141011_011354.jpg[/IMG]

- North Bridge Configuration

[http://s27.postimg.org/5smvc4adf/20141011_011550.jpg](http://s27.postimg.org/5smvc4adf/20141011_011550.jpg)

- PCI Express Configuration

[http://s21.postimg.org/3zzwpg6br/20141011_011542.jpg](http://s21.postimg.org/3zzwpg6br/20141011_011542.jpg)

- ME Subsystem Configuration

[http://s7.postimg.org/mqjgyapcb/20141011_011404.jpg](http://s7.postimg.org/mqjgyapcb/20141011_011404.jpg)

**PCI/Pnp Settings **

[http://s21.postimg.org/ay8m94ttz/20141011_011422.jpg](http://s21.postimg.org/ay8m94ttz/20141011_011422.jpg)
[http://s13.postimg.org/hiawelqfr/20141011_011433.jpg](http://s13.postimg.org/hiawelqfr/20141011_011433.jpg)

I think i should mention that regardless of what I do I always end up in a black screen that looks like a command window, or a white screen, and seconds after I make a selection from the boot list whether it be try ubuntu, install or check cd, my computer freezes completely and I have to manually turn it off from the psu or disconnect it from the outlet. power and reset do not respond, same thing happens with other linux distros so far I have tried ubuntu, mint, fedora, backtrack, kali, and backbox. Please help me. and once again thank you!

I am trying to install version 14.04 flavor Ubuntu Desktop x64 bit.

---

### Post by coffeecat on 2014-10-11
You posted this in the Ubuntu Development Version forum which is for discussion of the in-development 14.10 (at present). So...

*Thread moved to **Installation & Upgrades**.*

So that others can help you, which version of Ubuntu are you trying to install - e.g. 12.04 or 14.04 - and which flavour, Ubuntu itself, or Xubuntu, Kubuntu, Lubuntu, etc? Although you mentioned that you tried a number of distros without success, it be more efficient here to focus on which Ubuntu variant/version you are trying.

---

### Post by Impavidus on 2014-10-11
I see you have nvidia graphics. Often the nomodeset boot option helps. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Do you want to install Ubuntu only or do you want to keep Windows and dual boot? In the latter case, which Windows version is this and how has your hard drive been partitioned?

---

### Post by fantab on 2014-10-11
Unless you have windows8 related issues, '_nomodeset_' option at boot should allow you to boot with 'failsafe' graphics mode.
Let us know how it goes...

---

