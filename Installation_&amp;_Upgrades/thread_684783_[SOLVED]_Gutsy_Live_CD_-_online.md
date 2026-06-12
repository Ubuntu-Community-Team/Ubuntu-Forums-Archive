---
title: "[SOLVED] Gutsy Live CD - online"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Bruce M. on 2008-02-01
My current OS: Ubuntu 7.04 - Feisty Fawn

I have Ubuntu Gutsy running on a Live CD at the moment. Everything is working fine, except compiz. I didn't expect compiz to run on this old P-III anyway, no special video card or sound card, just the built in stuff here.

However it is running.

Does this mean if I install Gutsy (via the Alt CD I have) that it will run on my system?

I'm considering Kbuntu 7.10 as well, I will be getting the Live & Alternate CD's shortly.
But I have a question with that too:

My system:
[LIST=1]
[*]/dev/sda1/ - W2K
[*]/dev/sda5/ - Feisty - Root
[*]/dev/sda7/ - /home/bruloo
[*]/dev/sda6/ - /swap
[*]/dev/sdb1/ - my data disk
[/LIST]

If I end up installing Kubuntu 7.10, will it recognize all my files and data?

ie:[LIST=1]
[*]Firefox - bookmarks
[*]GNUCash - data files
[*]Thunderbird - email database
[*]The rest I can live with or without.  :)
[/LIST]

---

### Post by Rocket2DMn on 2008-02-01
Gutsy should work just fine, but I wouldn't try to get compiz working on that old computer.  Also, Kubuntu might be a little much for an older machine because KDE is a heavier desktop environment than Gnome.  Xubuntu (with Xfce instead of Gnome) may be the path to take since Xfce is even more lightweight than Gnome.
Everything should be recognized if you don't overwrite your /home partition.  Of course, I would backup everything important first (you can export your firefox bookmarks and thunderbird settings to files and store them on your backup disk).

---

### Post by Bruce M. on 2008-02-01
> **Rocket2DMn said:**
> Gutsy should work just fine, but I wouldn't try to get compiz working on that old computer.  Also, Kubuntu might be a little much for an older machine because KDE is a heavier desktop environment than Gnome.  Xubuntu (with Xfce instead of Gnome) may be the path to take since Xfce is even more lightweight than Gnome.
Everything should be recognized if you don't overwrite your /home partition.  Of course, I would backup everything important first (you can export your firefox bookmarks and thunderbird settings to files and store them on your backup disk).

My mistake, I knew Kbuntu is heavier, but forgot I knew.

I meant Xubuntu. I downloaded the system into Feisty (to start as another Session in the logon screen) and it is lighter.

I take it that Xubuntu (or is it Xbuntu) won't have compiz that I can't use anyway.

I'll look at it next.

Thanks
Bruce

---

### Post by Rocket2DMn on 2008-02-01
Its Xubuntu and Kubuntu.  I'm not sure if Xubuntu has built in capacity for compiz, but even if it does, you don't have to use it.  I even disabled compiz on my Ubuntu setup when I stopped using my laptop as my primary computer.
You should probably just get Gutsy, it's not any heavier than Feisty, and in fact I think benchmarks showed a slight improvement with Gutsy over Feisty, but don't quote me on that.  At this time I plan on making Hardy my last stop with upgrades to my laptop with Ubuntu since its an LTS (long term support) release.

---

### Post by Bruce M. on 2008-02-02
> **Rocket2DMn said:**
> Its Xubuntu and Kubuntu.  I'm not sure if Xubuntu has built in capacity for compiz, but even if it does, you don't have to use it.  I even disabled compiz on my Ubuntu setup when I stopped using my laptop as my primary computer.
You should probably just get Gutsy, it's not any heavier than Feisty, and in fact I think benchmarks showed a slight improvement with Gutsy over Feisty, but don't quote me on that.  At this time I plan on making Hardy my last stop with upgrades to my laptop with Ubuntu since its an LTS (long term support) release.

To be honest I want to stay with gnome.
Think I'll try it.

Thanks
Bruce

---

### Post by Bruce M. on 2008-02-15
15 Feb 2008

Today was Install Gutsy Day.

Gutsy 7.10 now up and running after a some research, two of which are below:

[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=684783](http://ubuntuforums.org/showthread.php?t=684783)
[*][http://ubuntuforums.org/showthread.php?t=656530](http://ubuntuforums.org/showthread.php?t=656530)
[/LIST]

I chose the Alt CD and installed 7.10 over 7.04 keeping my /home (different partition) intact (had a backup though) and everything went fairly well.

The Alt CD checked out OK, so I put:

sda5 - / - reformat
sda7 - /home - kept data
sda6 - /swap

First attempt had a hiccup, it failed the "Select and install software", but gave me the chance to try agin starting at that point.  So I did.

Second attempt was successful.

186 security updates later and I was reinstalling some of my programs:

[LIST=1]
[*]Thunderbird - all mail available
[*]jPilot - data intact
[*]conky
[*]curl
[*]lm-sensors
[*]Thunar
[*]GNUCash
[*]Inkscape, and my one and only game;
[*]Wesnoth
[/LIST]

I finally got Gutsy!

---

