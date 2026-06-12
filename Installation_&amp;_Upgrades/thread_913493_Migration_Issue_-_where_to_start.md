---
title: "Migration Issue - where to start"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Whydoe on 2008-09-07
I tried to move all the contents of my computer (hard drives, DVD, graphics card, sound card, and modem) to another computer which has a faster processor and better motherboard.  However, once everything was moved over and I booted, Ubuntu no longer connected to the internet.  No dial-tone.  BIOS settings were checked.  It was connected correctly, ie. there was a dial-tone.  I tried to boot into my XP partition, I rebooted and selected XP.  After about 2 seconds there was a fast blue screen (couldn't see any number) and a reboot.  Cannot boot into XP at all.  However, I tested the computer with JUST an XP install, and it works no problem.  
So, Ubuntu works as far as sound, and printer.  Just no internet.  The NVIDIA driver failed too, but I only realized after I moved everything back over that a simple restore of the xorg.conf file my backup would've most likely have solved that problem.
I've had issues with my current computer with IRQ settings and modem conflicts etc before, but they were all solved.  I moved everything back to the old computer and things are back to normal, just slower.  
Where would I start to find where the problem is coming from?  I'm guessing it's a BIOS settings I'm missing.  I would assume an IRQ setting, but Ubuntu sees the modem, it just won't dial-out.  I tried to reinstall the driver (it's an ess modem) I got an "error activating modem driver via insmod".  This was after the compilation was completed.  If you need more detail about the issues to make any guesses let me know.  Till then, I'm back to the PIII.  :(

---

### Post by Pumalite on 2008-09-07
Start from scratch.

---

### Post by Whydoe on 2008-09-08
Both OSs?  On dial-up?  I'm sure I could tweak settings in the BIOS and Ubuntu to get Ubuntu's internet working, and possibly doing a "Repair Install" of XP.  I'm looking for something less extreme than a fresh install of everything - which is what I'm guessing you mean by "from scratch".  From what I've learned from other forums on XP not booting, or booting to BSOD and then rebooting - it comes down to different IDE controller drivers.  As it is, I'm going from a VIA chipset to a SIS chipset.  I'd just like some input as to where to look for possible solutions before I try to move things over again.

---

### Post by Whydoe on 2008-09-11
I tried to move all the components over again, tweeking a few things in BIOS and getting XP setup for the move (ie. removing all references to VIA chipset). And, no, don't do it.  Not even Ubuntu started up.  XP blue screens and reboots, and Ubuntu just shuts off after trying to detect hardware... and in recovery mode.  So, ya, you need a fresh install... expecially when moving between 2 different chip sets.  And quite frankly, for the sake of a couple extra USB ports and a bump from a Pentium III 600 to an AMD 1.6 Athlon.... I'll save my time and money for a brand new system.  Fun to try... sorta.

---

### Post by helmut_hed on 2009-03-31
Hi Whydoe, this is a pretty late response, but I haven't done a search for "ESS modem" in a few months :)

Anyway, if you are still experiencing problems compiling the ES2898 driver, please post the make.log file you get from running the setup script (or send it to me by email - my address is listed in the README).  You should also make sure you have the latest driver version - presently that is 0.5.

Regards,
Jeff

---

### Post by Whydoe on 2009-03-31
I have the new modem up and running with the new drivers.  A bit of a pain with having different gcc and gcc kernel versions for compiling.  But I figured it out.

---

