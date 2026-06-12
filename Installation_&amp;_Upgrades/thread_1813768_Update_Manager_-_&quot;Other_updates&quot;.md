---
title: "Update Manager - &quot;Other updates&quot;"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by jmarcedwards on 2011-07-28
I have added the xorg-edgers & gnome3-team-gnome3 PPA to my repository.  When I use the Update Manager, I am noticing that both of these PPAs are listed as "Other updates".  It doesn't appear that there are any specific updates listed below these PPAs in the Update Manager list.

My question is:

Does the Update Manager during the "Check" act as an apt-get and also will scan the PPA repository and update all of those PPAs as well? Or do I have to issue a separate "sudo apt-get update" to update my PPA repository?  Am I assuming correctly that "sudo apt-get update" will indeed scan all PPA repositories for updates?

Kind regards, Marc

---

### Post by tom4everitt on 2011-07-28
Hi, yes, PPA-updates do show up as "other updates" in the update manager (which is quite natural, since they are not really security updates for the core system, nor recommended by Canonical). 

The Check button in the update manager runs a command more or less equivalent to apt-get update, but it is not the same. So running apt-get update will not make the update manager go to rest, it will still prompt you to check for updates via the check button if you haven't done so in a while). 

And yes, apt-get update also scans the PPAs. apt-get update outputs a list of scanned archives when run, look for your PPAs there if you want to make sure.

---

### Post by jmarcedwards on 2011-07-28
Good feedback.  Thanks, Marc

---

