---
title: "Conflicting/Missing Post-Upgrade Information"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by mjukr on 2005-04-11
In upgrading from Warty to Hoary, I'm unable to get suspend-to-disk to work. I found two sets of information on post-upgrade tweaks required to get things settled.

The first one directs changes to mkinitrd.conf:
[http://www.ubuntulinux.org/support/ReleaseNotes504/](http://www.ubuntulinux.org/support/ReleaseNotes504/)

The other directs changes to menu.lst:
[http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM)

Both have been recently updated, yet the info contained therein appears out of sync. Are both changes necessary to enable hibernate? 

I might also suggest adding a note to run `dpkg-reconfigure fontconfig` for those with mutilated fonts after upgrading to Hoary. I had a simple install of Warty with no backports or 3rd-party utils, and the font issue was the only major glitch. Perusing the forums leads me to believe that font ugliness cursed many others.

Thanks.

---

### Post by mjukr on 2005-04-14
Anyone know?

---

