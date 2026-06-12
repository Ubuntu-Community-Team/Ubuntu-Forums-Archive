---
title: "Old Medion pc with crashed HD."
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Ripvisitor on 2010-02-11
Hi
This is a first post.  I thought about posting it in the beginners section.  But I fear this is not a beginners question.

I have not used ubuntu yet ; but would like to install the latest 9.10 version on an old Medion pc => Windows (XP) crashed and I bought a new Samsung HD to replace the old one.
I found that most of the install "How To's" speak of using Windows to start a cd to install UBUNTU. ;)
But what can i do to install this latest version on a "free" HD?  Nothing installed. Is it possible ? Or not ?
 ](*,)

Thxs Regards.
Luc R

---

### Post by rogueleader12345 on 2010-02-11
Download a CD, put it in your computer, and restart. Should default to boot from CD, but if not go into your BIOS and change the boot order settings. You'll get the Live CD menu and you can hit Install Ubuntu from there or start Ubuntu up and do it from there.

---

### Post by Ripvisitor on 2010-02-11
> **rogueleader12345 said:**
> Download a CD, put it in your computer, and restart. Should default to boot from CD, but if not go into your BIOS and change the boot order settings. You'll get the Live CD menu and you can hit Install Ubuntu from there or start Ubuntu up and do it from there.

So I download an ISO .. ubuntu-9.10-desktop-i386. I copy the iso to the hd ?  Or do I burn it to the hd ?  Then i install the hardrive in the pc AND restart the pc ?
Maybe burn the cd on a different pc .. use the cd in the pc where I have installed the empty HD.  Can i access the bios on a pc with an empty hd ?

:confused:

---

### Post by Mark Phelps on 2010-02-11
You burn the ISO image file to a CD.  You need a CD burner and a burning app to do that.

Also, you should then boot from that CD and try out Ubuntu -- PRIOR to installing it.  That will give you a good feel for how well  Ubuntu detects your hardware and installs the proper drivers.

Anything that does not work in LiveCD mode is going to range from trivial to impossible to fix after installation.

---

### Post by Ripvisitor on 2010-02-12
> **Mark Phelps said:**
> You burn the ISO image file to a CD. You need a CD burner and a burning app to do that.
 
Also, you should then boot from that CD and try out Ubuntu -- PRIOR to installing it. That will give you a good feel for how well Ubuntu detects your hardware and installs the proper drivers.
 
Anything that does not work in LiveCD mode is going to range from trivial to impossible to fix after installation.
 
 
Ok burning this iso to cd is clear .
Then I start the old pc with the new HD on board .. (EMPTY) .. with the cd in the cd drive . Will it be possible to get the cd on board without an OS on the HD ?
 
 
*"Also, you should then boot from that CD and try out Ubuntu -- PRIOR to installing it. That will give you a good feel for how well Ubuntu detects your hardware and installs the proper drivers."* 
So if i introduce the cd in my cd player connected to the portable .. I can work on Ubuntu without installing it on the portable ?
 
Regards
 
Like this .. dicover the world of ubuntu.

---

### Post by Mark Phelps on 2010-02-12
I'm presuming your PC has the ability to boot from a CD.  If that's true, you generally go into the BIOS and change the boot device sequence to have your CD/DVD drive at the top of the list.  Then, when your machine boots (with the CD in the drive) you may get a line of text that says something like "press any key to boot from CD".  If you see that line, press any key on the keyboard.  The machine will boot from the CD.  Eventually, you will get a list of selections.  Choose the first one (try without installing -- or something like that), and eventually, you should be presented with an Ubuntu desktop.

If your machine can not boot from CD, an alternative is to boot from USB -- but the latter is mostly true on very recent machines, and in your case, I would doubt the option is there.

---

