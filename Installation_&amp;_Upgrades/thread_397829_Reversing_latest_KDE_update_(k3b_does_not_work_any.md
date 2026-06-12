---
title: "Reversing latest KDE update (k3b does not work anymore)"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by Jonam on 2007-03-31
Yesterday, I downloaded and installed the latest KDE security update for Dapper and since rebooting my PC, k3b will not work and locks up in Uninterruptible state on launch both in Gnome and KDE.

I know that the latest KDE update changed kdelibs4c2 to kdelibs4c2a. Is there any way that I can reverse this update and go back to the previous kdelibs4c2 so that I can confirm that k3b failed because of this update?

Jonam

---

### Post by pradeepadapa on 2007-03-31
u can just uninstall this kdelibs4c2a from either synaptic manager or from adept manager

---

### Post by Jonam on 2007-04-02
Already tried this and Synaptic recommended removing the entire KDE system software and all. I just want to revert to the previous revision of kdelibs so that things work again.

[EDIT] Issue Resolved - fault was an intermittent hardware problem on the CDR drive on the same IDE bus as the DVD-RW drive. k3b would start but go into Uninterruptible state because of this hardware problem. Removal of faulty drive fixed k3b. Likely that hardware fault occurred at same time as update of kdelibs.

Jonam

---

