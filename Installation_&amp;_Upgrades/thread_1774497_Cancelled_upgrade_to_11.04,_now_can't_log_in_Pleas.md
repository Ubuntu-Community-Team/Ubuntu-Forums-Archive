---
title: "Cancelled upgrade to 11.04, now can't log in? Please help!"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by Anarchis on 2011-06-03
When upgrading to 11.04 this morning through the update manager, I waited for the new packages to download, and when it came to the "installing packages" window, there was no cancel button so I forced quit since I thought I'd come back home and finish up the installation (it said 4 hours left). 

Now when I restart my laptop, the login window freezes my mouse, and there is no username/password option, just my username?

Is there a way to restore system to a previous time or login in safe mode? Please help! 

:(

---

### Post by lykwydchykyn on 2011-06-03
Not really, but if it already was starting to install packages, try this:

 - Select "recovery mode" from the boot menu
 - Select "Root shell" from the text menu that comes up
 - issue this command at the shell:
 ```

dpkg --configure -a

```

That should pick up the installation procedure where it left off.

---

