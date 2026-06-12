---
title: "automatic upgrade to 11.04 fails"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by damaru_inc on 2011-05-01
Hi,

The Update Manager has tried to upgrade me to version 11 three times now, and fails each time.

First I get a warning, that probably isn't important:
"Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager."

After the upgrade I get this:

"Could not install the upgrades
The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Upgrade complete
The upgrade has completed but there were errors during the upgrade process."

The console has about six messages similar to this, all complaining about the vnc-e package:

"warning, in file '/var/lib/dpkg/available' near line 10992 package 'vnc-e':
error in Version string '4.4.3_r16583': invalid character in version number"

Any hints would be really appreciated!

thanks!

---

### Post by Rat2000 on 2011-05-01
I have the same exact problem except it says it about the package "compiz-switch" which I don't have (I had it years back).

After reboot I only get terminal access and I'm stuck. I guess I'm up for fresh install and I'm not looking forward to it.

---

### Post by Drewvt on 2011-05-08
My experience with previous upgrades: when I tried to go from 8 to 9 through the automatic upgrade process, everything went corrupt. Fresh install.

When I tried to go from 9 to 10 through same (because I am apparently a slow learner, but in my defence it was on a newer, faster computer), it got stuck halfway and I ended up with the same 9 OS but with a completely dead update manager. Fresh install.

Not trying that again, I can tell you that. Apparently for an unlucky few, automatic upgrade just never works.

---

### Post by DaMonsterMonster on 2011-05-08
> **Rat2000 said:**
> I have the same exact problem except it says it about the package "compiz-switch" which I don't have (I had it years back).

After reboot I only get terminal access and I'm stuck. I guess I'm up for fresh install and I'm not looking forward to it.
thats what happens to me on my mac in vmware fusion.....

---

### Post by mörgæs on 2011-05-08
> **Drewvt said:**
> Apparently for an unlucky few, automatic upgrade just never works.

Very true. I believe that online upgrade is the single biggest source for anger among Ubuntu users.


Just get into the habit of reinstalling. After having done it a few times, it takes maximum one hour.

---

### Post by Rat2000 on 2011-05-09
I've been upgrading Ubuntu since... 2003? 2004? Can't remember.

Oh well, I bit the bullet, backed up my home and did a from-the-CD upgrade (I didn't even know that existed). It reinstalls Ubuntu fresh but doesn't deletes the data so I only had to reinstall my apps.


That I said, I always had one small problem or another after each upgrade: fstab will be weird, no sound, compiz would be wonky, that sort of thing. I know how I'll be upgraded coming October.

---

