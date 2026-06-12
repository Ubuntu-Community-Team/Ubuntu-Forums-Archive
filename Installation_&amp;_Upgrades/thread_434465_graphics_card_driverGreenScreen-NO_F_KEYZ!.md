---
title: "graphics card driver?/GreenScreen-NO F KEYZ!"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Sidistyk on 2007-05-06
Right now I'm running....

Windows Xp
AMD Athlon64 3000+ 
3 gigs DDR2 RAM 
Nvidia GForce 6600
Asus SKI-Deluxe motherboard 
Western digital hard drives
Sony DVD RW DRU-720A 
Floppy- FDC generic....

I would like to eventually run a dual boot between XP and Ubuntu but....
When I attempt to boot from the cd, I progress through the flash banner and end up with a green screen where I cannot utilize my F keys... 

Thanks for taking a look...
.B.

: ALERT: I have never connected to a linux OS before, I have wanted this for a few years now but  know veeeerrrrrry little. I don't know any programming language, an I don't know what the difference is between that and scripting, though I will be learning that soon enough I 'spose...On the plus side,  I am a bright guy and will have no problem learning this...

---

### Post by Sidistyk on 2007-05-06
Forgot to mention...I'm installing the 7.04 AMD64 bit version, I tried the alternate first with the same issue...

Okay, so I'm booted and operating from within Ubuntu but using graphics safe mode....whats next?

---

### Post by Scheater5 on 2007-05-06
hmmm...green?  Well, my first idea would be that the Xorg crashes, bt that would leave you with a terminal ("xorg" and "terminal" are terms you will be learning soon, but for now they are beside the point).  I would think that Ubuntu doesn't recognize your monitor driver.  From your description I don't see anything funny that would cause this.  Are you running an weird/unusual/complicated monitor setup, i.e. dual monitors, or running as a thin client?
Perhaps can you be more descriptive about "green?"  You say you cannot use your F-keys - that would imply that you can see the screen, but it is merely tinted green (because you would have had to be able to do things to know the rest of your keys work).  This is a much easier fix.

---

### Post by Sidistyk on 2007-05-06
Thanks so much for the quick reply...

So the monitor setup is a single CRT monitor, I don't know about the "thin client" so I would guess not....
The screen is a primarily green set of vertical lines, pixel-strip that flashes and glows from under with white stripes in that vert pattern. Between the primarily green lines is the black background, so difficult to focus on it really becomes more a slight contrast than strip of pixels...(This has been a blast to try an explain!!!) As I let it go on, the pixelation becomes multi-colored and random, isolated, square patterns turn purple/pink. This will continue as the pattern gets wider and the pink spreads, while sticking to the very basic pixelated box patterns with the contrasting black underneath...

I hope that helps...?
Thanks again...
.B.

---

### Post by Scheater5 on 2007-05-06
Wow...I have no idea what could cause that, but I have one more idea of what it *might* be.  
Screen resolution.  
I had problems when I upgraded to 6.10 six months ago that sound vaguely similar to your's.  Unfortunatly, if you can't see you screen well enough to change the monitor resolution in the menu, you are going to have to edit x.org in a command line.  I am probably not suited to guiding you through that except under one circumstance - if you can boot into a live cd, and it works normally, then I can tell you how to copy x.org from the live cd session onto your harddrive.

---

### Post by Scheater5 on 2007-05-06
Ah, I re-read your posts and see that you are running from the live-cd and that is where the problem is.  And my next suggestion would be to try the alternate-install, but I see that doesn't work either.  This is interesting, indeed.
See if you can get to a terminal.  Boot into the live-cd, and after the desktop loads (assuming you can tell when that is) press <ctrl><alt><F1>.  I'm not sure if that will help your case or not, but knowing that you can access a terminal may be important if someone besides me knows what is wrong.

---

### Post by Sidistyk on 2007-05-07
Hey alright, so I do get F key function with Ctrl+Alt+F1, (I thought I tried that? Musta' done somethin wrong!) the screen snaps outta it, but I'm not sure its a command line, it says something about "sudo"...says if I want to know more to enter "... sudo_'sumthin?", an i can access at root? When I tried the command it gave me a little feedback but after 10 minutes nothing changed so I rebooted to tell you about it.** I really believe its a graphics driver, my friend was here the other day when we first started messin with Linux on my machine an he got this same issue- said at the time, he re-routed a driver an it worked fine. That was with Debion, but this is the *exact *same symptom. I have been able to load in graphics safe mode, don't know if you caught that, but whats the difference and why would that matter? 
.B.

---

### Post by Sidistyk on 2007-05-07
After another re-boot, I came in on graphics safe mode an I get an error reading:

"error starting the GNOME settings Daemon...(A bunch of jibberish possibilities and then...) GNOME will try to restart the settings daemon next time you log in"

This help at all?
.B.

---

### Post by Scheater5 on 2007-05-07
I'm afraid it's over my head.  I will keep monitoring this post.  Perhaps seek alternate avenues of aid, like the IRC channels, if no one else in the forum responds.

---

### Post by Sidistyk on 2007-05-09
Thanks for the time an effort though Scheater, I'll check out the IRC. Anyone else try to take a stab at this?

---

### Post by Sidistyk on 2007-05-10
Must....stay...

---

### Post by Sidistyk on 2007-05-11
near top...

---

