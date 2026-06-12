---
title: "tzdata drama"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by wmblowers on 2007-10-20
Did the version upgrade from fiesty to gutsy the other day, all went well except for the tzdata problem.  Got that sorted out (by switching to the Europe/Berlin timezone, then doing   'sudo dpkg --configure -a' and it fixed the package.  It was scary because the upgrade aborted because of this and said that my computer might be broken, but it did reboot OK into Gutsy allowing me to make the changes.

Anyway, this AM there was a pushed update for tzdata, and it wouldn't install; the first time in Ubuntu I've ever had this happen for a push.  Changed the time zone again, and it loaded after changing the time zone.  Also, the update program wanted to upgrade my ops sys to Gutsy... kind of odd since I'm already on the release version of Gutsy.

Anyway, just those minor things, everything going well so far, just thought I'd post to see if anyone else got this.

WLB  :>)

---

### Post by lightstream on 2007-10-20
I did have a problem with tzdata, but it didn't affect the installation. In fact it may be a bit different to what you're referring to - my problem was that, after installation, tzdata appeared as an available update. However Synaptic couldn't download it (404 error). The problem was fixed the following day, and had no effect on my time or anything.

---

### Post by halfB on 2007-10-21
My tzdata upgrade mess up happened with update from gutsy rc.  While I am able to boot ok I still have problems with timezone and other time related settings and cannot install java6.  Will post problems later this week to see if any buntu wizards can help me.  Too afraid to upgrade my other 2 kubuntu machines.
Eric

---

### Post by loconet on 2007-10-21
What's the word on this? an available tzdata update showed up this morning but when i tried to apply it it warned me that it could not be authenticated.

---

### Post by drawman on 2007-10-31
Every time I try to upgrade or install a new package I get this:

> E: tzdata: subprocess post-installation script returned error exit status 10

E: util-linux: dependency problems - leaving unconfigured

I understand that problem is being worked on by some of the finest and kindest minds available.

---

### Post by speckman on 2007-11-04
i'm getting that error too, when trying to use synaptic or apt-get

---

### Post by kf4tqj on 2007-11-09
After a fresh install of Gutsy the update manager said that I had 29.6 meg of updates. When It tried to install them I got "E: tzdata: subprocess post-installation script returned error exit status 10" Now it won't install any of the updates that it downloaded. It just keeps telling me that I've got 22 updates.
Any ideas how I fix this?

---

### Post by santiagoward2000 on 2007-11-20
OK, I've been using Gusty since it came out (about 1 month) and hadn't experienced this problem. But today, I got a tzdata update. I tried to install it and I got:
> E: tzdata: subprocess post-installation script returned error exit status 10
Now I have other updates, but I can't install them :(
I hope this is just temporary and will soon be fixed!

---

### Post by evillan on 2007-11-20
> **santiagoward2000 said:**
> OK, I've been using Gusty since it came out (about 1 month) and hadn't experienced this problem. But today, I got a tzdata update. I tried to install it and I got:

Now I have other updates, but I can't install them :(
I hope this is just temporary and will soon be fixed!

I have the same problem. If anybody figured out how to fix this, please post the solution

---

### Post by ben::zen on 2007-11-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/153013](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/153013) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've gotten the same problems... 
```

Setting up tzdata (2007i-0ubuntu0.7.10)
dpkg: error processing tzdata (--configure):
   subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
   tzdata
```
I've run this several times, to no avail. Anyone have a hint or idea? I'm baffled, but here's more output (i found the command after googling for this stuff...
```

DEBCONF_DEBUG=developer sudo dpkg --configure tzdata
Setting up tzdata (2007i-0ubuntu0.7.10) ...
debconf (developer): frontend started
debconf (developer): frontend running, package name is tzdata
debconf (developer): starting /var/lib/dpkg/info/tzdata.config configure 2007h-1
debconf (developer): <-- VERSION 2.0
debconf (developer): --> 0 2.0
debconf (developer): <-- CAPB backup
debconf (developer): --> 0 multiselect escape backup
debconf (developer): <-- FSET tzdata/Areas seen true
debconf (developer): --> 0 true
debconf (developer): <-- FSET tzdata/Zones/America/North_Dakota seen true
debconf (developer): --> 10 tzdata/Zones/America/North_Dakota doesn't exist
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata

```
I'm in MN, but I use ND since there aren't any Minnesota locations...

EDIT:
The London hack used in the Launchpad link does work.

---

### Post by santiagoward2000 on 2007-11-20
> **ben::zen said:**
> The London hack used in the Launchpad link does work.

Hey! Thanks! It did work!

---

### Post by jimwhitend on 2007-11-21
I'm in MN, but I use ND since there aren't any Minnesota locations...

EDIT:
The London hack used in the Launchpad link does work.[/QUOTE]

I had identical problem and, following wmblowers lead, I changed the timezone from America/North_Dakota/New Salem to America/Winnipeg and the tzdata update package installed just fine, as did the others that had been blocked by the tzdata error.  Seems odd that some timezone settings don't work, but it also seems odd that there are so many timezone settings for my timezone.

---

### Post by evillan on 2007-11-21
I changed my time zone (etc/timezone) from "User defined" to "Europe/Berlin", that worked for me.

---

### Post by bastidrazor on 2007-11-21
Oddly enough setting your TimeZone to Europe/London then running sudo dpkg-reconfigure tzdata and setting it up with your time zone works. i just ran it.. tzdata now gives no errors.

---

### Post by ehcualp on 2007-11-21
i had this problem too and changing the time to london time, then installing the updates fixed it.
random. i wonder why it does this..

---

### Post by PatrynXX on 2007-11-28
Yeah this developed a few weeks ago, I haven't had time to explore it.  I can't upgrade anything because of this tzdata problem.

This is all I get.
E: tzdata: subprocess post-installation script returned error exit status 10  :confused:

---

### Post by Elotero on 2007-12-01
changing to london doesnt help for me.. or berlin.. i ran this:

sudo dpkg-reconfigure tzdata

and got this:

/usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed

---

### Post by Elotero on 2007-12-03
NVM.. it works..

---

### Post by kuantum_fizax on 2007-12-09
Hey, I get 

/usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed

just like the last post. How do you fix this?

---

### Post by trtr on 2007-12-09
I used aptitude to fix tzdata install and update the rest, because then there were others errors :(

---

### Post by J-Morris on 2007-12-11
I'm having the same problem as everyone else. Is this a kde thing? I'm using kubuntu on a HP laptop, what are other people using? is this a case of "you shouldn't be running ubuntu on your HP laptop"?

---

### Post by txfwmr1 on 2007-12-11
I'm a newbie to Linux and Ubuntu.  The Londaon hack on the time zone worked to resolve the tzdata error.  For some reason the time zone was blanked out.  After switching it to Londan and then back to my time zone.  I was able to do updates again.  Spent about 2 hours to resolve this.  Good experience though.  i am liking Linux and particularly, Ubuntu more and more.

---

