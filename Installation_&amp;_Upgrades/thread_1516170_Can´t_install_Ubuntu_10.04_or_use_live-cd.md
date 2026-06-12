---
title: "Can´t install Ubuntu 10.04 or use live-cd"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by twitterritter on 2010-06-23
I recently downloaded ubuntu 10.04 and I want to install it on my old computer. 
But when I boot from the cd it all looks fine in the beginning but the promt where it ask if I want to install ubuntu or want to test it via live-cd is not readable cause the screen looks kinda like a chess board, half of it being the actual window with text and all and the other half are only black or white.

I thought it might be because of the cd but it worked fine when I used the same cd on my other computer. I also dont think that its because of the cd-drive because I tried both with the same problem.

I assume that it has something to do with the graphics-driver or -card.

My system is a 
Fujitsu Scaleo P
Intel Pentium 4 
ATI Radeon X700 SE

---

### Post by darkod on 2010-06-23
When booting with the cd, hit any key at the first splash image. It should show you a main menu. You can hit F6 (or was it F4) for advanced options, and look for Safe Graphics.

After selecting safe graphics, select the Try Ubuntu option to try and load it from cd. See if that worked.

If not, also look at other advanced options to boot, like nomodeset, noacpi, etc.

It will be trial and miss until you hit the right option. Once you know what made it work, you can install and implement that option permanently, or in some cases the first boot after installing is enough to get a needed driver and work fine after that.

---

### Post by twitterritter on 2010-06-23
thank you for your quick answer darkod.

I tried to find the Safe Graphics mode under F4 and F6 and I just read that it is supposed to be under F4. But the only options I get there are "Normal", "use driver update disk" and "OEM install(for manufacturers)".

I also checked the cd for defects but none were found.

One thing that might be important is that when I started the cd with nomodeset, my monitor gave me an error saying that it does not support such a mode.

Well, I´ll keep trying the other options posted under F6 but if anyone has any other ideas, feel free to post.

---

