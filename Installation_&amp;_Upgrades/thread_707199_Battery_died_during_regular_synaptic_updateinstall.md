---
title: "Battery died during regular synaptic update/install and gutsy now wont boot"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by salviablue on 2008-02-25
Hi!
  I am back as a little less of a noob but still fledgling none the less! 
I was doing a repo update/upgrade through synaptic (you know, when the icon shows stating new updates are available) and there was rather a lot to be done (hadn`t done it for  a week). Anyway, I should have had enough battery power to get me to work so I could have plugged it in, but I didnt (have enough battery power), I later found out it was unplugged about 1/2hr before work, wife - phone charger!
  It had downloaded everything and was just going through the compile/make/install malarky (or possibly ldconfig deferred whatsit?) when the power died. BOLLOX I thought, now thats going to be a bugger! And right i was!
  I couldnt boot into ubuntu through either grub menu (usual or recovery). I chrooted in from the live cd and did the whole (from su) apt-get business, then tried the dpkg business (you know the ones if this has happened to you! I will fill them in later when i have more time or if someone asks) but everything seems to hang on two repo`s that wont install/remove/purge/update/upgrade nothing, just keeps coming up with the whole `package way too far out man use that dpkg configure or apt-get remove magic to fix it, try installing before removing ` but nothing seems to help.

 I read somewhere about looking for an older kernel image and subbing that in the boot, so I did. Booting with the recovery mode gets me to a command line, but with no networking support and the normal image gives me the blah blah error - dropped to psudo shell {initrmfs}  (or some such) with very limited commands (not even an ls!). Before doing this image swap both choices got me to that initd shell (or whatever it is). 

Any help would be great, I have to go for now but I will post some usefull info (like screen output etc!) 
Thanks

---

### Post by salviablue on 2008-02-28
Hi, no one up for the challenge eh? Or is it just far easier to reinstall. The only problem is, is that i lose most of my programs and have to reinstall them, but at least i get to keep my settings. BALL ACHE!

Well I actually did just reinstall and then had loads of probs with reinstating my sound, just like the initial install, but unlike the initial install, the fix didnt work! But after plenty of searching around i copied the sound driver/module bit from the 386 kernel image onto the generic kernel image (which is what i am using since one suggested fix was just to use the 386 kernel, but that caused loads of other problems).

Well dont think this will help anyone, but just in case!

---

### Post by harold4 on 2008-02-28
If everything downloaded before the power died, you should be able to just run "apt-get install -f" in the recovery console, since the .debs should be cached.

---

### Post by salviablue on 2008-02-29
I tried that and it came up with the whole unresolved dependencies thing. something like 
"the following packages are too fubar`d, you should reinstall them before removing"
trying to reinstall came up with the same response.
Trying to purge them came up with the same response.
I could have just sudo find -iname them and manually removed everything, then reinstalled them, but there were quite a few packages, and I dont know if there is some referencing file written by the system somewere or how to modify it.
Using aptitude came up with the solution of removing everything ubuntu and basically stripping back down to base debian.
 With lots and LOTS of messing around I manged to get the number of broken dependencies down to two (one was powernowd - or some such like, cant remember the other) but no amount of tinkering was helping. 
 It is difficult though to try and be accurate with my information now since I have already reinstalled ;(  but thanks for the try anyway.

---

