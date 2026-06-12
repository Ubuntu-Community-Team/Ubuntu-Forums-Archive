---
title: "flash is feezing jaunty"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Meow27 on 2009-04-11
i had this problem in ubuntu fiesty where the nvidia graphics drivers were no good and would crash the system all the time, im not 100% sure its the nvidia driver though this time


when im playing a online video, my computer will simply freeze no side terminals, nothing can be done at that point

---

### Post by beartard on 2009-04-11
You're not alone.  The same thing happens in Kubuntu.  The normal 32-bit flash won't work at all for me, so I tried Adobe Labs' 64-bit flash.  It works fine, but the freezes happen like you say.  Sometimes, my desktop freezes on login in the same way, so I'd definitely say it's a problem on nvidia's side.  Have you tried turning off compositing and seeing if you get the same situation?

---

### Post by hype on 2009-04-11
Just had a total system freeze this morning browsing this site [http://labs.adobe.com/technologies/textlayout/](http://labs.adobe.com/technologies/textlayout/) (the Adobe stuff i halflly care about, just saw a news...)

 I think i clicked on the globe to select another language, system was starting feel sloppy, then totally unresponsive after a few seconds.
 I used sys-request to reboot. 

I'm on ubuntu Janty 64bit, i use opera, and flash from adobe website.
Who do we report a bug to? :p

Edit: for 99.9% of others flash stuff i usually use, i works "quite" good; just noticed this bug this morning. It's the first time i actually see jaunty crash :( 

And btw, i use Opera 10 latest build from Opera Desktop Team blog: this is not supposed to be stable , even though it's quite fast and good since a few builds now. :)

---

### Post by davidgurvich on 2009-04-11
Try using the 'nv' driver for Xorg and see if there is a freeze.  I also had a motherboard where using the nvidia driver would reliably freeze the system, but only when using a particular network driver.  If I disabled that driver from loading there was no freeze.  Haven't seen that with recent kernels (2.6.28).

---

### Post by Meow27 on 2009-04-11
ok i dont think its flash anymore. i think its firefox

that or wine

but it seems jaunty cant handle anything anymore :/

---

