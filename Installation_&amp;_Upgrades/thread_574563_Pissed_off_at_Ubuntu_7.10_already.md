---
title: "Pissed off at Ubuntu 7.10 already"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by mmilitia9 on 2007-10-13
Maaann, I downloaded the Release Candidate just now.  I burnt it to a CD... and I loaded it up.  I picked "Start or install Ubuntu" option at the screen.  It loaded.. or looked like it was loading.  Then it just turned my monitor blank for 10 minutes and didn't do anything.  

Now.. I know this has something to do with my Nvidia Geforce FX 5500. On fiesty, I had to over come that by taking in all these stupid instructions on how to install or make it work on Ubuntu.. But I just was sooo hoping they finally fixed this issue for the cards  Is anyone experiencing the same issues with the same card?  Is there a way to go around this issue without having to enable to stupid onboard graphics through the bios and reading more "How-to" instructions for Nvidia Geforce FX 5500 cards?

Thanks for the info,

Dominick


System:
2.8 Pent 5
1 Gig DDR
Nvidia Geforce FX5500
160 GB Harddrive

---

### Post by tgalati4 on 2007-10-13
What happens when you boot in safe-graphics mode?

---

### Post by bulldog on 2007-10-13
Well,sorry to read about your bad experience with Gutsy.
I have a nvidia card too and installed the beta version and didn't have any problem with it.
Booted fine,did mention there were drivers available for the graphics,installed them and running without a hassle.
It won't help with your problem though, just to let you know it could be done without any trouble.
I have a 8800GTS 640MB so I needed the propietary drivers to get it to work.

---

### Post by louieb on 2007-10-13
Do you use the PCI version of the card? I have the AGP FX5200 in two pcs. Not a problem with either. Just installed xUbuntu Gutsy beta on one **using the alternate CD**. VESA or the NV driver either one works with the card. 
Neither of my pcs has an on board graphics card wondering if thats why you are having a problem?

---

### Post by Frak on 2007-10-13
No problems here with an FX 5500.

---

### Post by mmilitia9 on 2007-10-13
Yeah, I bet it is because of the on board graphics card.  Hey, last poster... Do you have an on board graphics card as well?

Yes, the card is PCI.  

Safe graphics mode doesn't work either.  Leaves me hanging with words on the screen this time.

I'm trying the alternative CD.. hopefully it'll work after its installed.. I have a feeling the installation is going to be simple but when I arrive to the desktop it's just going to crap out... but I should be thinking positive tho.. haha 


Dominick

---

### Post by Frak on 2007-10-13
Mine is PCI (not onboard)

Alternate should work, but I couldn't guess why it wouldn't work :confused:

---

### Post by mmilitia9 on 2007-10-13
But do you also have a On board too?

---

### Post by ExquisiteDeadGuy on 2007-10-13
I just installed 7.10 with an nvidia 6100 series and if I use the restricted driver, the machine locks hard every 5 minutes :(

---

### Post by vek on 2007-10-13
> **mmilitia9 said:**
> Maaann, I downloaded the Release Candidate just now.  I burnt it to a CD... and I loaded it up.  I picked "Start or install Ubuntu" option at the screen.  It loaded.. or looked like it was loading.  Then it just turned my monitor blank for 10 minutes and didn't do anything.  



This happened to me too.  But it turns out its the screensaver or something.  Cuz it goes away the instant I move the mouse.

---

### Post by mad chey on 2007-10-13
we have a pc here with fx5500 agp card in it, but no on board graphics and works perfectly fine with fiesty and the nvidia drivers from the repository, not tried it with gutsy yet

---

### Post by Frak on 2007-10-13
> **mmilitia9 said:**
> But do you also have a On board too?
No onboard. This computer came with an AGP ATi Rage/Fury Pro, and I swapped that out with a PCI Nvidia FX 5500. Way better.

---

### Post by mmilitia9 on 2007-10-13
Hmmm... I see.. Well, my computer has integrated graphics on it.  This could be the problem.  I just told the BIOS to use that card instead of the PCI Geforce FX5000.. The Ubuntu LIVE CD booted up in about 4 minutes... I don't understand why it's giving my PCI card such troubles booting up in Ubuntu... 

I'm afraid if I install Ubuntu with the integrated graphics enabled and then switch back using the PCI card.. It'll not work period.  and then i'll be super pissed when I wasted that all the time updating/installing the OS to have it not work in the first place.  I tried this method with Fiesty before and it didn't work either.  I got fiesty working through some how-to's on the web when the geforce issue was pretty big.. 

It's just making me mad that it doesn't want to work right off the bat.  I hate how I have to go around different doors to get the damn thing working.  


It's def not a screensaver by the way(To the dude that posted that suggestion)

Anyway, if there anymore suggestions.. I'd appreciate it.. but I guess until then.. I'll just wait until the actual release of Ubuntu comes out.. cuz I would hate to make the RC work and when I update to final or something... the whole thing crashes on me.. haha.  :) anyway.. suggest away :D

Dominick

---

### Post by Frak on 2007-10-13
This may sound really dumb (thinking of solutions) but is your monitor plugged into your integrated graphics or the PCI card?

As I believe, if you bought a PCI card, it would have a seperate port.

If thats not it, I'm still thinking.

---

### Post by mmilitia9 on 2007-10-13
Oh no.. Im sorry to confuse you.. lol No, in order to see Ubuntu I have to plug it into the integrated spot.

Update: But now that I enabled the drivers for the Nvidia card.. I can't even view with either card.. haha

Anyway, 

I installed Ubuntu 7.10 through the alternative CD.  It's still doing the same thing to me from the harddrive too... Hmm.. I'm going to try a system update and and maybe mess with the X11/xorg.. thing.. haha.. Maybe its a setting like in 7.04 that I have to switch around

---

### Post by Shannon_VanWagner on 2007-10-21
Hi there,

I installed Ubuntu 7.10 on my Dell Inspiron 2650 and enabled Nvidia GeForce Go proprietary drivers and after rebooting the screen either was blank, frozen, or sometimes would show some garbled output.

Here's what I did to fix it:

On bootup, hit F2 to enter the Dell BIOS
For the section marked "Video Display Device", switched the setting from "Simul Mode" to "LCD Mode"

Saved the setting with F10 and then exited and rebooted.


On reboot everything came up normal.

Go Linux!!

Hope this helps!

Shannon VanWagner

---

