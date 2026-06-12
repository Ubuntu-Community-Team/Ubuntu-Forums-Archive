---
title: "Notifications to upgrade from 12.04 to 14.04.1 LTS"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by pablinsfc on 2014-07-28
Hi,

I'm trying to upgrade my Ubuntu 12.04 LTS Desktop to 14.04 version, but the system doesn't notify me that is possible in the package manager (Muon). I've read that the 12.04 systems wont be notified until the release of the 14.04.1 version of Ubuntu, but this version is available from last week.

Do you have any information about that?

Thank you.

---

### Post by ibjsb4 on 2014-07-28
If 'sudo do-release-upgrade' will not work, then try the d-switch.  This will not take you to 14.10 as it is not possible to jump pass 14o4 in your case.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

---

### Post by kansasnoob on 2014-07-28
I discovered a nasty bug while performing iso/upgrade testing:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

Since I didn't discover and file it until the 23rd Canonical apparently delayed the automated notifications for Precise -> Trusty release upgrades until they get that sorted. But based on my own testing it only effects Precise users who applied the Trusty [HWE upgrade]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") earlier. To see if you're effected run the command:

```
uname -r
```

**If that shows you're already running the 3.13 series kernel then the upgrade is known to fail.**

If you're not effected maybe you have Software Sources set wrong? Run the command:

```
grep Prompt= /etc/update-manager/release-upgrades
```

That should show *Prompt=lts* if the settings are correct.

I think the safest thing to do is wait for Canonical to sort things out, I know they are working on it :)

---

### Post by cscj01 on 2014-07-30
Launchpad shows Fix Released for Bug 1347964 with a Milestone of 14.04.2.  Does this mean that those of us on 12.04.4 will have to wait until 14.04.2 is released before we are notified of the LTS release upgrade?

---

