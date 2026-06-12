---
title: "Update firefox 3.0 to 3.0.1"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2008-07-18
hi all
how i can update firefox 3.0 to 3.0.1 on hardy...?
exist any repositories....???
i waiting your replays

---

### Post by firefeather on 2008-07-18
The update comes through update manager, so you can start update manager and click "Check for updates"

---

### Post by chanfle on 2008-07-18
ok 
but on this moment i don't have any update for firefox....

---

### Post by firefeather on 2008-07-18
Oh...yep, I realized my mistake. The update is in hardy proposed, not main. Here's how you get the proposed updates (more likely to be unstable, but more up-to-date) if that's what you want to do:

[LIST=1]
[*]Go to System -> Administration -> Software Sources
[*]Enter your password
[*]Switch to the Updates tab
[*]Click Pre-released updates (proposed)
[/LIST]

---

### Post by Ozdemon on 2008-07-18
> **firefeather said:**
> Oh...yep, I realized my mistake. The update is in hardy proposed, not main. Here's how you get the proposed updates (more likely to be unstable, but more up-to-date) if that's what you want to do:

[LIST=1]
[*]Go to System -> Administration -> Software Sources
[*]Enter your password
[*]Switch to the Updates tab
[*]Click Pre-released updates (proposed)
[/LIST]

Should I uncheck the pre-released updates after doing the Firefox update?  In other words, is leaving it as a source likely to lead to me installing buggy software?

Tks

---

### Post by firefeather on 2008-07-18
> **Ozdemon said:**
> Should I uncheck the pre-released updates after doing the Firefox update?  In other words, is leaving it as a source likely to lead to me installing buggy software?

Tks

You might want to see [this link]("https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security") on the community documentation; the main thing it says is

> This repository is recommend to ONLY interested in helping to test updates and provide feedback. Since they are in effect testing updates, there is a higher chance of defective updates in this repository.

Since Firefox 3.0.1 is a security update and is programmed by Mozilla intentionally not to break things, I would say it's safe to install Firefox from there. As for the rest of proposed, it's better to uncheck it afterward. It's still not *likely* to break your system, but it still could happen to some degree.

Hope this helps!

---

