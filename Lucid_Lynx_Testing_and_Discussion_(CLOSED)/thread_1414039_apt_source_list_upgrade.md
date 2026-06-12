---
title: "apt source list upgrade"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by suoko on 2010-02-23
i guess when upgrading from an ubuntu version to another, apt should check your enabled ppa repositories and see if there's a version for the new ubuntu which we're going to install.
And then ask if you want those enabled (or just enable them).
This is true for lucid since many many ppa repos i was using in kk were already available for LL (but don't remember which ones !)

---

### Post by slakkie on 2010-02-23
The upgrade script will disable them. After the upgrade you can "upgrade" your ppa's and well, do your thing. 

Nothing wrong with the current implementation.

---

### Post by phenest on 2010-02-23
> **slakkie said:**
> The upgrade script will disable them. After the upgrade you can "upgrade" your ppa's and well, do your thing. 

Nothing wrong with the current implementation.

I think the OP has a point. The upgrade procedure should check any enabled PPA's too, and only disable those that have no upgrade candidate.

---

### Post by Seventh Reign on 2010-02-23
> **slakkie said:**
> The upgrade script will disable them. After the upgrade you can "upgrade" your ppa's and well, do your thing. 

Nothing wrong with the current implementation.

I agree, that there is nothing wrong with the way it is now, but I believe what he wants is for it to automatically update the PPAs to the next version.  Kinda like how Firefox extensions upgrade from version to version.  

God we are getting lazy.  No one wants to 'do' anything anymore.  Everyone wants things done automatically without any interaction.  Its marking the end for Arch and Slackware etc ..

---

### Post by slakkie on 2010-02-23
So you want the upgrader to see, ahh, ppa, now lets see if I can change the release for it, and then upgrade accordingly.

It is possible, but I already saw comments in the code of the add-ppa script that some things are placing a huge load on servers, which is not desirable. 

TBH, the upgrader will only upgrade from official repo's, which PPA's are not. Ubuntu devs cannot guarantee that everything on the PPA is correct and fullfills all of the needed dependencies. So if a PPA breaks the lot, then you start blaiming the upgrader, while a PPA is at fault. Seperate the two, and you will never have this issue.

---

### Post by dino99 on 2010-02-23
my 2 cents:

i have used and test so many ppa, specialy in Karmic development time when most of everything was broken, to resolve the problem waiting for a distro update which sometime have taken ages.So was the hard days.

But now the situation is very different: huge improvements have been done, says "apport hooks" creation, early upstream integration, better and faster patches included and coming from other distros, and so on. So, on my own, i only use ppa from devs/teams close to ubuntu developement, because "user" ppa often brings more trouble.

So i think that the actual "apt" script have not to be modified, or only include ppa from dev team.

---

### Post by garvinrick4 on 2010-02-23
You know I have to believe that the few ppa's I use were updated to lucid at time of dist-upgrade, I used 2nd line of code at last upgrade to do it all at once. Karmic to Lucid.
Any which way it was smooth and seamless as I remember. Does not seem big issue to have
to look into ppa's of your choice to dist-upgrade anyway. Just an opinion.

sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list



sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by seeker5528 on 2010-02-24
> **suoko said:**
> i guess when upgrading from an ubuntu version to another, apt should check your enabled ppa repositories and see if there's a version for the new ubuntu which we're going to install.

First, apt doesn't provide the features to update your sources, this is a function of update manager.

Second, allowing PPAs and/or 3rd party repositories to be enabled during upgrades when using the officially supported upgrade process would surely lead to a significant increase in bug reports resulting from problems during upgrades, so I can't really see them wanting to add functions to allow them to be enabled when upgrading.

Even if they added a disclaimer in there about upgrading while these repositories are enabled being unsupported and bug reports should not be filed about issues that occur when they are enabled, it still seems like more hassle than it's worth.

Later, Seeker

---

### Post by LKjell on 2010-02-24
You can have a compromised and let update-manager disable when the upgrade is happening. After the first reboot you get an option to reenable all those you need. Like now you have to go through all of them...

---

