---
title: "Install fails again and again and again..."
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by Stan Houswell on 2005-11-22
Hello,
       Our second computer is having a hard time loading ubuntu. It recently crashed in windows XP pro and we have been struggling to get it restarted with any operating system at all. So far, ubuntu has gotten the furthest, although it stopped at a certain line that says "checking if image is initramfs..." and the cd stopped reading. It has frozen, like this, on every single version of windows OR linux we try it on... Only on some it gets to the page of diagnostics before going blank, writing "uncompressing linux" and the cd once again  stops working. We are not using the latest version of ubuntu we have the version that came in april 2005 pc authority. The computer has a 200gb harddrive, 512 mgs ram, celeron 2.4ghs processor and a pretty sweet video card. During it's life, it was a constant pary-goer and has caught about every virus that ever crossed a LAN cable. If this sounds like anything you know of, please let us know... For the sake of my 'KOTOR' save...
Peace out,
Stan

---

### Post by yesplease on 2005-11-22
Sounds like a hardware problem. The computer is worth rescueing though.

It doesnt matter if you use hoary. The windows virusses wont be a problem. I suppose you have formatted the disk anyway.

Before chasing for hardware problems: how did you format the disk and where is ubuntu installed? If you have the live cd, you can check the partitions with gparted. That would also rule some things out.

If you are convinced that this is a hardware problem, the first thing I would try is to test the hard disk in the other computer.

---

### Post by Bartender on 2005-11-22
Hi, Stan -
I'm just thinking out loud here - not an expert but maybe if we put our heads together...
You mention the install crashing at a certain point - is it always at the same spot?  If so, I'd be looking at getting another CD.  
Or does it seem to crap out on you after roughly ten or fifteen minutes, enuf time for the parts to warm up?  I just found out about the plague of bad capacitors that got installed on many motherboards a coupla years ago.  Saw one of these in person, with the crud coming out of the capacitors, and MaximumPC's latest issue talks about the bad caps problem twice.  Google "bad capacitors" to see what I mean.
From what I've read, failing PSU's will often establish a pattern of working for a short period until they're all warmed up (or until they're working a little harder, like when the hard drive and cd drive are both spinning hard and the CPU is working - like during an install?).  Can you swap PSU's and try again?
While on that thought, swapping the cd drive for a known good unit might be worthwhile too...

---

### Post by dcstar on 2005-11-22
[QUOTE=yesplease]Sounds like a hardware problem. The computer is worth rescueing though.
.......[/QUOTE]
If you have two RAM modules, take one out and try again (then test the other one....).

If you have one RAM module, borrow another to replace it with (for a test).

You may also want to try resetting the BIOS to "Safe" defaults.

---

