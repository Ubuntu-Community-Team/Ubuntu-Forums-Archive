---
title: "hamsoft breaks upgrade from 6.06 to 6.10"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by umina on 2006-11-28
My first upgrade yesterday went flawlessly.  My second and third machines did not upgrade because of the package hamsoft which caused a conflict and generated an issue over /etc/X11R6/bin.  On one system I got a message that it could not delete this directory in the upgrade process because it was not empty.  Sure enough it wasn't, there was a link there, "hamsoft", which I deleted.  That system then proceeded to complete the upgrade.

The second system complained about a conflict with hamsoft over the directory /etc/X11R6/bin but I could not determine what the conflict was as this directory did not exist when I went to look at it.  It appears that it was a package conflict picked up during the analysis for the reinstall after the upgrade.

I used Synaptic Package Manager to remove hamsoft.  It did not work at first because it had quite a list of activities to accomplish but I was able to deselect all, then remove hamlib then restart Synaptic Package Manager and perform the pending activities.  Ultimately I followed the suggestion and used a terminal to run the remainder of the upgrade with the instructions provided.

If you have hamsoft on your system, remove it before upgrading!  Developers, whatever hamsoft actually does must be a bit unusual to the environment and it should be fixed or detected in the script.

I have a couple of years experience with Fedora and about a month with Ubuntu, so I was able to hack/manpage my way through the problem, but it was not easy.

Len Umina
El Dorado Hills, CA

---

