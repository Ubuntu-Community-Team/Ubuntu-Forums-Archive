---
title: "Upgrade problems; is this a dead end?"
date: 2019-04-22
forum: Installation &amp; Upgrades
---

### Post by simple_impulse on 2019-04-22
I'm upgrading one of my PCs, old 14.04 LTS Desktop PC to 16.04 LTS with command:

sudo do-release-upgrade

I get error(s):

Calculating the changes
Could not calculate the upgrade 
An unresolvable problem occurred while calculating the upgrade.

When I check:

grep Broken /var/log/dist-upgrade/apt.log | wc -l
451

So, it seems I have more than four hundred broken packages to check out. Not feasible, because they most likely have even more dependencies.

This PC contains several quite important environments. If need to be it stays with 14.04 LTS even after End Of Life. But I'd much prefer upgrade. I just don't see how.

What *realistic* possibilities I have?

---

### Post by TheFu on 2019-04-22
do-release-upgrade is a dangerous thing.

Make a _know-you-can-restore_ backup.  Don't ever do anything like this without doing that first.

All Linux systems need to be maintained. That means patching weekly, perhaps monthly. Any longer periods can easily result in dependency issues.  So the first step, and you need to do this before the 14.04 repos disappear, AFTER you make that perfect backup, is to perform a full patch session.
```

sudo apt-get update
sudo apt-get full-upgrade
```

Fix any issues as they come up. DO NOT move forward until all the issues are resolved. Reboot after the patching as needed.  When you run the "full-upgrade" and see 
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Then you are done and can make another know-you-can-restore-backup.

If you've manually installed .deb package, those are probably breaking all the dependencies. They will need to be removed.

Then try the do-release-upgrade step again.

Running an unsupported OS on a LAN that connects to the internet is asked to be hacked.  Lock down all network access that you can.  DO NOT let this be an internet server. You will be hacked.

I think Canonical is offering 5 more years of support for 14.04 servers. You probably want to buy that for anything so critical. There will be kernel security issues that need addressing.  If management refused to buy that support, I'd get something in writing from a board member, so they can't claim nobody told them. Craft a few paragraphs about the system, age, services it offers, and how much revenue those systems provide or how these critical services being unavailable will impact employees and/or customers.  Is $200/yr (my guess, IDK the real costs) really worth all that risk?  Often, just showing that to your boss will magically get the money or the time to perform the migration.  Plan on 5-10 attempts. Complex systems seldom migrate easily.  The do-release-upgrade process would likely break some of those services too.  Apache is completely different versions now, for example.  Same for php, mysql, nginx, and most other web-app languages.

I migrated a Zimbra server off 14.04 last week.  Painful.  Plus, Zimbra doesn't have an 18.04 release at this point, so I get to do it again in 2 yrs.  Ack!

But honestly, it is probably best to move to 18.04 and migrate all the services ASAP, even if you have to take the pain now.  It won't get any better 4 yrs from now, unless you plan to retire or change jobs.

---

### Post by simple_impulse on 2019-04-22
Hi TheFu,

this system in question is up-to-date (apt-get update and apt-get upgrade, my system does not understand full-upgrade?). Full backup was done yesterday. 

The release upgrade just does not work.

(I'm updating *another* PC from 14.04 LTS to 16.04 LTS as I write this and it is progressing well, so I guess this "problem PC" just has too many experimental debs or something.)

If someone knows some trick which helps is cases like this, I'm *very* interested.

---

### Post by TheFu on 2019-04-22
Try **sudo apt-get dist-upgrade** that's the deprecated version of "full-upgrade".

If you've installed any .deb files, those are what is preventing the release to move forward, most likely.  Since 14.04, many of those .deb packages have probably become part of the normal release, so you'll be using repo versions anyway.  Any "held dependencies" in the output?

Any funky PPAs in /etc/apt/sources.list.d/ ???   Those config files get disabled by the do-release-upgrade process, but left in place, so you can find the newer versions, if needed, post-update to the new release. Most of the time, a new LTS won't need PPA versions for most tools, but it depends on the specific purpose of the server.  I use the PPA for apertium to do some language translations even after moving from 14.04 to 16.04, for example.

There is no magic answer.

I'd make a list of installed packages - **dpkg --get-selections** or better, **apt-mark showmanual**, then I'd script something to look for unmet/failed/held back dependencies using whatever the equiv command to **sudo apt policy** is on 14.04.  At least then the migration to a newer LTS won't be about hunting down package names with the list.

If you do migrate to newer hardware and there are multiple systems on this single machine inside a single OS instance, might want to decouple those into separate containers or VMs.  It is much easier to upgrade a system running only Apache than it is to upgrade a system running Apache, Nginx, HA-Proxy, Mysql, Postgress, and 5 other services.  We all know this.

OS migrations are a pain.

---

### Post by simple_impulse on 2019-04-22
> **TheFu said:**
> Try **sudo apt-get dist-upgrade** that's the deprecated version of "full-upgrade".

All upgrade attempts end up the same way. 

I think this is not possible to solve manually listing the dependencies, it will probably only end up in more complexities.

I think I need to find another solution or leave the system in this (unsupported) state. Pity.

I will check out later, if anyone has some unorthodox solution. :D

---

### Post by rsteinmetz70112 on 2019-04-22
Have you tried:
```
# apt install -f
# dpkg --configure -a
```

The first will try to fix any broken packages and the second should check all dependencies.

If you get errors on the first you might try reinstalling any packages mentioned before running the second. Keep at it until yuo don't get any errors..

```
# apt install --reinstall  <package name>
```

If you get both to run without errors you can try doing the release-upgrade.

Also if you don't mind tell us exactly what happens when you tried to run ```
$ do-release-upgrade
```

As a final thought is the system set to upgrade to LTS versions only?

---

### Post by simple_impulse on 2019-04-22
Hi  				 				 					 						 	[COLOR=#000000]rsteinmetz70112[/COLOR],

apt install -f does not report problems, except some "no longer required".

dpkg --configure -a gives warnings for some typos from two packages (arch in one and rev number in other).

So, probably not the cause, but of course sheer mass of packages may be the problem. Heavily used system with exotic packages.

---

### Post by rsteinmetz70112 on 2019-04-22
I would try to resolve the two errors with dpkg and determine if they really are typos of if the wrong package is installed.

Do you have ppas or other alternate repositories configured?
Were any of those exotic packages installed manually (not a .debs)?

Either of the above makes it more likely that they are causing the problem.

---

### Post by simple_impulse on 2019-04-22
Unfortunately, yes, plenty of PPA:s and manually installed debs. 

Probably this is unsolvable. It may well be that the Ubuntu upgrade system gets confused with all these packages. However, updates before system upgrade always worked as they should.

---

### Post by rsteinmetz70112 on 2019-04-23
I am in the midst of upgrading 7 production systems. Most have gone fairly well, but I tend to stay close to the Ubuntu packages and only use something else when I can't avoid it. Of the 7 - 4 have been upgraded. I had some problems with one due to an old package not being removed. I am stuck on one where the upgrade blows up after the upgrade scripts are downloaded and start to run. I haven't been able to pinpoint the problem yet so I'm trying to participate in threads which have to do with do-release-upgrade. The remaining two systems seem to be able to run the release upgrade but I'm holding off until I solve the current issue. Unfortunately do-release-upgrade doesn't seem to log errors very well.

---

