---
title: "[SOLVED] unable to go past documents and settings screen"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by RogueClown on 2008-04-11
i am installing Ubuntu for the first time...in fact, installing Linux for the first time.  this is all new to me.

i'm installing 8.04 through Wubi.  i burned the CD image, installed it, and rebooted into Ubuntu.  it went through all the checking and loading splash screens, and then got to the screen where it asked which of my documents and settings from Windows i wanted to import into Ubuntu.  i could click "cancel"...but the "forward" button was greyed out.  i clicked on settings to import, and it was still greyed out.  i cancelled and tried again, booted again in Ubuntu...and the same thing happened.

how can i rectify this?

thank you for your help...if you need any more info to tell me something helpful, i'll tell you whatever else i can, just ask.

---

### Post by Partyboi2 on 2008-04-12
This was on the wubi wiki page.
> During installation sometimes you may get stacked seeing a migration assistant page with the forward button disabled ([[IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] https://bugs.launchpad.net/wubi/+bug/195905]("https://bugs.launchpad.net/wubi/+bug/195905")). In this case press cancel, at the desktop open a terminal (Applications > Accessories > Terminal) and run 
  ubiquity --automatic

---

