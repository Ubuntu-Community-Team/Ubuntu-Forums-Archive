---
title: "ubuntu freezes during upgrade - refuses to upgrade"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by SlickTheNick on 2007-05-28
I upgraded up to edgy this morning, and just a litle bit ago was in the process of upgrading to fiesty...then ubuntu decided to freeze (was browsing the web while waiting for it to upgrade, i think that may have been the culprit). After waiting a little while with it still being frozen, I was forced to turn the computer off. I booted up ubuntu again only to have it tell me there is over 600 updates available, and that i need to do a distro upgrade for some of them. I try the upgrade and..

"A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport"

So my question is....how can I fix this and restart the upgrade?

Also, it now says that I am back in the original distro i installed (the one before edgy...breezy right?) even though I just upgraded from that this morning

---

### Post by DougieFresh4U on 2007-05-28
Try in terminal; **sudo apt-get update** then  **sudo apt-get -f install** then **sudo dpkg --configure -a**
And please just let it work, surf the web later:p

---

### Post by mmlnewbie on 2007-05-29
For me the upgrade from Edgy to Feisty failed miserably with fatal errors. I had to back out and do a fresh re-install. Fortunately I had /home on a dedicated partition and a complete backup of /etc - this helps a lot.

---

### Post by DougieFresh4U on 2007-05-29
> **mmlnewbie said:**
> For me the upgrade from Edgy to Feisty failed miserably with fatal errors. I had to back out and do a fresh re-install. Fortunately I had /home on a dedicated partition and a complete backup of /etc - this helps a lot.

Sorry to hear of your trauma :(
Did you manage to get Feisty installed? What was the failure?

---

