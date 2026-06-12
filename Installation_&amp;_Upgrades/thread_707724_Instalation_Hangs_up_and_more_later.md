---
title: "Instalation Hangs up and more later"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by ptaramelli on 2008-02-25
I have installed Ubuntu in several PC&#347;, laptops and Desktops without problem. In one in particular I Have problems:
Processor pentium 4 2.8 GHZ, 1 GB Memory, mainboard Intel 865 without integrated video (so I use an ATI AIW 9600)

In the instalation of the live cd, the orange bar stopped at almost 80%, without any messages, I have tried many acpi=off, and others and nothing.

I have downloaded the alternate CD and it seems that it was installed ok (it'is like Debian and I installed Debian without problem).

But when I tried to start the system from the hard disk, it happened the same thing: the bar stops at the same 80% and hangs up.

I was looking in many forums without success, Can anybody help me?
At least now I can reach the terminal in the second option and maybe do something if I get some help.

thanks

Pablo

---

### Post by Pumalite on 2008-02-25
Can you finish the installation? Do you see the Grub menu? At which point it hangs?

---

### Post by ptaramelli on 2008-02-26
Hi!, yes, the instalation is complete, it ask me to retire the CD so the reboot will be from the hard disk and will not begin the instalation again.

While rebooting the progress of the orange bar stopped just before reach 80% (16 blocks of 20), and that is exactly what happened before when I try to install from the live CD,

At the beginning it recognize the Ubuntu and the XP installed. I can start it in recover mode and I finish with a terminal as root, I suppose from there I could do things, but what ?.

Pablo

---

### Post by Pumalite on 2008-02-26
Hit 'Esc' so you can see where it gets stuck and let me know.( the kernel has problems with some of your hardware)

---

### Post by ptaramelli on 2008-02-27
Dear Pumalite: Thank you so much!!!!

Pressing ESC gave no results because the system was totally hang up (no even the SHIFT key turn on the lights).

But because you said the conflict with the kernel and some hardware (I always thought the ATI card) I unplugged a second network card (wireless) that I have and now it works fine. I even installed again the system now with the live CD without problem.

I had before this wireless network card working with Ubuntu along with the other in a similar PC, just an Intel  845 mainboard instead of this 865, so I could use the one or the other, I have installed the Ubuntu with the two cards plugged, and I make work the wireless with ndiswrapper.

I have now to figure out how to install the wireless but that s the fun.

Thanks again

Pablo

---

### Post by Pumalite on 2008-02-27
You are welcome. Good luck.

---

