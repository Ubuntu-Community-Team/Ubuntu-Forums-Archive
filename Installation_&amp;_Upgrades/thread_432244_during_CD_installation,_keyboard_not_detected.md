---
title: "during CD installation, keyboard not detected"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by mkramer on 2007-05-03
When trying to install Ubuntu 7.04 from a CD image I am getting stuck very early.  At the initial splash screen that includes the options to install, check memory, etc, my keyboard is not recognized.  Because of thsi I am unable to do anything at all with the install, I'm completely handicapped.  I don't have a PS/2 keyboard available, so I can't work around it.   I'm using an apple USB keyboard.  The keyboard is detected just fine by the BIOS.  This guy reported the exact same problem over a year ago, but there were no solutions offered:  [https://bugs.launchpad.net/ubuntu/+source/gfxboot/+bug/35530](https://bugs.launchpad.net/ubuntu/+source/gfxboot/+bug/35530)

I've been reading another thread in this forum where somebody had this problem, except that he was using a PS/2 keyboard.  He was able to fix the issue by disabling the USB ports in the BIOS to install, and then renabling them.  I just tried disabling the PS/2 ports in my BIOS, but the keyboard still won't work.  

What can I do? thanks

(By the way, I'm a linux newbie.  I've never done any linux installation before, so please don't omit any steps or assume that I have even a basic level of knowledge about linux).

edit: and by the way thanks to everyone out there who works on this project!

---

### Post by mkramer on 2007-05-03
Fixed!

I had to enable "legac usb support" in the bios.  Now it works.  From what I've read:

if you have a PS/2 keyboard and it's not working, try disabling legacy usb or "direct usb" or whatever it's called in your bios.  If you do have a usb keyboard, enable it.

---

### Post by samgod2001 on 2007-08-26
Thank you also had the same problem.  Fix worked perfectly

---

