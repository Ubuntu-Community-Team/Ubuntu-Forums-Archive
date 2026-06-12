---
title: "lucid reinstall on dual system - no printer (hp p1006), no sound"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by emmvie on 2010-09-05
I have a dual boot (win/linux), where I had totally bolluxed up the linux, so i bought the dvd and reinstalled over the old linux on the same partition. Current version is now **Lucid Lynx (10.04)**.

**What doesn't work** is my printer (hp p1006), which seems to be a common problem but nowhere in the forums do I find a solution. I've purged and reinstalled hpijs and hplib and cups and run hp-setup as root, but still it tells me i need a "binary driver plug-in" (which is what???). 

what i did:  [http://georgia.ubuntuforums.org/showthread.php?t=1523646&highlight=hp+p1006](http://georgia.ubuntuforums.org/showthread.php?t=1523646&highlight=hp+p1006)

same problem as i have, also **unresolved**:  [http://old.nabble.com/Re%3A-help-related-to-hp-plugin-3.02-in-Ubuntu-10.04-p29214854.html](http://old.nabble.com/Re%3A-help-related-to-hp-plugin-3.02-in-Ubuntu-10.04-p29214854.html)

**Plus, I have no audio anymore**. Any ideas? Also a typical 10.04 problem?

Thx for any advice!!
emmvie

---

### Post by emmvie on 2010-09-06
Apparent solution: run this from hp support:
[http://puzzle.dl.sourceforge.net/project/hplip/hplip/3.10.6/hplip-3.10.6.run](http://puzzle.dl.sourceforge.net/project/hplip/hplip/3.10.6/hplip-3.10.6.run)
$ sh ~/hplip-3.10.6.run
It still throws the same error message but whatever, it works now.

Audio solved by simply (!) opening mixer and raising PCM level from zero to max.

---

