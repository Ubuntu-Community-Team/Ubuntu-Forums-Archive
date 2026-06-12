---
title: "Xubuntu upgrade crashed"
date: 2024-06-15
forum: Installation &amp; Upgrades
---

### Post by peyre on 2024-06-15
Ok, I took a chance this morning and forced an upgrade to 24.04 (from 22.04), using **sudo do-release-upgrade -d**.  I'd done that on my two laptops already, because reinstalling those from scratch would be no big deal if it all tanked.  I was going to hold off on my desktop, since that would be a hassle to redo from scratch.  However, with a change to the source for a project I'm involved in ([https://github.com/raceintospace/raceintospace/discussions/856#discussioncomment-9782712](https://github.com/raceintospace/raceintospace/discussions/856#discussioncomment-9782712)), I needed cmake 3.25 but only had 3.22.1 and 3.25 isn't available for the old LTS...so I decided to bite the bullet and do the upgrade.

Everything ran fine, but at one point it just crashed.  No error message or anything that I saw; just suddenly my terminal windows closed.  Now I have the 24.04 look to the Desktop and **lsb_release -r** returns 24.04 and I can't use **sudo do-release-upgrade -d** to resume the upgrade.  I still have Software instead of the Snap Store, and it looks like Wine is broken, don't know what else.

Fortunately I used Clonezilla to create an image of my hard drive recently, so I *can* revert to how the machine was a few weeks ago, but that'll take a while, so I thought I'd ask if anyone had any suggestions to repair this system, some way to resume the upgrade, or whatever.

---

### Post by peyre on 2024-06-15
Well, I reverted it and then the upgrade ran successfully.  So to anyone considering doing the forced upgrade, be sure to image your hard drive with Clonezilla or something first!

---

