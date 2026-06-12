---
title: "Cannot boot live CD"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by tomvalois on 2012-02-18
I have an emachines T5212. It is an older computer (from 2007). I cannot boot to the Ubunutu live CD. I have tried the current version (11.10), the next most recent version (11.04), and the long term support version (10.04). 
 
I don't think it is a linux specific hardware problem, because I can boot to G-Parted Live which, like Ubuntu, uses a debian-based kernel with a GUI. Also, I have checked my hardware against a list of incompatible hardware, and nothing I have found appears in that list. 
 
I don't get any error messages when I try to boot to Ubuntu. It just goes to a blank screen with a cursor blinking in the upper left corner, and the system is unresponsive to any keyboard or mouse input.
 
Any ideas?

---

### Post by MAFoElffen on 2012-02-19
> **tomvalois said:**
> I have an emachines T5212. It is an older computer (from 2007). I cannot boot to the Ubunutu live CD. I have tried the current version (11.10), the next most recent version (11.04), and the long term support version (10.04). 
 
I don't think it is a linux specific hardware problem, because I can boot to G-Parted Live which, like Ubuntu, uses a debian-based kernel with a GUI. Also, I have checked my hardware against a list of incompatible hardware, and nothing I have found appears in that list. 
 
I don't get any error messages when I try to boot to Ubuntu. It just goes to a blank screen with a cursor blinking in the upper left corner, and the system is unresponsive to any keyboard or mouse input.
 
Any ideas?
Going to bed so not much time... But, use nomodeset as a boot option on the LiveCD. Use same in grub after the install. Then install your ATI Driver for your video card (specs say its a ATI Radeon Xpress 200).

Instructions linked from Post #2 of my sticky:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Night...

---

