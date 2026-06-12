---
title: "Keyboard/mouse problems prevent final installation?"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Swimmie1 on 2010-07-27
Ok, I've gotten no response at Ubuntugeeks, so it's up to you!
 
I've been trying to run 64-bit 10.04 LiveCD for two+ days now. Machine is an Acer Aspire E7300 (M3641) w/ nVidia GeForce G100, and garden variety mouse + keyboard plugged in via USB.
 
The farthest I've gotten is to the actual desktop screen; the only way I've been able to get even that far is by changing the boot options to replace "quiet screen" with "nomodeset", and changing the BIOS to enable legacy keyboard support. From what I've read, all this is necessitated by my having a (ubiquitous) graphics card.
 
Once the desktop screen appears, however, the cursor is frozen in the middle of the screen and the keyboard has no effect whatsoever. I'm dead in the water.
 
I've tried toggling the "enable legacy support" for the mouse, per someone's suggestion, with no effect.
 
Please, please, please help me.
 
[I'm not a programmer, and this is my first foray into Linux, and please forgive what I'm about to say...but I'm beginning to wonder: is this really what the great Linux revolution looks like? Machine-by-machine recoding of each and every OS upon installation?]

---

### Post by heimo on 2010-07-27
I'd suggest trying another version of Ubuntu or installing in text mode (at least on install dvd you can press any key at the beginning (when there's some icons on the bottom of the screen) and then choose different options, like installing in text mode. You could try 10.10 (not released yet) or 9.10, or another distribution. I would bet that the problem is not about keyboard and mouse, but some other hardware, like graphics card / GPU.

---

### Post by Swimmie1 on 2010-07-27
Thanks for the speedy suggestion.
 
FWIW, i've suspecting the graphics card as well.  It seems to be a complaint all over the forums, yet there's no consensus response.
 
I have been going to the non-graphical installation options screen already, just to get as far as I have (in order to do the whole "nomodeset" thing).  There's no "install in text mode" option presented, but I see that if I hit ESC it sends me to a text mode that looks like a command line --  "boot:"  
 
But at that point I'm guessing I need to speak Linux to tell it what to do.  And my programming training ended 24 years ago with PASCAL.
 
Surely there's some boot option command I can give to work around the nVidia card and still retain my keyboard/mouse???

---

### Post by heimo on 2010-07-27
Text mode install is probably only option on alternate install CD.
[http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

I'd burn couple different versions, older and newer, and check if some of those work.

---

### Post by Swimmie1 on 2010-07-27
Just tried PuppyLinux 5.0.  Exact same situation:  the graphical desktop appears, along with First Run Configuration menu, but cursur is frozen in middle of screen and keyboard does nothing.
 
Am I correct that the keyboard/mouse data "runs through" the graphics card in some sense?
 
I noted that during the pre-Linux boot process, my computer listed both keyboard and mouse as recognized USB devices...

---

