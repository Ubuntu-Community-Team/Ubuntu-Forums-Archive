---
title: "installation laptop"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by payrim9 on 2017-07-22
ok so i have a laptop that has 2 gpu, its asus(n552vw) the problem is it will stuck on installtion : (here) [https://4.bp.blogspot.com/-vs0vHKOfLFA/UIJIBuUQEnI/AAAAAAAABjs/sNxZ9gLwj58/s510/1350715389451.png](https://4.bp.blogspot.com/-vs0vHKOfLFA/UIJIBuUQEnI/AAAAAAAABjs/sNxZ9gLwj58/s510/1350715389451.png)
i tried the usb on other laptop (only had 1 gpu ram2) and pc and it worked (i have windows 10 installed ) any help ? thanks

---

### Post by johndough2 on 2017-07-22
Hi

It's an earlier screen that may help.

If there is a screen with options, you may want to run thru those in the hope of finding something that will say - noacpi or 800x600.

It would seem that a piece of hardware is causing a stumbling block, and going with the lowest common denominator may give the highest result.

---

### Post by helen-ms on 2017-07-25
Funny I have the same problem I have the G552VW and i find the boot sequence seems to be under win 10 boot manager and it just ignors the usb and disk drive at random.
looking at the bios it boot order also changes. I not sure if it is crazy or I am  :lolflag:

---

### Post by wildmanne39 on 2017-07-25
Welcome to the forum helen-ms if you need help please start your own thread so you and the OP of this thread can both get the help you need.

Cheers

---

### Post by BenginM on 2017-07-25
Salutations! and welcome to the forums.

The machine has a hybrid/dual graphics , SO disable one in the BIOS , am pretty sure you will be able to boot fine with the Intel HD graphics .. you might also need to boot with the kernel parameter nomodeset , see these screens:

[ATTACH=CONFIG]276137[/ATTACH]

[ATTACH=CONFIG]276138[/ATTACH]

---

### Post by sccman on 2017-07-26
> **BenginM said:**
> Salutations! and welcome to the forums.

The machine has a hybrid/dual graphics , SO disable one in the BIOS , am pretty sure you will be able to boot fine with the Intel HD graphics .. you might also need to boot with the kernel parameter nomodeset , see these screens:

[ATTACH=CONFIG]276137[/ATTACH]

[ATTACH=CONFIG]276138[/ATTACH]

+1 for this.

If that doesn't work, you could try pushing a button when you get this screen:

[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png?cache=[/IMG]

Then push **F6** at the menu and tick **nomodeset** with the spacebar. Run **Install Ubuntu**&#8203;.

---

