---
title: "Did you upgrade from Dapper to Hardy ?"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by koenn on 2008-06-08
I'm trying to upgrade from Ubuntu 6.06 to 8.04, and I'm having a bit of trouble with it.

1- From what I read, I expected that update-manager or 'software-properties" would show me "new release available" but it never does.
I suspect this notification is a configurable option I turned at some point, but I can't find how to turn it on again

so I decide to upgrade "server style :"
2- I run "do-release-upgrade" and it says "no new release available"

3- as a workaround, I try "do-release-upgrade -d" and ... it fails
In the logs I find what probably caused the failure :
"package ubuntu-desktopis marked for removal but it is on the removal blacklist. Dist-upgrade failed : a essential package would be removed"

4- so I abort the upgrade, remove ubuntu-desktop, and try again with "do-release-upgrade -d". The upgrade is in progress now.  

So, I'm wondering : did anyone succesfully upgrade from Dapper to Hardy ? 
if so, how ? Or : what am i doing wrong ?

quick show of hands ?

---

### Post by nick09 on 2008-06-08
Download the 32 bit or 64 bit version(look to see if your processor is 64 bit) burn to CD or DVD and I think you should be able to upgrade Ubuntu that way.

But I don't know much so check this page out:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by LaRoza on 2008-06-08
Did you update the sources?

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by ynnhoj on 2008-06-08
i think there's a "dapper-updates" repository that needs to be enabled -- have you done that?  updating your sources (*sudo aptitude update*...), as laroza mentioned, might also be required before running the update-manager.

---

### Post by koenn on 2008-06-08
> **nick09 said:**
> Download the 32 bit or 64 bit version(look to see if your processor is 64 bit) burn to CD or DVD and I think you should be able to upgrade Ubuntu that way.

But I don't know much so check this page out:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
thanks, but
a/ I insist on doing a network upgrade ; I want to see Ubuntu handle LTS to LTS upgrades, no wipe & install etc.

b/ I did read the upgrade instructions, that's why i expected the update manager "new release available" notification

---

### Post by koenn on 2008-06-08
> **LaRoza said:**
> Did you update the sources?

```

sudo apt-get update && sudo apt-get upgrade

```

yes, did that, first thing.

---

### Post by smartboyathome on 2008-06-08
You need to do alt+f2 and then type
```
gksu "update-manager -d"
```
That is what the instructions say on that upgrade page. ;)

---

### Post by koenn on 2008-06-08
> **smartboyathome said:**
> You need to do alt+f2 and then type
```
gksu "update-manager -d"
```
That is what the instructions say on that upgrade page. ;)

Yes, and that gives me the "Software Properties" saying "your system is up to date" (re 1- ). I can then click "Check" all I want, all I get is is some progress bars, then "system is up to date". 
That's why I tried "server style' with do-release-upgrade.

---

### Post by karrank% on 2008-06-08
> **smartboyathome said:**
> You need to do alt+f2 and then type
```
gksu "update-manager -d"
```
That is what the instructions say on that upgrade page. ;)
Hey, I just did that, and I get this:
  warnings.warn("apt API not stable yet", FutureWarning)
and then an offer to upgrade to hardy thru Software Updates which contradictorily says my system is up-to-date. 
?

---

### Post by koenn on 2008-06-08
> **karrank% said:**
> Hey, I just did that, and I get this:
  warnings.warn("apt API not stable yet", FutureWarning)
and then an offer to upgrade to hardy thru Software Updates which contradictorily says my system is up-to-date. 
?
If you're not yet using Hardy, that's normal.
It's telling you your current system is up to date (no patches/updates needed), but you could upgrade to a newer release of the whole system.

---

### Post by koenn on 2008-06-08
> **koenn said:**
> 
... 

4- so I abort the upgrade, remove ubuntu-desktop, and try again with "do-release-upgrade -d". The upgrade is in progress now.  

So, I'm wondering : did anyone succesfully upgrade from Dapper to Hardy ? 
if so, how ? Or : what am i doing wrong ?

quick show of hands ?

This works, i.e the upgrade completed succesfully. Just install the ubuntu-desktop package separately afterwards, to get some new packages that weren't included in Dappper.


----
Still, this leaves me wondering  : did anyone succesfully upgrade from Dapper to Hardy ? Without the need for such workarounds ?

---

### Post by karrank% on 2008-06-08
[QUOTE=
----
Still, this leaves me wondering  : did anyone succesfully upgrade from Dapper to Hardy ? Without the need for such workarounds ?[/QUOTE]

I don't have enough sensitive info that can't be replicated, so I plan on a clean install.

---

### Post by Sef on 2008-06-08
> I don't have enough sensitive info that can't be replicated, so I plan on a clean install.

1) **Back up** your data before doing a clean install or updating to Hardy Heron.

2) Clean installs tend to be less problematic.  And the alternative cd is problematic than the Live CD.  (Sometimes you need to use the alternate cd to install Ubuntu.)

---

### Post by nicho22 on 2008-06-22
Well, thank you so much for this thread!
I was beginning to wonder what was going on with my installation.
Removing ubuntu-desktop was exactly what fixed it for me.
Now busy actually upgrading from Dapper to Hardy.

Thanks again

nicho

---

### Post by koenn on 2008-06-22
you're welcome

---

### Post by Dale61 on 2008-06-23
> **koenn said:**
> 

So, I'm wondering : did anyone succesfully upgrade from Dapper to Hardy ? 
if so, how ? Or : what am i doing wrong ?

quick show of hands ?

I upgraded from 6.06 to 8.04 successfully back in early April, and I did so as it showed up on Update Manager (new distribution available?).

Not wanting to sound like a broken record as I've mentioned this several times already, but my upgrade took 100 hours as I'm using dial-up.  Everything worked first time, and what minor problems I did have were easily rectified with suggestions from these forums.

---

### Post by BLTicklemonster on 2008-06-27
My daughter brought her laptop by here, and I was going to do a fresh install of hardy, but the cd-rw/dvd won't read the same cd-rw I used before, and her ubuntu was tanked, so I didn't want to mess with it, so I did a fresh install of dapper on it. I then changed the sources.list from dapper to hardy, and did an update then upgrade. It's doing it now.

So how bad is this going to turn out, anyway?

:)


*edit:

just now noticed this:

[https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1](https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1)

so if it doesn't work, I can just do that.

Oh bother.

---

### Post by koenn on 2008-06-28
> **BLTicklemonster said:**
>  I then changed the sources.list from dapper to hardy, and did an update then upgrade. It's doing it now.


A number of packages will be upgraded, but a lot more will be "held back" because they need a newer kernel or because of other dependencies.

You could try apt-get dist-upgrade to get the rest of hardy, but that will most likely result in all sorts of breakage.

---

### Post by BLTicklemonster on 2008-06-28
I had to start over, and Hardy is up and running like a champ. Not sure if the wifi is working, though. It's an Acer 3003lci (or cli, I can't remember) I installed ndiswrapper and ndiswrapper tools, and I see connect to some other connection when I click the network icon, but it says wired, so I don't know.

Here's what I ended up doing

1 Make sure the "dapper-updates" software channel is enabled.
(in synaptic, settings, repositories, check all the boxes, I did :) )

2 Be sure that you have all updates applied before you upgrade.
(I restarted because I wanted to be sure I was doing it right, and it said I needed to)

3 Press Alt-F2 (don't use the terminal) and type 
```
gksu "update-manager"
```
(with the quotation marks)

4 Click the Check button to check for new updates.
5 A message will appear informing you of the availability of the new release. 
6 Click Upgrade.
7 Follow the on-screen instructions. 

and voila.

---

### Post by koenn on 2008-06-28
yeah, that's how it's supposed to go, but for me this only worked on a newly installed Dapper, not on the system I'd been using for 2 years. I never got that "new release available" msg, and when I forced a release-upgrade, it failed.

I suppose some of the software I added over those 2 years, got in the way ...

---

