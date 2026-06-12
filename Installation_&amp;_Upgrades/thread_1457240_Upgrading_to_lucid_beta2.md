---
title: "Upgrading to lucid beta2"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by adante on 2010-04-18
Hi,

Could someone please advise me how to upgrade to lucid beta2 from the command line.

When I try 'sudo do-release-upgrade' I get this:

> 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
[100%] 86.3kB/s 0s
Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled

Some third party entries in your sources.list were disabled. You can
re-enable them after the upgrade with the 'software-properties' tool
or your package manager.

Done downloading

Checking package manager
Reading package lists: Doneucid/main Packages: 90 ed Packages: 77
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the
'update-manager' package and include the files in
/var/log/dist-upgrade/ in the bug report.


Restoring original system state

Aborting
Reading package lists: Donem lucid-updates/restricted Packages: 94
Reading state information: Done
Reading state information: Done
Reading state information: Done


The first 2 don't apply as I'm on 9.10. I can't really remember if I have installed any unofficial software packages. I guess so. Is there a way to find out more information on this?

---

### Post by mbobak on 2010-04-18
Actually, the first applies to you, as Lucid Beta 2 is a pre-release version of Ubuntu.

As to determining if you have any third-party packages, have look at the various sources.list in /etc/apt/sources.list.d

Hope that helps,

-Mark

---

### Post by Sef on 2010-04-18
> The first 2 don't apply as I'm on 9.10. I can't really remember if I  have installed any unofficial software packages. I guess so. Is there a  way to find out more information on this? 	

Have you installed anything proprietary, like NVidia drivers?

---

### Post by adante on 2010-04-18
> **mbobak said:**
> Actually, the first applies to you, as Lucid Beta 2 is a pre-release version of Ubuntu.

As to determining if you have any third-party packages, have look at the various sources.list in /etc/apt/sources.list.d

Hope that helps,

-Mark

Oh. I misread that. I assumed that as people were telling me to use this to upgrade to beta 2, I'd be able to use it to upgrade to b2. My bad! What should I be using as an alternative?

> **Sef said:**
> Have you installed anything proprietary, like NVidia drivers?

Nothing which comes to mind. Not nvidia drivers as this has an intel video chipset.

---

