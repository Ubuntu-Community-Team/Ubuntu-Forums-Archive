---
title: "41 updates in a 3 days? My God!"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2007-03-28
I am using Ubuntu as a critical software development workstation - and can't afford destabilization of the system - in addition to needing to have as controlled environment as possible (so that troubleshooting, debugging, backtracking is easier).

But I keep being bombarded with updates almost weekly. Usually I try to keep up with that so that I don't accumulate too much lag, but in the past 3 days my Update Manager notifies me about 41 (forty one!) udpates. This is crazy - considering the fact that I have already applied **hundreds** of updates to the system (fortunately without any adverse effects) since I installed it in November 2006 using the latest ubuntu-6.06.1-desktop-i386.iso CD (at the time).

My questions are basically:
[LIST=1]
[*]Are all these updates really necessary? I mean, if I don't use Evolution, why do I need to get so many Evolution updates? Is there a way to tell Update Manager to notify me about critical and/or security updates only?
[*]Is there an updated CD (e.g ubuntu-6.06.**5**-desktop-i386.iso) that already contains all recent updates? (otherwise, re-installation could take hours...)
[*]Alternatively, is there a way to download a "differential" updates CD that contains all updates released since ubuntu-6.06.1-desktop-i386.iso?
[*]Suppose I am using Ubuntu mainly as a host OS for VMWare, not so much as an office desktop system. Is the Server version of Ubuntu more suitable for this purpose?  Does the server version come with a GUI desktop like the desktop version?
[/LIST]

Thanks,
Alex

---

### Post by zvacet on 2007-03-28
I think you can find solution in system>administration>software repositories(maybe this is not correct name because I don´t use english version).Open it and do quick search and you will find choices about updates.Pick what suits you better.If you don´t want upgrade some program go to the synaptic,find that program,mark it and from edit I think choose lock version.Anyway I don´t think Ubuntu gives updates without reason.

---

### Post by cyberdork33 on 2007-03-28
Updates seem to happen more frequently as a new release gets close.

---

### Post by ygarl on 2007-03-28
BTW - I don't use Evolution either... 
Do what I did:
Go to Synaptic, and just uninstall it.

No more Evo updates!
(I much prefer Thunderbird - but that's me!)

---

### Post by mardawi on 2007-03-28
Yeah.. that's what i did too. if you don't use Evolution then just remove it and the update manager will stop bugging you with large evo updates every now and then!

---

### Post by xp_newbie on 2007-03-28
Hmmm... I am trying to uninstall Evolution now (using Synaptic Package Manager I mark it for removal) and it says:

> Mark additional required changes - to be removed:
  evolution-exchange
  evoloution-plugins
  ubuntu-desktop


Removing  evolution-exchange and   evoloution-plugins is fine with me, but removing  **ubuntu-desktop**???

Uh oh... what am I missing here? Am I going to loose the entire GNOME desktop if I uninstall Evolution?

Thanks,
Alex

---

### Post by qamelian on 2007-03-28
> **xp_newbie said:**
> Hmmm... I am trying to uninstall Evolution now (using Synaptic Package Manager I mark it for removal) and it says:



Removing  evolution-exchange and   evoloution-plugins is fine with me, but removing  **ubuntu-desktop**???

Uh oh... what am I missing here? Am I going to loose the entire GNOME desktop if I uninstall Evolution?

Thanks,
Alex

The ubuntu-desktop package is a meta-package and can be safely removed. It is only used to provide an easy way of determining dependencies for the default Ubuntu installation.  No other packages will be removed.

---

### Post by FuturePilot on 2007-03-28
Unless you want to upgrade to the next distro in your case Edgy. Then you won't get anything that was added to Edgy that was not present in Dapper.

---

### Post by xp_newbie on 2007-03-29
> **qamelian said:**
> The ubuntu-desktop package is a meta-package and can be safely removed. It is only used to provide an easy way of determining dependencies for the default Ubuntu installation.  No other packages will be removed.

OK - thank you. I also tried to remove evolution-data-server and it said that this will remove **ekiga**, too. WTH... ??? Why should a softphone be dependent on a bloated PIM application?

I am not touching anything (whether uninstall or update) - it's waaaaaaay not making any sense.

Unless someone can explain to me please what is going on.

Thanks,
Alex

---

### Post by rillip on 2007-03-29
Ye olde kenundrum, most complain Windows doesn't update often enough, now the complaint is Linux update too often.. :D

If you're honestly dedicated to pairing down your instalation without risking any sort of stability/performance/application issues, the best thing to do would be to stand up a mirror, start removing things one at a time and see what breaks it.  Tedious, but effective. If you have a maintenance window for whatever you are doing, then it should be trivial to remove an applicaiton at that time, if it goes down oh well, then just add the package back if bad things happen.

Nice thing about Linux, you don't have to restart every time you install an ugprade/program/sneeze.

Best of luck with customizing it the way you're wanting

---

### Post by xp_newbie on 2007-03-29
> **rillip said:**
> If you have a maintenance window for whatever you are doing, then it should be trivial to remove an applicaiton at that time, if it goes down oh well, then just add the package back if bad things happen.

Thanks - that's exactly what I intend to do.

I am just curious though - why removing Evolution data server mandates removing Ekiga, too? What's the connection between the two?

Or is it simply a bug in the APT packaging?

---

### Post by justin whitaker on 2007-03-29
> **xp_newbie said:**
> Thanks - that's exactly what I intend to do.

I am just curious though - why removing Evolution data server mandates removing Ekiga, too? What's the connection between the two?

Or is it simply a bug in the APT packaging?

It is probably something Ubuntu specific. According to the website, the only things you need are:

Gnome Libraries
Open LDAP
OPAL and PWLIB
SDL

Maybe when they wrap the desktop metadata together, they tie Ekiga and Evolution with Open LDAP?

---

### Post by PriceChild on 2007-03-29
Could you paste your /etc/apt/sources.list please?

41 updates sounds like something else is going on...

---

### Post by xp_newbie on 2007-03-30
> **PriceChild said:**
> Could you paste your /etc/apt/sources.list please? 41 updates sounds like something else is going on...

Sure, here it is:

> ~> cat /etc/apt/sources.list

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ
erse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted 
universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
~> 

Do you see anything "suspicious"?

Thanks,
Alex

---

### Post by PriceChild on 2007-03-31
Wow and you don't even have the universe or multiverse enabled.... I haven't got a clue sorry.

---

### Post by suckpipe on 2007-04-03
Let me just ask one simple question: will the update manager only ever update packages that I already have or will it just list every updated package available? In other words, can I just say "sure, update" or do I need to carefully deselect every package I don't recognize?

---

### Post by xp_newbie on 2007-04-04
> **suckpipe said:**
> Let me just ask one simple question: will the update manager only ever update packages that I already have or will it just list every updated package available? In other words, can I just say "sure, update" or do I need to carefully deselect every package I don't recognize?

I wish I could answer this answer. If someone has an authoritative one, I would be glad to hear (read) it.

---

### Post by christhemonkey on 2007-04-04
The package manager should only ever upgrade packages that are installed on your system.

---

