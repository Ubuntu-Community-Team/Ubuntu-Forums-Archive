---
title: "Mouse/Keyboard not responding when starting Ubuntu 7.10 live cd."
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by Metallic Blade on 2007-12-31
Hello. I have used Ubuntu on occasion on my other computer which worked fine. Now when I have my new system now, I though it would be the same procedure, on which apparently is not. Before running the live cd, I checked the disk for defects. It cam out clean. So I launch the live cd, Ubuntu starts up nicely. Good, then when I try to move my mouse, nothing. The same with the keyboard. No response with any keys. This is where I stop. Ugh, Vista came with this computer. I'm already growing tired of it. I would like to create a dual-boot setup.

My machine's specs:

HP a6230n 
Asus: M2N68-LA mobo
AMD Live! 62 X2 5600 Dual Core
3GB DDR2 SDRAM
nforce 430 GeForce 6150SE 
Standard keyboard/mouse that came packaged. 

Help would be very appreciated. Many thanks!  :D

-SOLVED-

---

### Post by bharadwaj on 2007-12-31
may be its the problem with your USBports try checking them out get on to PS ports

---

### Post by Metallic Blade on 2007-12-31
Thanks for your reply. Sorry, but I'm running my mouse and keyboard off the PS/2 ports, not USB.

---

### Post by Metallic Blade on 2007-12-31
I just tried to boot it off from my older distro version: 6.10. Again, no effect. My PS/2 mouse and keyboard just don't respond. Well, both are powerd on. The num-lock is on my keyboard, and my optical mouse lights up. 

Is there anything else that I can try? Is it still possible to get Ubuntu on my machine? :mad:

Thanks advanced!

---

### Post by torgrot on 2007-12-31
During the POST hit f2 or f12 or whatever key your BIOS requires to get into setup.  At least make sure your system can see the keyboard.

torgrot

---

### Post by Metallic Blade on 2007-12-31
Alright, I'll try that. I'll report back on the result.

---

### Post by Metallic Blade on 2007-12-31
I went into my BIOS setup, found the setting for PS/2 mouse. By default, it was set to, "Auto Detect". I set it to, "Enabled". Saved BIOS, and started the 7.10 livecd again. Yet, STILL no mouse or keyboard. 

Any other suggestions? 

Thanks.

---

### Post by mandrill on 2007-12-31
I know this may sound ridiculous, but my entire system froze up one time when my mouse batteries ran low. New batteries, everything fine.

---

### Post by Metallic Blade on 2008-01-15
Wow, how clueless was I? I forgot that my CPU was a 64 bit. So after I ran Ubuntu 7.10 64-bit live CD, success! My mouse and keyboard actually started to work. I was trying to run the 32-bit instead of the 64-bit. 

Thanks for the help.

-SOLVED-

---

