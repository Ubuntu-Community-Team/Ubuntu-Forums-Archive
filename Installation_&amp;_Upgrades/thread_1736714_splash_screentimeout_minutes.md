---
title: "splash screen/timeout minutes"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by Gustav521 on 2011-04-22
[B]I need help!  I have clean installed Ubuntu 10.04. After every 10 min. or so of not 

moving the mouse, I am asked for my password. How can I extend those short 

min. to say an hour??  Also, at startup I do not have a splash screen only a black 

screen for about 1min or so. How can I watch the splash screen at startup?? Thank 

you. -gustav521[/B]

---

### Post by coffeecat on 2011-04-22
For the password issue, you need to stop the screensaver locking the screen. Go to System > Preferences > Screensaver and untick the box that says, "Lock screen when screensaver is active".

The black screen and no splash: have you installed a proprietary video driver from Additional drivers?

---

### Post by Gustav521 on 2011-04-22
[B]Thank you "coffeecat" for your quick response: your screensaver solution worked well! No, 

I have not installed any new drivers. I have read that grub2 might not show the splash, 

and that you have to intervene. I don't remember the solution! I had the splash with 9.04


"Jaunty", but with 10.04....  Thank you for any additional help! -gustav521[/B]

---

### Post by coffeecat on 2011-04-22
The reason I asked whether you had installed proprietary video drivers is that they can corrupt the "Plymouth" splash screen that has been used since Lucid/10.04. Jaunty used the completely different usplash so I doubt whether a fix for Jaunty would work in Lucid.

Perhaps someone else may be able to suggest how to fix your Plymouth splash. I don't know what else to suggest.

---

### Post by Gustav521 on 2011-04-22
Hello again "coffeecat"! I do remember some talk re plymouth and the splash screen not coming up. "koala" ( [http://www.techsupportforum.com/forums/f64/ubuntu-10-04-splash-screen-timeout-minutes-568367.html#post3232904](http://www.techsupportforum.com/forums/f64/ubuntu-10-04-splash-screen-timeout-minutes-568367.html#post3232904) ) has just sent me this:

"Check in BIOS to see if there's a 'Quiet Boot' option.
If this is enabled, there will be a splash screen displayed during POST.  If it's disabled, you will see the usual POST messages or a black  screen."

I'll check it out and post here in a day. Hope this works! Thanks again!! -gustau521

---

### Post by Gustav521 on 2011-04-24
Hello "coffeecat": I was wrong, it is not about the Plymouth splash screen at all! After the 

Bios splash, there use to be a Grub (legacy) splash in Jaunty 9.04. Here in "Lucid" I am 

getting a black screen for 45 seconds or so. After that I get the Plymouth splash. How can I 

get all that info that is now "in the dark" to be seen?? -gautav521

---

### Post by coffeecat on 2011-04-24
The grub "splash" you refer to I assume is the grub menu. If you are not seeing a grub menu  in Lucid, you need to press the shift key (and keep it pressed) before the POST screen turns to a black screen. Thereafter, once you've selected your entry from the grub menu, expect to see a black screen for quite some time before the Plymouth screen appears, although 45 seconds does seem a long time.

---

### Post by Gustav521 on 2011-04-24
Hello "coffeecat": I saw th grub2 options page, and hit "e". In the grub2 edit menu page I see "splash vga=789" and "quiet splash". Should I do something to either one of these to get the visible splash?? And what should that be, delete?? Thank you, -gustav521

---

