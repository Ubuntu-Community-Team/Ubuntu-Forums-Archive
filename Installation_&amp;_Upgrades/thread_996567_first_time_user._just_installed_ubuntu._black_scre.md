---
title: "first time user. just installed ubuntu. black screen."
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by cjm77` on 2008-11-29
hi i just tried to install ubuntu on my lenovo s10 through a bootable usb. everything went smoothly until i restarted from a fresh installation of ubuntu. currently, it just shows a blank lit screen, while the computer sounds as if it trying to do something, though visually nothing is happening...no boot...no bios..nothing. This was my first ubuntu experience so im not sure if i did something completely wrong, can anyone help?

---

### Post by enchesss on 2008-11-29
no bios post message demonstrates a problem with the hardware - most likely the motherboard or ram. If you have a live cd then try that instead of the usb. How did you install the ubuntu to the usb?

---

### Post by dkhall618 on 2009-01-06
I just had the same problem: completed install of Heron using a USB key (on Lenovo s10), and got a blank screen at startup (no BIOS).  I read a post suggesting taking out the battery and putting it back in and trying again.  Surprisingly it worked, and everything seems to be fine now.

---

### Post by drinkmocha on 2009-01-11
i was able to get out of this situation by removing the battery while the computer is powered on. might not be the safest but it worked for me.

---

### Post by Fritz_4030 on 2009-01-15
Well I am also having problems, Ubuntu will load, the Ubuntu screen shows it loading but then it make a load noise (cymbals or such clashing) then it goes to a white/pink screen with the mouse pointer, which you can move around, but nothing else. Clicking the mouse or pressing the keyboard does nothing.

I installed Ubuntu on a clean HDD, with no other system on the machine.

Can anyone help ?

Cheers,  Chris

---

### Post by kranny on 2009-01-15
Did yuot try all the kernel options like 
acpi=off
nopcmia=yes..

I would also suggest you to press alt+f1(text mode) while the splash screen comes and post the message at which the boot resumes/strucks at

---

### Post by Fritz_4030 on 2009-01-15
This might be a dumb question, but how do you get to the kernal to make these changes ? Is there a list of these options ?

Looked at the text boot all seems OK, expect it seems to be trying to load Acer WMI hardware drivers and it is not compatible ?? Hard to see it goes by very fast ....

---

