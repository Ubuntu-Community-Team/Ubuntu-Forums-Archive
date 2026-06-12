---
title: "Something causing Nautilus to open 3 or 4 windows per second"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GavinZac on 2009-03-03
I don't know what's going on, but there are dozens of nautilus windows trying to open. XORG is showing the most CPU usage, while each individual nautilus window is too short lived to show up in the system monitor for very long.

Attached is a screen shot, the many windows are on the top panel. Nothing I kill in system monitor seems to stop them, and a reboot just makes them start again when i log back in. Logging into a different account, everything is normal.

---

### Post by tnat on 2009-03-04
Have you advised nautilus per gconf not to show the Desktop?

I had the same problem, which was solved by enabling this again.

/desktop/gnome/background draw_background

---

### Post by Nullack on 2009-03-04
Is this happening by default? I cant replicate it. Please consider a bug report if its happening by default for you, and you havent messed with the build.

---

### Post by nyarnon on 2009-03-04
On top of this page there is an option search this forum. If you would have clicked on that and had entered nautilus as search term, you would have encountered :

[http://ubuntuforums.org/showthread.php?t=1061458&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=1061458&highlight=nautilus) 

Where a solution was left for anyone having this problem.

Hope it works for you. If not please comment in that thread.

Could one of the moderators please close this thread?

---

### Post by Nullack on 2009-03-04
From the other thread it seems its this bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325973](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325973)

GavinZac you can subscribe yourself to the bug to be updated on its progress, and change the bug doesnt effect me field to it does effect you.

---

### Post by GavinZac on 2009-03-04
> **nyarnon said:**
> On top of this page there is an option search this forum. If you would have clicked on that and had entered nautilus as search term, you would have encountered :

[http://ubuntuforums.org/showthread.php?t=1061458&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=1061458&highlight=nautilus) 

Where a solution was left for anyone having this problem.

Hope it works for you. If not please comment in that thread.

Could one of the moderators please close this thread?

Ah, apologies. The 'threads similar to this' didn't bring back any results as I making the new thread and I relied upon that.

As I was a biy desperate last night, I 'solved' the problem by removing Gnome's config files so that I booted back into a default config. Do you think I should implement those steps now so it doesn't happen again, or leave it alone and let the devs fix it?

---

