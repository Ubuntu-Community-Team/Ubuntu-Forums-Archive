---
title: "Install hangs"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by greenwom on 2010-05-06
Before I spell out the problem, I've downloaded 2 iso's and made multiple usb sticks.  Same problem....  Mythbuntu 32 bit

When I boot the live usb stick I get to the splash screen with the
keyboard equals "the man in the circle" (accessibility icon).

that is as far as it goes.   

I just put this machine back together (I only changed dvd drives....)

It was running 9.10 just fine....


Where do I go from here

---

### Post by tom4everitt on 2010-05-06
Did you try the alternate install cd?

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

---

### Post by greenwom on 2010-05-06
i tried mythbuntu 32 bit and the regular 32 bit iso.  same problem

---

### Post by tom4everitt on 2010-05-06
But did you try the text-based installer for instance?

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by greenwom on 2010-05-06
I'm downloading it now...

never had this problem with this machine

---

### Post by frantid on 2010-05-06
there's a decent sticky here, I think I've read something similar in that thread.

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by greenwom on 2010-05-06
Well. I went back to the myth iso.

If I press the space bar I get the menu at boot, if I select install or try it hangs.  I pressed escape and it went to the myth logo for a sec.

It hangs at a black screen with a flashing cursor....  


If I select expert mode from the menu and then try to install it give me a pop-up with the path and will not install.

---

### Post by Catharsis on 2010-05-06
Do you know what graphics card you have?

Try:
1) At the purple screen with the keyboard and stickfigure, press Enter to get to the menu.

2) Select your language, and then make sure "Try Ubuntu without making changes" is selected (or whatever they call it these days).

3) Press F6 and then Esc. Add "i915.modeset=1" after the "quiet splash" part, and then hit Enter.

Let me know if that works. If not, try adding "xforcevesa" instead of "i915.modeset=1". If you have an nVidia card, try "nomodeset".

---

### Post by greenwom on 2010-05-06
i915  - went to the black screen with the blinking cursor
xforcevesa - same
nomodset - locked it up.....

---

### Post by Catharsis on 2010-05-06
When you get to the blank screen with the cursor, does your keyboard still work? Does the Capslock light turn on? What happens when you type Ctrl+Alt+F2? 

Do you still have an old install or another LiveCD? It'd be nice to know your graphics card: "lspci | grep VGA".

You can always try more kernel parameters: replace "quiet splash" with "i915.modeset=0" or "xforcevesa noapic noapci nosplash irqpoll".

---

### Post by greenwom on 2010-05-06
Well, I tried the Alternative CD as well...

Same black screen with the cursor.

So I'm guessing a hardware issue?  any ideas.  

I recently swapped drives on this machine to salvage files off of a family member's PC.  

When I try to boot the old install of 9.04, my grub menu is messed up?  
It hangs on the grub loading screen.
(I didn't notice this until now).

So where do I go on the trouble shooting?  Drive cables are all secure.  
Doesn't seem like a drive issue?  

It's 11pm, I'm gonna call it a night on this one.  Hope someone has an idea

---

