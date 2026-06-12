---
title: "Cannot boot after install due to graphics problem"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by SnarkyTwit on 2011-10-18
Hi there.  I am brand new to Ubuntu.  I tried installing Ubuntu and Kubuntu 11.10 and have the same problem.  I am using a Dell Precision M4400 with a nVidia Quadro FX 770M graphics card.  After the install goes seemingly smoothly, I reboot only to find that the computer has crashed. During the boot process, It seems the graphics driver has crashed the machine.  I say this because it seems the boot process is trying to load a graphic but just quite can't.  Then it goes to a text mode and shows some things [OK] and the crash report [FAIL].  Then it hangs on the battery state.  Nothing happens after that.  Can anyone shed some light on how I can change the driver without actually being able to boot into Ubuntu or Kubuntu?

Thanx muchly in advance!
Snarks :D

---

### Post by varunendra on 2011-10-19
Try to boot in 'Recovery Mode' with 'failsafeX' option. If grub menu does not appear by default (where the 'Recovery Mode' is listed as a boot option), press and hold 'shift' key while booting to bring it up.

If it allows you to boot with safe graphics, you may then try to install suitable proprietary driver through "Additional Drivers" option.

---

