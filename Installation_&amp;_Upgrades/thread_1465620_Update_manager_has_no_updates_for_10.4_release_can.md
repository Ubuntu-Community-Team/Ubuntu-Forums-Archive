---
title: "Update manager has no updates for 10.4 release candidate?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by AbuMusaabIbn Ali al-Turki on 2010-04-29
Hello,

I have the 10.4 release candidate installed, and I now see that 10.4 is officially released.  When I go to update manager, there are no updates.

When I alt-f2 and type in "update-manager -d"   still no updates.

Is there a reason for this?

---

### Post by recluce on 2010-04-29
> **AbuMusaabIbn Ali al-Turki said:**
> Hello,

I have the 10.4 release candidate installed, and I now see that 10.4 is officially released.  When I go to update manager, there are no updates.

When I alt-f2 and type in "update-manager -d"   still no updates.

Is there a reason for this?

Yes, no changes from RC to release version for most installs. Frankly, at this point in time I didn't expect much in the way of updates anyway - the "barrage" of updates will come after a couple of days or weeks, as bugs get discovered that were missed during the beta-phase.

---

### Post by AbuMusaabIbn Ali al-Turki on 2010-04-29
So would my current version then be considered the same as the official release version?  Without any update?

Meaning that "technically" the official version was released last week in the form of a release candidate?  Meaning that the release candidate won the contest and became the official version?

---

### Post by asmodeus_dhoine on 2010-04-29
Same question here!
Also, how to I see what version of Ubuntu am I running?

---

### Post by recluce on 2010-04-30
The purpose of a Release Candidate is to be RELEASED, unless there are major bugs. IIRC, there were some updates after the RC was released, but non for the last two days or so - as the RC obviously had no major bugs that were fixed for the final release.

So yes, for all purposes, you are running the "final" version - which will also change over time, as updates come along.

If you go to System > Administration > System Monitor and klick the "System" tab, you will see your version of Ubuntu displayed. For older (not updated) Lucid development releases, you will see something like "Ubuntu Development Branch". The final or updated RC reads "Ubuntu 10.04 (Lucid)".

---

### Post by Koala Kid on 2010-04-30
> **asmodeus_dhoine said:**
> Same question here!
Also, how to I see what version of Ubuntu am I running?

```
koala@Mindphaser:~$ cat /etc/issue
Ubuntu 9.10 \n \l
```


```
koala@Mindphaser:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```

---

