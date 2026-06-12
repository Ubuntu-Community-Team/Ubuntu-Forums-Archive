---
title: "Upgrade to 13.04: Nautilus &quot;Open with...&quot; no longer works with .avi"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2013-06-09
After upgrading to 13.04 and making the usual adjustments I am left with 2 problems. This is the first and my next post will be the second.

When I right click on a .avi file the usual menu opens and if I select the default viewer, "Open with VLC media player" , nothing happens. If I choose ""Open with"  and then select "SMPlayer" or "Movie Player", again nothing happens.

All movie players are installed and working and if I start up, for instance, VLC and then select the file it plays it perfectly.

---

### Post by mikodo on 2013-06-09
> **stepheny said:**
> After upgrading to 13.04 and making the usual adjustments I am left with 2 problems. This is the first and my next post will be the second.  When I right click on a .avi file the usual menu opens and if I select the default viewer, "Open with VLC media player" , nothing happens. If I choose ""Open with"  and then select "SMPlayer" or "Movie Player", again nothing happens.  All movie players are installed and working and if I start up, for instance, VLC and then select the file it plays it perfectly. I don't use Ubuntu but Xubuntu, but google shows this link . Might it be the answer:    [http://www.itworld.com/software/355979/set-vlc-default-video-player-ubuntu-1304](http://www.itworld.com/software/355979/set-vlc-default-video-player-ubuntu-1304)

---

### Post by stepheny on 2013-06-09
Thanks for the reply but the problem is not setting VLC as the default. The problem is that right clicking on a .avi file and selecting any player at all, nothing happens even though the players are all working perfectly.

---

### Post by stepheny on 2013-06-10
I fixed this by going to ~/.local/share/applications/ and right clicking on "VLC media player". The command had been corrupted by the upgrade, "-F 32" had been added to the command "optirun vlc U%". I removed that and everything is fine now.

How do I mark this thread as solved?

---

### Post by mikodo on 2013-06-11
[How do I mark this thread as solved?[/QUOTE]

[Try this method for marking a thread as solved.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Edit: I see you have it marked already! Blah............

;p

---

