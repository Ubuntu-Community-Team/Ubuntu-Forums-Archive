---
title: "Upgraded Gutsy to 8.04.1 - and lirc won't update"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by kcox5342 on 2008-10-28
I installed the update via the alternate 8.04.1 CD on my 32-bit laptop, with the internet updates turned on.  Then I rebooted and included the medibuntu repo, which got another 96MB of updates.  All went well except for lirc, which won't update.  It says:

>> E: /var/cache/apt/archives/lirc_0.8.3~pre1-0ubuntu7.1_i386.deb: subprocess new post-removal script killed by signal (Segmentation fault)<<

It never goes away from the update manager.  While I use my laptop as a mythtv frontend, I do not have any remote control used with it - hence I don't even *need* lirc, except I can't remove it using Synaptic without removing mythbuntu-control-center and two other essential-looking things.

I'd like to upgrade lirc, mainly to get it off my upgrade manager list.

Edit:  Huh.  Last night it did this, this morning an update ran and it worked.  Now I'd just like to know why weather.niu.edu crashes both Firefox and Epiphany.

---

