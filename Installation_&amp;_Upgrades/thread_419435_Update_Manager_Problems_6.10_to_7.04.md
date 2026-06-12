---
title: "Update Manager Problems 6.10 to 7.04"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by jbowman86 on 2007-04-23
Hi Guys,

I just upgraded from 6.06 to 6.10 but am now trying to use the update manager to get 7.04 via the upgrade distros button. it runs through for a while but then returns this error.

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Can ANybody help me upgrade or at least show me how to report the bug. thanks

---

### Post by benmoreassynt on 2007-04-24
Same problem. Help appreciated.

First time I tried to download. It was very slow, and eventually stopped completely. I've most recently tried to upgrade from the alternative install CD, as suggested on the download page, but still an error.

Here's extracts from the logs where errors seem to be mentioned - however I think both these may be earlier attempts:

WARNING: can't read '/usr/share/update-manager/mirrors.cfg'

WARNING: Failed to read mirror file

mirrors.cfg is present, so I don't know why it would be unreadable when running as root.

---

### Post by Liolikas on 2007-04-27
Same problem.

An unresolvable problem occurred while calculating the upgrade.

---

### Post by Liolikas on 2007-04-27
Now I checked main.log file and last line may be interesting:
2007-04-28 time,596 ERROR DistUpgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."

---

### Post by benmoreassynt on 2007-04-27
My upgrade worked in the end. How I got it to work was by logging into Gnome (I use Kubuntu usually) and using the Gnome update manager. Still did not work the 1st time, 2nd time it worked. The download was very slow (like 7KB a second over a fast connection) , but once done, the upgrade happened as it should.
 
Are the mirrors being used overloaded? I'm using a Canadian mirror.

---

### Post by zvacet on 2007-04-28
I don´ know if this help but try 

```
sudo aptitude update
```

to be sure your OS is up-to-date.Nothing else cross my mind.

---

### Post by pangos on 2007-04-28
I also have update problems. My system was fully updated with all my favourite packages when I tried to upgrade to Fiesty Fawn. Now the uprade always fails. and I don't have the option of adding packages.

---

### Post by Liolikas on 2007-04-29
After 14 hours of fun I updated my Ubuntu.
Gnome do not woking any more evrything else jus fine. :popcorn:

---

