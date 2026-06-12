---
title: "Login Screen Half of Screen Illegible"
date: 2017-11-03
forum: Installation &amp; Upgrades
---

### Post by kenneth17 on 2017-11-03
Hi. I have just upgraded to Ubuntu 17.10 on my Acer Aspire One netbook.
(Memory: 986.7 MiB, Processor: Intel Atom CPU N270 @ 1.60 Ghz x2, Graphics: Unknown, Gnome: 3.26.1, OS Type: 32 Bit, Disk: 156.3 Gb)
The problem: The computer boots normally, but when it finishes loading and the Login screen appears it is cut in half by pixilated garbage. Putting the computer in sleep mode by pressing the power button and waiting a few seconds, then waking the computer up by pressing the power button removes the pixilated garbage and allows the user to login normally - all screens are normal after this "sleep reboot." 
How can I get the computer to boot normally and display the login screen on the first bootup?
See attached pic.
Thanks!

---

### Post by mattemawi on 2017-11-04
Hi! Im using a HP mini 5101 notebook, 1.66GHz Intel Atom N280 CPU, 2GB of RAM, a 64GB SSD and 6 cell, 55WHr battery. It features a 10.1 inch, 1024 x 600 pixel display and im experience the exact behaviour!  What to do?

Thanx // Mats

---

### Post by mörgæs on 2017-11-04
Is it more or less the same problem as described [here]("https://ubuntuforums.org/showthread.php?t=2375598")?

---

### Post by mattemawi on 2017-11-05
Thanx mörgeas! 

The bug is accurate described here! 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639)

BR // Mats

---

### Post by kenneth17 on 2017-11-05
I have decided to do this temporary fix instead, and hope that a more permanent fix will come about:

1. Power on computer.
2. Hold down both SHIFT keys while the computer boots.
3. The GRUB menu should appear.
4. Select an older kernel and press ENTER.
5. The computer should boot normally without error.

i know this is a less than ideal fix to have to do the above every time you start the computer,  but hopefully this will be a temporary fix until a more permanent solution can be brought forward.

-kenneth

---

### Post by Robb987 on 2017-11-11
> **mattemawi said:**
> 
The bug is accurate described here! 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724639)

BR // Mats

and even a temporary solution!
Edit the grub file and add line "GRUB_GFXPAYLOAD_LINUX=text" works for me...

---

### Post by Sami Lehtinen on 2018-04-03
Thanks, I had the same problem with Samsung NC10, and Lubuntu. Now issue has been "resolved". With GRUB configuration change.

---

