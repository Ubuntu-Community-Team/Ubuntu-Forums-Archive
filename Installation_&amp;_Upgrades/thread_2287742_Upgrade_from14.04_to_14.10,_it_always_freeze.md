---
title: "Upgrade from14.04 to 14.10, it always freeze"
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by Pascal_Paquin on 2015-07-21
So tonight I decide to upgrade my 14.04 install, to the 14.10 install.
Everything was working fine on the upgrade process.

But since then I only have problem. As soon as I try to open anything, it will freeze, either completly, so I can't even move the mouse, or something the mouse will move, I will be able to do ctrl+alt+F2 and type command there, but I can't open anything.

Is there something that I can try to solve that problem ? I want to avoid to reinstall completly, but if it's the last solution, then I won't have any choice

Thanks in advance for any help

---

### Post by Bucky Ball on 2015-07-21
Unsure why you decided to upgrade from a stable, long-term support release to an almost dead one. Forget 14.10. It is out of support in a couple of days. 

I suggest you backup your data while running from live media and clean install 14.04 LTS (supported until 2019) or 15.04 (January 2016).

---

### Post by Pascal_Paquin on 2015-07-22
Do you think I will be able to update while in the command line (ctrl+alt+f2) and that it will be stable once again if it's working ?

---

### Post by dino99 on 2015-07-22
hello Pascal,

when dist-upgrading a system, you need first to deactivate the third party(ies) sources (mainly ppa) and downgrade to the genuine package version if necessary. Synaptic is an easy tool to do that stuff. Then its a good idea to clean the system with clean/autoclean/autoremove/gtkorphan; and finally update & reboot. You then are ready to dist-upgrade.
But wait a couple days to jump directly to 15.04

---

### Post by v3.xx on 2015-07-22
To add to Buckies post..

14.04 has long term support (5 years).  The next LTS is 16.04, due out in April of 2016.  You could then upgrade direct from 14.04 to 16.04 because of the LTS feature.

A dist-upgrade is not a version upgrade.  #3
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

And use gtkorphan with extreme care as it is known to bork systems.

---

### Post by Pascal_Paquin on 2015-07-22
What about the do-release-upgrade, will that upgrade to 15.04 and hopefully solve my freezing problem ?

---

### Post by Bucky Ball on 2015-07-22
> **Pascal_Paquin said:**
> What about the do-release-upgrade, will that upgrade to 15.04 and hopefully solve my freezing problem ?

Upgrading to a new release is definitely NOT the way to fix a broken one. If you can't do an update/upgrade or get to a desktop, upgrading, if you can, has a 99% chance of not fixing the issue and a good chance of adding further confusion. Do you actually know what release you are running and if the upgrade was successful?

Post the output of these commands, please:

```
sudo uname -a
lsb_release -a
```

---

### Post by Pascal_Paquin on 2015-07-22
I'm at work so I won't be able to post it soon... I think I might just re-install it, it seems most of my stuff was on another partition so I won't lose that much

---

### Post by Bucky Ball on 2015-07-22
Okee doke. I recommend 14.04 LTS and good luck. Post a new thread if you hit any brickwalls. ;)

---

