---
title: "Will Radeon drivers automatically upgrade?"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by nudnikian on 2012-10-11
I installed Ubuntu 11.04 on a GA-A75M w/ A4 3300.  11.1 and 12.04 would not install and gave me a black screen. 11.4 started with a non-unity graphics

I found the fglrx driver pkg in update mgr.  WOW it works and I have Unity on 11.4   *BEAUTIFUL*, except I have a strange AMD logo in the bottom right corner labeled UNSUPPORTED HARDWARE.  Weird - this is an FM1 sysmobo w/FM1 APU

What will happen when I update in stages to 11.1 and 12.04? 
Will the system keep the new graphics drivers intact or what? 
How do I get rid of the warning label?  

Unity seems to be running perfectly but I haven't tried and flash videos or streaming HDMI yet.

---

### Post by critin on 2012-10-11
> **nudnikian said:**
> I installed Ubuntu 11.04 on a GA-A75M w/ A4 3300.  11.1 and 12.04 would not install and gave me a black screen. 11.4 started with a non-unity graphics

I found the fglrx driver pkg in update mgr.  WOW it works and I have Unity on 11.4   *BEAUTIFUL*, except I have a strange AMD logo in the bottom right corner labeled UNSUPPORTED HARDWARE.  Weird - this is an FM1 sysmobo w/FM1 APU

What will happen when I update in stages to 11.1 and 12.04? 
Will the system keep the new graphics drivers intact or what? 
How do I get rid of the warning label?  

Unity seems to be running perfectly but I haven't tried and flash videos or streaming HDMI yet.

I never worry about my old drivers because linux installs the noveaus for me--they always work but I don't use any 3D or extras.

Did you Try 12.04 Live before installing it?  You should.  You'd find whether it would run or not.    Run the live as TRY and see if the graphics work in live session.

If 12.04 didn't have graphics the first time, I wouldn't upgrade to it until the problem is found, explained and instructions given on how to fix.   Also the 'unsupported hardware' error message needs to be addressed.

Someone knowledgable will be along soon.

I'd suggest running 11.04 for a while since it works so well and gather all the info you need before upgrading.  It's a good, solid system.    Give it a week or so without putting much personal work in it, then just do a fresh upgrade to 12.10.  It'll be released the 28th or thereabouts.   

But of course there will be issues there too for a while. (new always has a few issues for some hardware because they can't test on absolutely every version out there.)

---

### Post by nudnikian on 2012-10-12
> **nudnikian said:**
> I installed Ubuntu 11.04 on a GA-A75M w/ A4 3300.  11.1 and 12.04 would not install and gave me a black screen. 11.4 started with a non-unity graphics

I found the fglrx driver pkg in update mgr.  WOW it works and I have Unity on 11.4   *BEAUTIFUL*, except I have a strange AMD logo in the bottom right corner labeled UNSUPPORTED HARDWARE.  Weird - this is an FM1 sysmobo w/FM1 APU

What will happen when I update in stages to 11.1 and 12.04? 
Will the system keep the new graphics drivers intact or what? 
How do I get rid of the warning label?  

Unity seems to be running perfectly but I haven't tried and flash videos or streaming HDMI yet.

  SOLVED! I didnt have the patience to wait for suggestions.  In fact I suspect its beter to let bumbling neubies struggle and puzzle things out sometimes.  I reasoned if the correct driver was avail in 11.04 update mgr, then it would likely follow the update to 11.1. what was curious is that there was base VGA support in 11.04 but not 11.1 or 12.04. If the update died it was no loss, just a lot of wasted HDD grinding.  That VGA video saved the whole project because im not skilled enough to patch a black screen "failed" installation with a driver, if it is even possile. The upshot of all this is that 12.04 is up and running and almost everything works as expected. I'm guessing the little AMD semi-transparent logo w/ UNSUPPORTED HARDWARE warning must be some kind of CYA generated in the BIOS or a video self-test. Ive contacted AMD tech support.      Excellent - thanks for all the help, I got a lot of clues from former posts concerning Radeon support.

---

