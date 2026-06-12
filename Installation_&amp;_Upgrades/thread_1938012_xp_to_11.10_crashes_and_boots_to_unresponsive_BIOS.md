---
title: "xp to 11.10 crashes and boots to unresponsive BIOS."
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by Jake5 on 2012-03-08
I have a HP a1110n, 
1.25g RAM, 80g hdd.
Windows XP
      I have successfully installed several variants on my machines so experience is there, not much but some. I tried replacing XP with ubu 11.10 and half way through the install the system crashed and rebooted to an unresponsive BIOS screen. I have tried twice to shutdown and reboot and get the same results, I fear if I try hard powerdowns too much I could really damage the machine. I have found some resources online that say the BIOS on this machine was loaded onto the hard drive and therefore it is impossible to install another operating system. Is this thing trash now or is there a way to install another BIOS?

Sub Question 
where exactly is a BIOS installed at normally?

---

### Post by Jon Monreal on 2012-03-09
From all indications I've found online, the BIOS on the a1110n is stored in ROM on the motherboard like any other BIOS, so installing Ubuntu should have had no effect on it.

Are you able to try to boot from a LiveCD? Perhaps something happened to the hard drive during installation, and it has nothing to boot to.

---

### Post by pavi_elex on 2012-03-09
BIOS is not related to HDD, it is related to mothernoard. OS is related to HDD.
use another LIVE/CD or change your BIOS setting to usb boot and try to boot .iso file from usb. If it is still giving problem. Try to install XP again, either by cd or either by usb.
Then install ubuntu using wubi.

If process is completed and bootable cd is still in CD-ROM. It can give error but as you told, os was not installed so it can be some other proble. But it does bot look like any serious issue.
I think you are missing a very small and rare thing.

---

### Post by Jake5 on 2012-03-09
To answer your questions, No the computer will not boot a Live CD. I cant change anything in the BIOS because the only screen that will load is the one that says hit f1 for setup, f4 for boot options. None of the listed commands on the screen will do anything. I think it may have usb power shut off, and therefore I cant run a keyboard on it. and that might explain why it wont do anything on the bios or boot the live cd. may have just talked myself into the solution, Thanks for your help guys.

---

### Post by Jon Monreal on 2012-03-09
If the USB power isn't working, do you have a PS/2 keyboard around? You could try that to see if it works, provided there's a port.

---

### Post by Jake5 on 2012-03-10
> **Jon Monreal said:**
> If the USB power isn't working, do you have a PS/2 keyboard around? You could try that to see if it works, provided there's a port.


There is a port, finding a ps2 keyboard is another thing, I found one on ebay for six bucks, and its on its way, Not too hard online, but they dont carry them in any of the office stores or even @ radio shack where I live. Let you know how it works out.

---

### Post by Jake5 on 2012-03-20
So I don't know what jank site I went to that told me the BIOS was on the HDD, but anyways after I got the ps/2 keyboard, I was able to boot again and ran the install just fine. all good here.

---

### Post by Adrian98 on 2012-03-21
Wow I am so lucky that I got a ready-made solution for making my Operating systems crashes to be repaired!!! Thanks you all!!

---

