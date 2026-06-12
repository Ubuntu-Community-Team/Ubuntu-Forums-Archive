---
title: "Fiesty Upgrade good idea?"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by itendsnow on 2007-05-13
Okay, I tried to get fiesty installed on my machine however it would hang duirng the installation, even the alternative install disk did the same and the screen would go blank during the boot up of the installer, so my question is: Would is be a bad idea to upgrade to fiesty since I have got my desktop (of 6.10) set up well and the install problems could be an actual hardware problem that fiesty can't understand?

My computer is a fujitsu siemens scaleo P.

---

### Post by Ateo on 2007-05-13
A better question might be 'what hardware does your system have?'.. 

Maybe post your system specs but honestly, if dapper works for you, so *should* feisty. I can't see regression here when it comes to hardware support unless the device is so old that it needs to be ditched anyways.

---

### Post by theaceoffire on 2007-05-13
Ok, 1.

Do you have an ATI video card?

If you do, that is probably your issue.

^_^;; I am still trying to get mine installed right now, so I don't know how to FIX it, but umm..

>.< telling the bios to use my on board video by default rather than the PCI one really helped me (Allowed installation, etc).

---

### Post by itendsnow on 2007-05-14
My hardware is that of the scaleo P, my PC is only 2 years old with onboard intel graphics card which seems to have been supported forever.

---

### Post by Jordan-D on 2007-05-14
> **theaceoffire said:**
> Ok, 1.

Do you have an ATI video card?

If you do, that is probably your issue.

^_^;; I am still trying to get mine installed right now, so I don't know how to FIX it, but umm..

>.< telling the bios to use my on board video by default rather than the PCI one really helped me (Allowed installation, etc).

i have an ATI video card and i used EasyUbuntu to install the drivers. And it works fine :) [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by stefaan.dutry on 2007-05-14
> **itendsnow said:**
> Okay, I tried to get fiesty installed on my machine however it would hang duirng the installation, even the alternative install disk did the same and the screen would go blank during the boot up of the installer, so my question is: Would is be a bad idea to upgrade to fiesty since I have got my desktop (of 6.10) set up well and the install problems could be an actual hardware problem that fiesty can't understand?

My computer is a fujitsu siemens scaleo P.

Are you getting the screen with a selection to make?

If you do you'll see you can press F6 at the bottom(i think it was F6) for options
Hit F6 and add the option **acpi=off**

It solved my problem; hope it solves yours.

---

