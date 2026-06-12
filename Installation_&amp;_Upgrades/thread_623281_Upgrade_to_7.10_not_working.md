---
title: "Upgrade to 7.10 not working"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by monkey5672 on 2007-11-25
Upgrade to 7.10 (Gusty) from 7.04 not working. I'll post my error message below. I'm using the upgrade manager, maybe I should burn a DVD and try from that? 

-monkey5672

---

### Post by funkyFlash on 2007-11-26
You seem like you're doing it right, I'd hate to burn a DVD when not necessary.  That error is indicative of something else trying to update/install packages at the same time.  From your open windows, it seems that it's not the case.  Does it give this error after it thinks really hard for about an hour or so, or does it pop this up right away?

I'd be curious to see the outcome of the old-skool way, and do a "sudo apt-get dist-upgrade" from the command line.  That way, you'll have a better idea of what's going on, without pretty pretty smoke and mirrors.  And, if something goes wrong, it will say "HAY, THIS IS BROKE.  RUN THIS COMMAND TO FIX IT"  That's how I got through a couple broken Kubuntu upgrades.

Make sure there's nothing else running, especially things like the update manager, synaptic, and add/remove..., and try the apt-get approach.  If nothing else, it will tell you there's something wrong before wasting an hour of your time.

---

