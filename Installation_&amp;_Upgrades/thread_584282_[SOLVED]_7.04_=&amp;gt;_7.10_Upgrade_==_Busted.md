---
title: "[SOLVED] 7.04 =&amp;gt; 7.10 Upgrade == Busted"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by hunkybill on 2007-10-20
I used the update-manager upgrade option on a workstation to try and move from 7.04 to 7.10. My 7.04 was tricked out with Compiz-Fusion, AWN, Screenlets and not much else of any consequence. 

I had some trouble with repositories on upgrade, so I unchecked all my 3rd party repos for 7.04, and tried upgrade again. Second time around it went pretty well. After 20 hours or so, I had the system upgrade and rebooted. 

7.10 gets to the point where it loads what looks like OpenBSD SSH daemon (It's hard to tell the exact process) before the video kicks out, and she's a dead dead dead system. NO way it's gonna boot. 

So, what's the secret to fixing this scenario of an upgrade gone bad. I can boot with a LiveCD and see all my partitions and data. I checked out my xorg.conf and it appears fine.   dmesg shows no errors.

Anyone have any advice? I am now 99% sure I will never upgrade my other perfectly working 7.04 install on my laptop as it looks like the Upgrade process sucks bag to me.. 

Is there a way to use the Live CD to try and install over an existing install while keeping the existing partitions? If so, then maybe I can just re-upgrade??? 

Thanks!!

---

### Post by kindloaf on 2007-10-20
I experienced a similar thing.  I tried to update from 7.04 to 7.10.  The upgrade manager downloaded some packages and installed some packages, suddenly the upgrade manager disappeared and I was never able to open it again(when I clicked administration->upgrade manager, nothing happened).  The other parts of the system were normal though.

After I rebooted the machine, the login window popped up and I entered the username&password.  Then the system shows a blue screen(the whole screen is lightblue), and it's *DEAD*!!  The only thing on the screen was the cursor which I could move.

It's not totally dead though.  When the system is on lightblue screen, it responded to the power button.   After I pressed the button for 1 second, some command lines was printed to the screen saying "...catching shut down signal ..." and the machine was shut down.  Also if I didn't touch the keyboard & mouse after about 5 minutes it went to the "black-screen" screen saver.

Feeling frustrated!

---

### Post by Guises on 2007-10-21
I've had basically the same experience as kindloaf, with the grey/light blue screen. The curser moves and I can get an error box when I type ctrl-shift-x (the shortcut that I had defined for popping up a terminal).

I can get a command line when I boot in recovery mode, but I don't know what to do with it.

One more thing - when I rebooted after the upgrade I had a filesystem error. I did the fsck thing as normal and it fixed everything, as normal. However - there appeared to be a whole lot more problems this time than there is most of the time. Going through the fsck process took a while.

---

### Post by hunkybill on 2007-10-21
Hi,

I downloaded Gutsy for a LiveCD. I booted it. I navigated to my old /etc/X11 and used one of my older xorg.conf files and then rebooted. My system came up. All sorts of older themes and Compiz problems remain. I had a heck of a time getting Compiz working, had to remove it completely and re-install.

Now, I have my Avant Window Navigator and Compiz running on GUTSY...

IT IS MUCH MUCH MUCH SLOWER.. which leads me to believe I now have some work ahead of me trying to figure out what is truly wrong with my Video driver.

Of course.. this is probably all due to the fact that I have an ATI Radeon card, albeit an older one that I think the Open Source ATI drivers can handle (9200).. so I am hoping that after some fiddling there.. my system will be 7.10 and FASTER..


All in all.. I still give the UPGRADE process a big fat 2/10.. nice try, but the whole process obviously needs more TLC for those cases where we strayed from a default 7.04 install...

---

### Post by kindloaf on 2007-10-21
Yeah I agree that updating is quite slow and unstable.

I finally gave up and installed 7.10 from scratch.  It went smooth and took about 1 hour.

By the way, I am quite impressed by the font rendering of the new system.  Now the pages in the browser(firefox) are much much better than they were!  And much better than what I saw from other distributions.

---

