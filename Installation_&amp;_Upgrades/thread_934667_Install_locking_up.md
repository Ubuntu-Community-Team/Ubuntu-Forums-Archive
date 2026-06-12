---
title: "Install locking up"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by DnDer on 2008-09-30
Running an old IBM thinkpad that used to run 98SE just fine. I was using it to sample Xubuntu for the first time.

P3 chip with 384 MB RAM and the HD is less than 10 gigs, maybe 5... Sorry, I don't remember.

I'm using the desktop CD, and I downloaded it from the Waterloo/Ontario mirror. I've checked the memory and the diagnostic options, and I think it rang up fine for me. But attempting to install or launch it without install causes it to lock up.

I get as far as the xubuntu logo and the sliding bar, but after bouncing back and forth about 3 times, the bar freezes and the entire installation seems to stop cold.

Suggestions? Did I forget something?

---

### Post by prshah on 2008-09-30
> **DnDer said:**
> 
P3 chip with 384 MB RAM and the HD is less than 10 gigs, maybe 5

I'm using the desktop CD,

I get as far as the xubuntu logo and the sliding bar, but after bouncing back and forth about 3 times, the bar freezes and the entire installation seems to stop cold.

Specs look OK for Xubuntu.

Use the "Options" from the menu from where you launch the live Xubuntu. (I think it's F6?). Choose the option of "acpi=off" and check if it works. If not, try the other (or a combination) of options. Post back if you still face trouble. 

Remember what options you have used if you get it to launch successfully. You may need them after the installation has completed.

---

### Post by HotCupOfJava on 2008-09-30
I have had similar problems on an old Compaq. Hardware requirements seemed OK, but the Live CD would freeze and an installation attempt would do the same. I have had several other successful installs with the same CD, so I know it was not the CD. Some of my successful attempts were with even older machines. I figure it to be a hardware incompatibility of some sort. I know this doesn't really help you, but misery loves company....

---

### Post by DnDer on 2008-10-01
> **prshah said:**
> Specs look OK for Xubuntu.

Use the "Options" from the menu from where you launch the live Xubuntu. (I think it's F6?). Choose the option of "acpi=off" and check if it works. 

It was F6, and it did work.

Now, because I'm new to Linux, period... Can you explain just why turning off the energy saving standards (that's what ACPI is, right?) actually allowed the computer to boot and isntall when it wouldn't before?

And use small words and terms. I'm not even sure I qualify for a 100-level class when it comes to open source.

---

### Post by DnDer on 2008-10-01
Correction. It passed that cycle of the installation.

I watched text roll across the screen, showing what it was creating and installing. I looked away, and when I returned, the screen was black. The disc is spinning, and the HD light has been on since I last posted. The screen,however remains black.

Something is either taking forever to install, or it's caught on something?

[COLOR="Red"]EDIT:[/COLOR] No sooner do I post, then text starts reappearing on the screen. >_< Sorry.

---

### Post by lisati on 2008-10-01
> **DnDer said:**
> Correction. It passed that cycle of the installation.

I watched text roll across the screen, showing what it was creating and installing. I looked away, and when I returned, the screen was black. The disc is spinning, and the HD light has been on since I last posted. The screen,however remains black.

Something is either taking forever to install, or it's caught on something?

Maybe the screensaver has kicked in. Try pressing the shift key or moving the mouse....

---

### Post by DnDer on 2008-10-01
The text disappeared again, and the screen has returned to black for another exceedingly long period of time. Same as before. I trust it will finish installing... Eventually...

But the shift key (either of them) isn't working.

[COLOR="Red"]EDIT:[/COLOR] Now the screen is a messed up line of Xubuntu logos across the top of the screen, and the bottom 2/3 of the screen is in a b/w static (unmoving) television-snow pattern.Assuming this was just the screen saver, with botched video drivers, I tried pressing shifts, with no luck. I'm closing the laptop for the night, even with the HD and CD still running. Not worth staying up longer for, and I can troubleshoot in the morning...

---

