---
title: "Ubuntu studio does not uninstall properly"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2008-10-16
I tried to install ubuntu studio according to: 
[http://ubuntuforums.org/showthread.php?p=5975950](http://ubuntuforums.org/showthread.php?p=5975950)

I skipped the video which I wasn't interested in. 
When I rebooted my computer I had error messages 
("fatal error: no swap" was one of them). And 
both on turn off and on turn on I was forced to 
watch an animated logo (no wonder these packages 
are so large...). Even the login screen had been 
taken over by ubuntustudio :(. 

Then my sound card was off, the sound was back to 
its default output thought the laptop speaker. It 
had taken me ages to get this sound card working. 

So I did "sudo apt-get remove" for all the packages 
I had intalled and... The removed size was much smaller 
than what came on my computer upon install. 

Well, at least now my sound card functions again. 
But I'm rather upset by this, I thought only stable 
packages were allowed access to the apt-get repositories 
unless one specified otherwise? 

Where could I find a list of all the packages installed 
by ubuntu studio to clean up my computer, please? It 
downloaded Megs and megs of stuff and only removed a 
few Kbs...

Mariane

---

### Post by snowpine on 2008-10-16
You should use 'aptitude' instead of 'apt-get' to uninstall, since you used 'aptitude' to install. This should get rid of all the dependencies as well. Good luck!

---

