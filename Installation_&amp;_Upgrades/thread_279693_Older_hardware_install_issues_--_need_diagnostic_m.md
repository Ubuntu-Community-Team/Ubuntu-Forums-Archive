---
title: "Older hardware install issues -- need diagnostic method."
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by cheuschober on 2006-10-18
Hi. I'm installing 6.06.1 on some older hardware (Athlon XP 2200+, a 30GB hdd from 2001, GeForce 4400Ti) and have run into some issues with failed installations and/or kernel panics.

What I need is some time-tested and/or suggested method for diagnosing my pc ills before I go out and burn a wad of cash on new hardware.

_Known Possible Problem Areas_
[LIST=1]
[*]The drive used to burn the ubuntu cd (a laptop drive) has been slowly dying for some time. Alternate install cd burnt at 4x. Thus far no burning errors have been noticed on the drive only dvd read errors have become apparent.
[*]The first dvd-rom was last used on a windows box. It was a rewritable with excellent reliability but accessing / detection / mounting (take your pick) takes a laboriously long time under linux (to the tune of 10-15 minutes) making me suspect whether or not it has full support under linux os's. (this was observed in both knoppix and ubuntu)
[*]The second cd-rom used was replaced by the former on the aforementioned windows box for having read errors after a yearlong tour of duty. It does not suffer from the delay problems of the first dvd-rom used.
[*]The 30gb hdd this is being installed on is awfully loud and quite old (2001).
[*]The fan on the video card (GeForce 4400Ti) has siezed up.
[*]This motherboard is definately a budget - budget model that, while new and Socket A doesn't recognize my cpu or ram frequencies automatically. I've guessed 133 and 166 respectively.
[/LIST]

_Problems reported_
Installation failed six out of six attempts and always in the latter quarter of configuring software packages but not always on the same package. Occasionally it is 'gnome-applets' occasionally 'libpango' and so forth. On the fifth attempt I was able to force it through by repeatedly telling the installer to set up software until at it installed without error.

After the successful installation I was able to boot the system normally with the exception of being incapable of any DNS resolution on my wireless card (atheros based using the Madwifi utility. Resolv.conf was copied directly from another system on the same network as was /etc/network/interfaces. Pings to lan, gateway, and wan objects were all successful). I thought that perhaps some module was missing or a madwifi compilation flag was awry. I rebooted on two occasions. No troubles.

Leaving the pc it eventually went to a screensaver. When I awoke in the morning it was frozen on the screensaver. A soft-reset later and I had a kernel panic on attempted boot. All boot attempts now resulted in kernel panics.

Installation was attempted again and failed in the same location. This time I didn't attempt to force it through.

Do you have any idea what this could be? What would your suggested diagnostic route be?

Many thanks.
~Chad

---

