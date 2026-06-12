---
title: "Changing installed version."
date: 2022-06-08
forum: Installation &amp; Upgrades
---

### Post by sundaresh on 2022-06-08
I have installed hirusite hippo on my system, but now I came to know it is EOL , not LTS ? How do I change from this version to another which is LTS ?

---

### Post by VMC on 2022-06-08
Why not just install the current LTS, 22.04 and be done with it?
Here's a YouTube to go from 21.04 to 22.04 LTS:
[https://www.youtube.com/watch?v=yRjp25TgR3s](https://www.youtube.com/watch?v=yRjp25TgR3s)

---

### Post by Bashing-om on 2022-06-08
sundaresh; Hello -

As Hirsute Hippo (21.04) has not as of this time been rolled to old-releases; you may do the normal release routine(s).
The CLI method:
```

sudo apt update
sudo apt upgrade
sudo apt do-release-upgrade

```
this brings you to the 21.10 release that also goes End_Of_Life next month.
from 21.10 one runs similar:
```

sudo apt update
sudo apt upgrade
sudo apt do-release-upgrade 

```
Note Post#5

Now this is a lot of bandwidth and time to get to 22.04 - you may be the better served to fresh/clean install 22.04.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by ActionParsnip on 2022-06-09
Hirsute was never LTS. The LTS releases are every two years.

18.04 is LTS
20.04 is LTS 
22.04 is LTS
24.04 will be LTS when released
26.04 will be LTS when released

and so on....

---

### Post by Impavidus on 2022-06-09
> **Bashing-om said:**
> 
note the -d flag for reaching the in(D)evelopment status of 22.04 - that is the latest LTS release.


There's no need for the -d flag to go from 21.10 to 22.04; that upgrade path has been released. One does still need the -d flag to go from 20.04 to 22.04, as that upgrade path hasn't been released yet.

---

### Post by TheFu on 2022-06-09
I've found upgraded to require 2+ hrs for each, whereas a fresh install is 10-15 minutes and will not bring the cruft from those old installs forward.

Just backup the stuff you can't lose before doing a fresh install. Do the install, then restore what you backed up - probably data in your HOME directory.  This will prevent all sorts of odd issues that sometimes happen when old config files get migrated forward.

---

### Post by guiverc on 2022-06-09
I'm of the belief that a 21.04 system can no longer be upgraded using `do-release-upgrade` or [Ubuntu Release Upgrader tools]("https://launchpad.net/ubuntu/+source/ubuntu-release-upgrader") for non-LTS users (*21.04 was never a LTS release*), but I'd likely still try it.

If it's a desktop system, I'd just re-install anyway as it's far faster, and you can re-install a Ubuntu desktop system (*including flavors*) without losing your data, and having your *manually installed* applications re-installed automatically (*if available in Ubuntu repositories* for the new release). 

When Lubuntu 21.04 reached EOL & I didn't need that system for *support* purposes any more, I just installed Lubuntu *jammy *(22.04) LTS over it as a QA (*Quality Assurance*) test install and thus had my 22.04 system ready.  I used 22.04 as I already had a 21.10 system (*a prior 20.10 had upgraded to that 6 months before*).  For Lubuntu it's documented [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") (see the "*Install using existing partition*" testcase) though do note that document was written for QA-testers & not end-users, but it still maybe helpful.

21.04 EOL Notice - [https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)
21.04 Released (note no LTS mention) - [https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/](https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/)

FYI:  If using partition encryption of anything else that's currently not used by default in Ubuntu releases; you can still use the "*Upgrade via re-install*" or "*Install using existing partition*" install; you just need to add the packages not found on the ISO to the *live* system so they can be handled, then start the installer...  I used this to upgrade a 20.04 laptop (*with encrypted home*) to 22.04 as it took a fraction of the time of `do-release-upgrade` & as the Lubuntu team had already completed all QA-testing for 22.04 at that time; I used Xubuntu to perform the upgrade (*it works in all; but note: I had that choice as the laptop in question had two desktops installed - Lubuntu's LXQt & Xubuntu's XFCE as I do love both*).

---

### Post by #&amp;thj^% on 2022-06-09
As a older user I just "sed" my way there>>>>if you try this you must first purge all active PPA's and be fully upgraded.
then I'll simply run:
```
sudo sed -i 's/impish/jammy/g' /etc/apt/sources.list
```
and update && upgrade, and bobs yer uncle just upgraded to jammy.
and yes replace names to their respected names.

---

### Post by TheFu on 2022-06-09
LTS for Ubuntus is easy.

Even years, April.  Everything else is NOT an LTS.
```
22.04
^   ^
|   &#9493;&#9655;  April 
&#9493;&#9655; 2022

```
Assume all desktop LTS flavors have 3 yrs of of support.

The default LTS "Ubuntu Desktop" - which is either Gnome3 (20.04) or Gnome4 (22.04) now, get 5 yrs of support. All others get 3.
The LTS "Ubuntu Server" - that's the zero GUI "server" distro - gets 5 yrs of support.

Before Canonical had their "LTS" nailed for what the market could handle, they had some false starts and a few non-even year, none-April releases did get LTS support. I think that was before they got the HWE kernel and GUI aspects included in their LTS support channel.

Oh, and If we don't stick with the default kernel for the LTS initial release, then we have to always upgrade to the next kernel in the HWE cycle for that LTS release to stay "supported."  
So, 20.04 was released with a 5.4.x kernel.  If your system keeps that kernel for the entire support period, life is good.  But if we install 20.04.1 and got the 5.8.x kernel, no we had to move from 5.8.x --> 5.10.x --> 5.11.x --> 5.13.x as the HWE kernels became available to remain under "support".  I still with the initial release kernel, until a few months before the system will be moved to the next LTS release.  So my 20.04 system will remain on 5.4.x kernels until I'm about to move to 22.04 (or more likely 24.04) in a few years.

Currently, my 18.04 systems, which will lose support next April, are running the HWE kernels, which match the 20.04 5.4.x kernels.  This is just 1 more thing that I don't need to worry about if I upgrade. I'll already know that the kernel and supported hardware in that kernel work with my system(s).

Of course, other people will have come to slightly different conclusions and choices than me.  We all have different needs.  To me, "new" is the enemy of "stable".  Stable is more important than new almost always here.  I've been avoiding the newest stuff until I cannot avoid it any longer. My users don't care about new. They just want systems that work and don't get cracked.  In the 1990s, I was constantly seeking "new", but at that time, things were changing so very fast that huge basic features were being added almost monthly across almost all libraries and programs.  I don't mind running 3 yr old, but still maintained versions of most programs, provided they are stable and have the features I need.  There are a few programs where I usually am less than 6 months behind their current released package, but those are extremely niche programs.  For example, ccextractor  and apertium. I doubt most people here have ever heard of those programs. They are part of my workflow a few times each week.

Choose what you need, within the support formulas.

---

### Post by sundaresh on 2022-06-16
It does not perform the upgrade.It says your version is not supported. I cannot install or uninstall anything in this version and none of the packages I tried installing work on this system. And they do not uninstall despite removing them.

---

### Post by TheFu on 2022-06-16
> **sundaresh said:**
> It does not perform the upgrade.It says your version is not supported. I cannot install or uninstall anything in this version and none of the packages I tried installing work on this system. And they do not uninstall despite removing them.

Learn this lesson. Don't use unsupported versions and migrate BEFORE support ends.
There are ways, but since you are asking the question, it is likely the required steps are too complicated and nobody can tell you exactly what to type for the 50 things that need to be done to migrate from an unsupported OS to another without all sorts of risks and bad results in the end.

Best to backup and data you can't lose and install either 20.04 or 22.04 at this point.  Depending on the DE and OS you choose, you'll have until next April for support or until April 2027.

If you will say the DE (Desktop Environment) being used, then we can advise the support period.  Most DEs in an LTS release get 3 yrs of support with a few exceptions that get 5 yrs. For example:
XFCE, LXQt, Cinnamon, Mate get 3 yrs.
Gnome 3/4 in Ubuntu Desktop gets 5 yrs.

---

### Post by ajgreeny on 2022-06-16
I have used the method shown by 1fallen in post #8 but never in one of the Ubuntu family; I did it when using Debian on which Ubuntu is based, and there all went faultlessly.

It could be worth a try on your system, but be prepared for potential problems when you reboot after the upgrade.

---

### Post by #&amp;thj^% on 2022-06-16
> **ajgreeny said:**
> I have used the method shown by 1fallen in post #8 but never in one of the Ubuntu family; I did it when using Debian on which Ubuntu is based, and there all went faultlessly.

It could be worth a try on your system, but be prepared for potential problems when you reboot after the upgrade.

I've used it on very similar cases as the OP, works great, but first PURGE all active PPA's and run update && upgrade, then use the "sed" command in OP's case use:
```
sudo sed -i 's/hirsute/jammy/g' /etc/apt/sources.list
```

---

