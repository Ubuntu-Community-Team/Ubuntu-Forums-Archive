---
title: "Gutsy upgrade from allternate CD accesses net"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by sjatkins on 2007-10-18
Since Ubuntu is popular (YAY) upgrading over the net is dog slow (BOO) today.  So I managed to download the alternate ISO and planned to upgrade my 3 machines from it.  When asked I told it to only use what was on the CD to upgrade.  Yet it is still accessing the net in "Fetching the upgrades" in the Distribution Upgrader.  What gives?  Net access was precisely what I wanted to avoid.

---

### Post by sjatkins on 2007-10-18
Many hours to do an OS upgrade is not acceptable.   This is way slower than I have seen Ubuntu upgrades be in the past and much slower than OS X or even Windoze upgrades.

---

### Post by sjatkins on 2007-10-18
Is there a way to copy the bits from CD to disk and force it to upgrade from them in the most efficient way possible?  I don't need a slick GUI and sure don't need or want to hit the net in the process.  


Thanks much.

---

### Post by jetpeach on 2007-10-18
Do you run KDE or Gnome? Have any programs installed on only one or the other by default? If so, my *guess* is that it is still going to the net for packages not on the alternate CD - e.g., if you run any KDE packages not on the GNOME ubuntu alternate CD, it can only get the new ones through the web. Or, if you run Kubuntu and any GNOME pacakges were needed... If it doesn't do this, there really isn't any way for it to complete the upgrade, unless it just removes all the packages that can't be found directly on the the CD and will have unmet dependencies...

So what we need is an alternate **DVD** that would contain nearly all the packages, including those only on one of the two K/Ubuntu distributions.

Searching through the torrent list
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
I see two big DVDs, one for Ubuntu and one for Kubuntu. Last time when I upgraded to 7.04 I tried one of these, but it still didn't have all the packages needed and I had to wait for stuff off of the repositories. I think I even posted complaining, "what *is* on this 4GB dvd if not the packages for both KDE and GNOME programs?" I think the reply was, it could be used as a live CD or alternate and maybe had some other things. This time around I haven't yet downloaded the DVD so don't know if it would have everything needed this time, but if it doesn't then we should file a bug - they really need to have a DVD with virtually *everything*on it...or at least a method to upgrade without waiting for the repositories.

---

### Post by jetpeach on 2007-10-18
> **sjatkins said:**
> Is there a way to copy the bits from CD to disk and force it to upgrade from them in the most efficient way possible?  I don't need a slick GUI and sure don't need or want to hit the net in the process.  


Thanks much.
I believe so, although don't know for sure. The alternate CD should contain most of the .DEB packages needed during your upgrade - they are in the directories in /cdrom/pool
If these were copied to the hard dist where the upgrade normally copies files (sorryu don't know this off hand) then it shouldn't have to re-download those packages.

---

