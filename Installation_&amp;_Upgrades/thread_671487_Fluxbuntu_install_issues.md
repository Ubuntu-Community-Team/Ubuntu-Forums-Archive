---
title: "Fluxbuntu install issues"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by MonsterTrimble on 2008-01-18
Hey;

This is the deal. I have a PIII (550 Mhz, 256 MB RAM) that recently was running as my windows-based file & print server. Now (due to a change in printers) I intend to make this into a linux torrent & file server. I tried installing Fluxbuntu a couple times and it would start installing no problem, but it would crash at having 66% of the base system installed. I tried this a couple times with different formatting configs (I have three HDs that I want to set up with LVM from the get-go) and the same result happened every time. I also tried Xubuntu 6.10 & Ubuntu Alternate 6.10 (They were what i had on hand) and after selecting start (Xubuntu)/Text Install (Alternate) the entire system froze solid.

Am i missing something?

---

### Post by Craigus on 2008-01-18
Eliminate hardware problems first - do the memory test from one of the live cd's (you should also of course do the cd check to make sure that the cd is being read correctly in this drive).

Get ultimate boot cd:

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

and run the appropriate manufacturer's HD test utility to test the HD's.

---

### Post by MonsterTrimble on 2008-01-21
Hey! Got it solved. It was something extremely stupid on my part. I forgot that the *buntu installer only partions what is free instead of copying over the original OS. Whoops! My system didn't like LVM though, but I can get that sorted out later.

Thanks!

---

