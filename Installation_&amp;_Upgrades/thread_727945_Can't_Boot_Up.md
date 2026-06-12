---
title: "Can't Boot Up"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by Sicilian626 on 2008-03-18
Hello, this is my first time using linux so any help will be greatly appreciated. The first time I installed Ubuntu 7.10 I never got it to boot up because it kept hanging at "Running Local Boot Scripts." I had a feeling it had some thing to do with my graphics card so i reinstalled the OS after switching to the graphics card built-in to my motherboard in the BIOS and it worked fine. I downloaded ENVY to try install the drivers for my graphics card that way and switch to the card using the synaptic but it still won't boot up. Everytime I boot up the screen goes off for about 5-10 seconds and then kicks back in and flashes the words on the screen 3x and hangs at "Running Local Boot Scripts."

---

### Post by Ub1476 on 2008-03-18
Running local boot scripts mean starting X as well, but since X couldn't find any correct values for your graphic card it wouldn't start.. So yes, it's about your graphic card.

Is it an ATI or nvidia card?

---

### Post by lavinog on 2008-03-18
What graphics card do you have??

When you boot up to the grub menu, change the default startup settings:
press 'e' on the default startup entry
then select the line that starts with kernel and press 'e' again
then change quiet to verbose and press ESC
then press 'b' to boot

this should give you a text display instead of the graphical startup so you can get a more detailed look on what is causing the hang.
it is a temporary change to grub...if you reboot it will go back to normal

---

### Post by Sicilian626 on 2008-03-18
Its an NVIDIA

The exact model is VIDEO-338PCI-DVI Nvidia GeForce 6200

---

### Post by Ub1476 on 2008-03-18
At the live CD menu, set resolution to 1024x768 (16 bit depth can help too) and driver to VESA. If this does not work, check the CD for errors.

---

### Post by Sicilian626 on 2008-03-18
I think I might know what the problem is...when I downloaded the Live CD iso I downloaded this file ubuntu-7.10-alternate-i386. I didn't download the desktop version. I'm going to try reinstalling with that CD and see if it makes a difference.

---

### Post by lavinog on 2008-03-18
> **Sicilian626 said:**
> I think I might know what the problem is...when I downloaded the Live CD iso I downloaded this file ubuntu-7.10-alternate-i386. I didn't download the desktop version. I'm going to try reinstalling with that CD and see if it makes a difference.

That really shouldn't make a difference
I have used both...the alternate cd is faster for me.

---

### Post by rillip on 2008-03-18
Might want to check the /var/log/boot.log, /var/log/xorg (this is usually something like xorg.0.log, and the highest number is the most recent boot), and the /var/log/dmesg log, see if there's anything in there to help troubleshoot the speciifc issue X is having.

---

