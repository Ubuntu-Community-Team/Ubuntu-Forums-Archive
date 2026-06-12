---
title: "How Can I Upgrade From 11.10 back to 10.04 LTS?"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by brolin_1911a1 on 2012-11-07
I recently "upgraded" 2002 IBM eMachine from v11.04 to 11.10 because 04 had reached the end of its support life.  Unfortunately, the "upgrade" removed drivers for the Intel graphics chipset on my machine's motherboard.  It still works -- sort of.  Text, fonts, and colors in Thunderbird seem to change and intermingle at random, displays in Firefox sometimes overlap, and what used to be contrasting displays and highlights are now invisible.

How can I use apt-get, dpkg, Synaptic, or even Software Manager to upgrade back to a earlier version of Ubuntu that actually worked on my machine without risking my personal data?  :(

---

### Post by arpanaut on 2012-11-07
Back up your personal data, and re-install the release that worked for you.
There is not a downgrade path with Ubuntu.

FYI 10.04 is only supported until April of 2013.
You might want to consider Xubuntu or Lubuntu for a machine of that age.
Good Luck.

---

### Post by Dn4mycrownj on 2012-11-07
I don't believe you can role back an OS. You may end up backing up your personal files and do a clean install.  Or there are plenty of resources on here to install the driveers you need. Always remember that others have prob had the same problem and have found a work around.  Usually google is a wonderful place to find info like that

---

### Post by Frogs Hair on 2012-11-07
Downgrades are not possible , but you could check additional drivers to see if there are drivers available. Both 10.04 and 11.10 reach end of life in April so you may want to backup and preform a clean installation of 12.04.

Lubutu and Xubuntu are the best choices for older hardware and gnome-session-fallback is available in Ubuntu if your machine doesn't support Uinty.

---

### Post by brolin_1911a1 on 2012-11-07
> **Frogs Hair said:**
> Downgrades are not possible , but you could check additional drivers to see if there are drivers available. Both 10.04 and 11.10 reach end of life in April so you may want to backup and preform a clean installation of 12.04.

I know but that's at least roughly another six months of my machine actually working instead of limping along as it's doing with Obstreporous Oscelot.  I actually thought since I was doing the online upgrade any drivers available would have been downloaded as part of the process.  Instead, after getting waaaayyyy too far into the process to change my mind, the upgrade manager notified me that my computer's Intel chipset was not supported; did I wish to continue?  What could I say?  No, and leave it with an OS half installed?

> **Frogs Hair said:**
> Lubutu and Xubuntu are the best choices for older hardware and gnome-session-fallback is available in Ubuntu if your machine doesn't support Uinty.

I'm currently using the gnome-session-fallback.  It's the only thing that kept the machine useable.  But... it has "issues," i.e., the sort of problems mentioned in my first post.

Not having a spare, unused terabyte drive lying around, blithely saying, "back up your data and reinstall" doesn't come across as practical, not unless a reinstall stands a very good chance of not wiping personal data in the first place.  And, I admit, I'm still enough of a neophyte that I don't know how to install one Linx version in place of another safely.  Can it be done?  If so, how (in very small baby steps?)

---

