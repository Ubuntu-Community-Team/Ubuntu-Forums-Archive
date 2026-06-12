---
title: "Upgrading Hoary-&gt;Breezy-&gt;Dapper without ubuntu-desktop - possible?"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by benblout on 2006-10-16
Hi all,

I have a very bare-bones install of Hoary on a low-memory machine that works great for me.  I want to upgrade to Dapper, as security support for Hoary should be ending soon.   One of the steps mentioned in the upgrade guides is to install the package ubuntu-desktop before I upgrade.  On my system, that will install 477 additional packages.  It hardly seems practical to install all those packages, and then try to remove them again.  How can I proceed?

For examples of the warnings, you can see step 1 in the section "Upgrading by changing sources and the command line" at:
[DapperUpgrades]("https://help.ubuntu.com/community/DapperUpgrades#head-0171d3953a2ea19e9b4228bcd5cde3ecfb67f7af")
or this post mentioning problems:
[Sounder Post]("https://lists.ubuntu.com/archives/sounder/2006-June/007543.html")

Or, to put it another way.  I have a server-like install of Hoary.  I want to upgrade to the server version of Dapper, without doing a re-install. What is the best procedure?

Thanks for any help,

Ben

---

### Post by benblout on 2006-10-16
Or, perhaps a related question.  If you don't know the answer, to my original question, but can suggest where to look for the answer, that would be quite helpful.

-Ben

---

### Post by moore.bryan on 2006-10-16
[I]i'm not sure it's possible to upgrade without ubuntu-desktop... you could try aptitude running the --without-recommends option; that is:
```
sudo aptitude install --without-recommends ubuntu-desktop
```
if it doesn't work, at least it'll tell you so before you make any drastic changes...
[/I]

---

### Post by benblout on 2006-10-16
> **moore.bryan said:**
> [I]i'm not sure it's possible to upgrade without ubuntu-desktop... you could try aptitude running the --without-recommends option; that is:
<snip>
if it doesn't work, at least it'll tell you so before you make any drastic changes...
[/I]

I have not seen it recommended to upgrade with aptitude; why are you suggesting it over apt-get dist-upgrade and/or the "Update Manager application", as suggested in the Dapper Upgrade guide?

Thanks,

Ben

---

### Post by moore.bryan on 2006-10-17
> **benblout said:**
> I have not seen it recommended to upgrade with aptitude; why are you suggesting it over apt-get dist-upgrade and/or the "Update Manager application", as suggested in the Dapper Upgrade guide?
Thanks,
Ben
*according to ubuntu, the update manager is the best way to go, but there are a zillion (okay, maybe that's an exaggeration, but there are a lot) of posts in this forum advocating aptitude over apt-get because of its innate ability to better resolve dependencies...  in essence, there's no difference between ```
sudo apt-get dist-upgrade
``` and ```
sudo aptitude dist-upgrade
``` it's just claimed aptitude handles dependencies better...*

---

