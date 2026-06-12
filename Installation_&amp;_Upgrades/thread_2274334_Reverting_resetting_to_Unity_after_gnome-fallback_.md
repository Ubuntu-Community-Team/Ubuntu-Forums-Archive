---
title: "Reverting resetting to Unity after gnome-fallback gnome-flashback"
date: 2015-04-19
forum: Installation &amp; Upgrades
---

### Post by sefs on 2015-04-19
This post is just to share my experience in reverting/resetting to Unity after gnome-flashback, gnome-fallback.  I had just upgraded to 14.04 and wanted to try unity at this point in time.  

I tried every reset / revert command on the internet but no matter what I did, when I logged into my account I was greeted with just my desktop wallpaper.  I downloaded all tweak tools deleted all gnome directories but nothing work.

I cannot remember what led me to ~/.config/autostart but there it was I stared my nemesis eyeball to eyeball and mano y mano.  This was a Mexican standoff, and I was not reinstalling from scratch or backing down. 

There he was.... metacity.desktop in my autostart directory.  I did a "cat metacity.desktop" and it was running/autostarting the command "metacity --replace".  So each time I logged in it was replacing unity with a metacity desktop (the blank desktop I was getting) I disabled it (later deleted it).  logged out and logged back in and Unity loaded without issue.

---

