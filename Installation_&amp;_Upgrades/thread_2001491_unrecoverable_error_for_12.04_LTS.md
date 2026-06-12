---
title: "unrecoverable error for 12.04 LTS"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2012-06-11
Have tried to install Ubuntu 12.04 LTS with a CD and DVD, and I end up with the same problem.  Unrecoverable error.  This happens after I enter my name and password.  They provide a desktop so I can locate the error, but I have no clue what I am looking for.  Anyone have a clue?  BTW, the computer I am using is not the one shown in my signature.

---

### Post by wilee-nilee on 2012-06-11
> **gilloz said:**
> Have tried to install Ubuntu 12.04 LTS with a CD and DVD, and I end up with the same problem.  Unrecoverable error.  This happens after I enter my name and password.  They provide a desktop so I can locate the error, but I have no clue what I am looking for.  Anyone have a clue?  BTW, the computer I am using is not the one shown in my signature.

Can you provide the actual error?

Can you explain the exact install method used?

---

### Post by gilloz on 2012-06-11
This is what the error windows says:

The installer encountered an unrecoverable error.  A desktop session will now be run so that you may investigate the problem or try installing it again.

I honestly do not know where or what I am suppose to look for.  My method of installation has been using a CD and a DVD.  No Go.  Tried manual partitioning and let the program load itself, still no go.  Opened a terminal in live session and typed  sudo apt-get remove ubiquity-sideshow-ubuntu, which I read on another thread and that did not work.  Don't know where else to look.

---

### Post by gilloz on 2012-06-11
After 124, so far, lookieloos, I guess no one has any answers.  I'll forget about 12.04 and go back to 10.04.  It has installed without a hitch and is running.  I guess no one wants to admit that 12.04 is buggie.  Shouldn't have to experience this hassle installing the program.  Thanks to those that looked in.  Thanks Wilee-Nilee for your response.

---

### Post by gilloz on 2012-06-13
OK.  Finally solved my problem.  I had to download, burn and install the Alternative CD for 12.04 LTS.  It installed without a hiccup.  Downloaded all updates and I am now configuring my Thunderbird and Firefox.  Thanks wilee-nilee for your response.  I appreciate that.  BTW, the computer I was trying and finally installed 12.04 was my old Soyo SYK7V Dragon Plus mobo with an AMD Athlon XP1900, 1 GB PC-2100 DDR DIMM, eVGA FX-5500 AGP video card and a WD 80GB HDD.

---

### Post by milhous on 2012-08-01
Sounds promising, having similar install troubles on an Athlon 1900, nForce2 system. Will try the alternate iso and report back.

For some backstory, I couldn't zero the disk from the installer CD without encountering an error. I also couldn't zero the disk with DBAN without an error. Ran vendor diagnostics on the disc without error. Finally took the disc out, place it into an enclosure and successfully zero'd it with my Mac. Am concerned there may be a physical problem. Memtest was also clean.

Update: Alternative ISO installed flawlessly. Thanks to all!

---

### Post by doccpu on 2012-08-09
same deal unrecoverable error after fresh install or live cd from desktop install. argh trying the sudo apt-get remove ubiquity-slideshow-ubuntu   then go back to desktop and run install. we will see. 
on a 933mhz with 512mb ram. ubuntu is too big and slow these days. live cd takes 20 mins to boot on a 200mhz 384mb machine and 15 min on this one with a 1gb swap. sigh wish folks would write new code on an old machine so it will work on what people have.
where are the alt cd's?
[email]dhorner@usa.net[/email]

---

