---
title: "Software update connection and other issues with old laptop."
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by linuxg on 2010-03-07
Hello all:
I have an old (by computing standards - really old) laptop: a compaq presario: pentium 3, with 192 megs and an upgraded hard-drive of 40G.

I had been running an older version of ubuntu(5.4) on the laptop reasonably for quite some time now.

I just did a fresh install of 9.10 on the laptop.
I have been able to finally get access to the internet using firefox and can see the local lan with windows xp pro machine/drives.
I have been able to connect wirelessly and with an eth cable.


Couple of problems though:

Main problem ) I cant get the update manager to connect out. 
    Seems like I cant connect through the routers port 8080?
    If the internet works through this port, why should I get a "Connection refused" error ???
    I have tried this with the eth cable and the same errors.
    I have also tried getting updates with the command line: sudo apt-get update


annoying issue:) When using the smc wireless card (SMC2835W), I get speaker crackles when ever there is activity on the card.


annoying issue:) When running a terminal and a firefox instance with one tab, seems like the os is trashing like crazy ! I hear it constantly...

For such old hardware, is xubuntu the preferred distro ?
although, i would imagine if I cant update packages, then i would be in the same boat ?


Any help would be appreciated

Thanks.

---

### Post by Old_Grey_Wolf on 2010-03-07
Ubuntu needs 384MB of RAM. I have gotten Ubuntu 9.10 to run on 256MB; however, it was painfully slow. Xubuntu is for 192MB of RAM.

You could try going to Synaptic Package Manager, select Settings > Repositories, then select Download from > Other..., then Select Best Server. 

Also check the router/firewall for blocked ports.

---

### Post by linuxg on 2010-03-13
Thanks and sounds good, I did download the xubuntu and will try to install, however, the update manager issues still remains. Can see the main port 8080 as blocked though.
So, even if I install the xub, seems like updates would be a problem anyway.

---

### Post by Old_Grey_Wolf on 2010-03-13
You may be having a problem with the repository list. See if any of this helps, [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

---

