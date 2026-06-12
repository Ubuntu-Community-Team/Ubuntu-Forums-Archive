---
title: "Incorrect Time"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by *B* on 2008-02-10
I succesfully changed my laptop to dual boot Ubuntu/XP and decided to do the same thing on one of my dekstops. The only difference is, I already had XP installed on the master IDE. I moved the XP drive to the secondary IDE, put an empty drive on master IDE and installed Ubuntu on it, chainloading XP. No Problem there. The problem is, the system time in Ubuntu is always wrong in some way. Even though I set it to central time (my time zone) upon first boot, it was off the 6 hour difference. If I changed the time to make it correct in Ubuntu, it adjusted the time in BIOS and then BIOS and XP were wrong. WHen I would set the time back in XP and BIOS, then Ubuntu was wrong. I came to this forum and found a solution to check  "use UTC". This works.... partially. Even though I leave it checked, the time is still off at times, like right now. If I reboot the system, it may be correct. The thing is, even when the time is correct, everything time wise that has to do with the system is off 6 hours. In other words, if I boot up Ubuntu and the clock is correct, and then I open Thunderbird and receive an email....... the time stamp on the email for when it is received is 6 hours off. Or, if I create a document, or alter a file, the system times shown for those files is off 6 hours, even though the time displayed is correct. Anyone have any ides?

---

### Post by linuxmagick on 2008-02-10
You may want to try this, if you haven't already.  In Gnome, right-click the date/time in the top right corner and choose *Adjust Date & Time*.  Here where it says *Configuration*, choose *Keep synchronized with Internet servers* from the list.  If ntp support isn't already installed, you will be prompted to install it and can just click on the *Install NTP* button.  After it's installed you can select the servers that you want to keep the time synced with.  That should help keep your clock in Ubuntu accurate.  Let me know if you need anymore help.

---

### Post by *B* on 2008-02-13
Thanks for the suggestion. I tried it and all that did was make the time shown down in the panel different than what is shown in the system properties when I click 'adjust time". The correct time as I type this is 10:17am. The panel shows 3:17pm, when I click adjust time, the box that comes uip shows the correct time. Honestly, this is getting discouraging. Something as simple as setting the time shouldnt be such a problem. The entire time interface is silly. You have to pick a "city" to choose your time zone. Why? Now you have to be familiar with where cities are exactly to know which one to pick. Why not just have a list of time zones? The cities listed dont even have listed next to them what time zone they are in. So, for me (living in the central time zone, and no cities listed that are close) its trial and error.

---

### Post by *B* on 2008-02-16
Nobody has any idea of how to rectify this?

---

### Post by geekygreen on 2008-02-18
Sigh.  I was hoping the answer was already here...I am having the same problem.  I run a dual boot system because I have not found drivers for all my USB hardware (Film Scanner and MIDI digitizer...) but the difference in time is annoying.  :confused:

---

### Post by geekygreen on 2008-02-18
check out this thread, it worked for my problem...

[http://ubuntuforums.org/showthread.php?t=633848]("http://ubuntuforums.org/showthread.php?t=633848")

my thanks to Ifnomore for pointing the way to the above thread, and to NilsE  for posting a fix that works!

---

### Post by *B* on 2008-02-25
Thanks for the info. I had given up on this. I read the thread you linked, applied those changes.... now my time is off an hour (ahead) for some reason, instead of the 6 hours ahead (difference in time zones). I live in the central time zone and have chosen America/Indiana/Vincennes as the city to set the zone for, since there is nothing as simple as "choose time zone". This is the same city I have chosen on my laptop and the time is correct on it. This is getting very disturbing, that something as simple as setting the clock properly is this much hassle.

---

