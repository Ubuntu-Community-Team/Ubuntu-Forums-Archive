---
title: "Rewrote boot partition"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Lostincyberspace on 2008-01-23
I, for my brand new linux installation monday, went and made seperate partitions for my /boot and my /home partitons, pretty smart thing I thought. The install went fine and I really liked it. But to day when I went and installed my testbed on a seperate partition I told it to over right the previous /boot partition thinking that thinking that would be a good way to keep clutter out of my system. When I realised I coulden't boot to my regular partition I imediatly whiped out my supergrub disk and rebooted. And it all went  down hill from there. And to make a long story short I can't boot any thing any more and am rather flustered about what to do next. 

Could someone help me figure out how I could fix my biggest mistake ever (with computers at least).

If this helps the main partition is Linux Mint, and the test bed partition is Xubuntu though neither boots right now, So they won't be much help to me.

---

### Post by Rocket2DMn on 2008-01-24
Although it doesn't seem that Windows is the source of your problem, there is a solution offered to reinstalling GRUB when installing windows overwrites your bootloader:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
more specifically for you, the reinstallation of GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)
Ideally, this should fix your problem as well.

It also mentions the Super GRUB Disk on that page, but I guess that didn't work too well for you :(

---

