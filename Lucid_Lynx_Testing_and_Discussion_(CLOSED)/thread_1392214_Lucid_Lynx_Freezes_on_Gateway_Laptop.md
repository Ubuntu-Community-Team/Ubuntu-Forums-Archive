---
title: "Lucid Lynx Freezes on Gateway Laptop"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ScentOfUnderstanding on 2010-01-27
I just installed Lucid Lynx on my laptop yesterday.  I have used Ubuntu a little before (Hardy Heron) but am switching due to the expiration of my Windows 7 RC install (and the low value/old age of my computer).

After installing Lucid Lynx, it seemed to freeze up periodically.  It happened probably 6 or 8 times over the course of a day.

I haven't located a for sure cause, but thought I would share my experiences.

Freezing occurred while using FireFox (alone), while using Google Chrome (alone) and also while using either of these browsers simultaneous with RhythmBox music player.

I tried installing Opera.  This seemed to help, but still froze occasionally while playing music in RhythmBox.

I then tried installing Banshee to play music.  The computer hasn't frozen since (fingers crossed) while using Banshee and Opera.

I'd rather use Chrome, but I guess I'll hold out a while and see if maybe there are updates that stabilize things.

Any advice or comments are welcome.

FYI -- I'm using a Gateway laptop, Pentium 4 @ 2.8Ghz, 1GB RAM

---

### Post by utnubuuser on 2010-01-27
I'm having a similar problem on my desktop.  Using Karmic, it was ok since October, but since the new year it is freezing up occasionally. every two hours of so.  no apparent cause.  likewise tried different browser, different photo app, all to little or no avail.  removed gnome-screensaver and that cured it for a day, but now it's back to same old same old.

Tried reinstalling too. Only thing I haven't tried is sudo dpkg-configure -a.

---

### Post by ScentOfUnderstanding on 2010-01-28
As a follow-up, my computer eventually did freeze again.

I was only running Opera and Empathy, no music player.  I had been using it for a couple of hours without issue, left it sit for 20 minutes or so, and it froze.

---

### Post by AlexZaim on 2010-01-28
[http://ubuntuforums.org/showthread.php?t=1390402]("http://ubuntuforums.org/showthread.php?t=1390402")

download wicd and uninstall network-manager

---

### Post by ScentOfUnderstanding on 2010-01-28
Thanks, Alex -- I did what you said and am trying it out.

> **AlexZaim said:**
> [http://ubuntuforums.org/showthread.php?t=1390402]("http://ubuntuforums.org/showthread.php?t=1390402")

download wicd and uninstall network-manager

I was away from the computer for a while after uninstalling network-manager and installing Wicd, and it looks like it did freeze -- but maybe it needed a chance to restart (?) before the changes would take effect.

So far, it looks like Wicd has some trouble connecting to my wireless network.  It finds the network just fine, but can't get an IP address when attempting to connect.

---

### Post by ScentOfUnderstanding on 2010-01-28
Further follow-up...

I used my computer for a few hours with Opera, Empathy and RhythmBox after installing Wicd and uninstalling network-connection.

It didn't freeze.

I then switched back to using Google Chrome.  It continued working fine for a while.

The computer then froze when watching a full screen video (not YouTube, but something similar)(not pr0n) in Google Chrome.

I restarted and it once again froze while browsing a non-video site in Google Chrome.  (Both times with Opera open in the background.)

I'm going to try using just Opera for a while to see if Chrome perhaps is a part of the problem.

---

### Post by ScentOfUnderstanding on 2010-03-04
Well, I took some time off from Ubuntu to switch back to Windows, but my Win7 RC finally started bi-hourly shutdowns -- so the time for Ubuntu has come.

Unfortunately, I am still suffering from periodic freezes.  I have tried running Update Manager to get the most recent stuff, though I'm not sure if that's really likely to help.

I'm an Ubuntu n00b, so if anyone can help figure out how to troubleshoot freezes, it would be much appreciated.

Is there a 'first thing to check' when a crash occurs?

---

