---
title: "Fed up with Bill Gates, but shiny new 6.10 CD wont boot (X Failure)"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by dave3000 on 2007-04-09
Ok, I finally got fed up with Microsoft.  The last straw was another “Genuine Advantage” update.  I already knew I didn’t like it, but when I Googled it I found that they collect all kinds of info on my PC and check in with Redmond every day.  That’s it, I have to install Linux (dual boot since unfortunately I’ll still have to start Windows occasionally… maybe I’ll firewall Big Brother Microsoft).  

Anyway, so, I downloaded Ubuntu-6.10-desktop-i386.iso.  Used ISO Image Recorder to burn a CD.  CD integrity check finds zero errors.  Comes up to the initial menu fine, but when I choose to “Start or install Ubuntu” OR “Start Ubuntu in safe graphics mode”, I eventually get the following:

“Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?  <yes> <no>”

The last few lines of the X output say:

“(WW) I810:  No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
No screens found”

Doesn't appear to be anything I can do at that point.  Can't get to a shell, nothing.
As I said, I get this even if I boot using the “safe graphics mode” option.  

This is on a Toshiba M65-S8091 laptop (1.73 GHz Centrino, 1.5G RAM, Intel Integrated Graphics).

Oh, I should probably also mention this message sequence that occurs prior to the X failure:

* Activating swap...   [ok]
mount:  Function not implemented
* Checking file systems...
fsck 1.39 (29-May-2006)  [ok]

(not sure if mount is trying to tell me something there.)

Any help appreciated.

-Dave

---

### Post by Rui Pais on 2007-04-09
Hi,
somewhere on boot screen you have an option to boot on vga mode (use to be by F4 key...)
Give it a try to see if it work.

If you get a boot command and it still fails after you plain press enter, try to pass "vga=791" before pressing enter.

hth

---

### Post by dave3000 on 2007-04-09
Rui,

Thanks.  I tried modifying the boot parameters via F6 and adding vga=791.  Same result.

I did find that if I delete the "splash --" part of the boot line, then I can get to a shell.

I have a feeling my problem may be related to the "915resolution" Intel Video BIOS hack:

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

I suspect this because I get the "No Video BIOS modes for chosen depth" message.

-Dave

---

### Post by holz on 2007-04-09
Could you elaborate? are you on a laptop? your video card? we need more info. As a first step I would download the alternate install cd and have it ready so you can install in text mode.
Bear in mind, I am a nu bee, and just completed an install having the same problem as you on a Toshiba satellite, so my answers are a beginner level.

---

