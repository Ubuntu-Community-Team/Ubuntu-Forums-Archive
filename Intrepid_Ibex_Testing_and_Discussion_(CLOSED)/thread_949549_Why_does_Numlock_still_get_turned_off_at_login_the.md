---
title: "Why does Numlock still get turned off at login then back on after"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-10-16
It's set in my bios to be on so why does ubuntu still insist on this behaviour.

---

### Post by Kow on 2008-10-16
> **philinux said:**
> It's set in my bios to be on so why does ubuntu still insist on this behaviour.

That BIOS setting should only control the numlock while no O/S is in control of the hardware. I would recommend looking into numlockx if you want numlock to be turned on when gdm starts (and stay on.)

---

### Post by philinux on 2008-10-16
> **Kow said:**
> That BIOS setting should only control the numlock while no O/S is in control of the hardware. I would recommend looking into numlockx if you want numlock to be turned on when gdm starts (and stay on.)

Yep i know about numlockx. But why does the OS still turn it off by default. Newbies wont know about numlockx.

---

### Post by Kow on 2008-10-16
> **philinux said:**
> Yep i know about numlockx. But why does the OS still turn it off by default. Newbies wont know about numlockx.

When the kernel inits the hardware it is reset. The default setup for a keyboard is numlock off, scroll-lock off, capslock off. The real problem is the window manager is what should be controlling this (it is) but it is not started until you login. I'm guessing Ubuntu devs could whip up a quick script sometime to allow some sort of user interaction between numlockx being called on X11 startup instead of the user having to work with scripts themselves. Another option is to have X11 (Xorg) control the behavior but this wasn't a good option for hardy or intrepid due to the major configuration changes Xorg is currently experiencing. Perhaps the next Ubuntu release could somehow incorporate these keyboard settings into the input device setup (which is now controlled by HAL I believe.) Maybe have X11 save the keyboard settings on shut-down and then re-apply them when the keyboard is re-initialized on the next start-up.

Point is, there are numerous options to make this work right for the typical user but since Xorg is currently undergoing major changes it is not the best time to deal with it. So stick with numlockx for now. :)

---

