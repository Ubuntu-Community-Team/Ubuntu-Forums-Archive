---
title: "Problems booting Wubi in last intrepid beta"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gilean on 2008-10-13
Hi to all, i have problem with wubi and intrepid beta. The installation is ok, Intrepid installs (i have vista in c: and i instal wubi in e:) but when installation finishes and i reboot and choose ubuntu, starts the countdown then i have a message saying (no partition disk).

---

### Post by ago on 2008-10-13
Press esc and select the other boot options, see if you have a more verbose error. If it is the first reboot look into /casper.log

---

### Post by mr.sauli on 2008-10-14
Hey,

I'm having a similar problem, with a similar setup.. 
I ran the wubi installer from the 8.10 cd-rom, and after reboot, and choosing the ubuntu option in the vista bootloader, was greeted by a grub menu filled with garbled characters.

so I chose to uninstall 8.10 (using, again, the wubi uninstaller) and reinstalling my previously working 8.04 version.. which, now won't boot into the second part of the installation either..

gr,
S

---

### Post by Gilean on 2008-10-14
ago where can i find casper log? i tried to boot with other options, but it gives me always the same error.

---

### Post by ago on 2008-10-15
Please see [http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)

---

### Post by Gilean on 2008-10-16
i edited menu.lst and now ibex is fully working with wubi, tnx ago :)

p.s. this problem will be fixed in final release?

---

