---
title: "dist upgrade hang"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by chadmichael on 2008-07-15
I was upgrading, via the upgrade manager, to 8.04.  The upgrade hung, became unresponsive, etc. during the installation.  

I have since read that the recommended process is to upgrade incrementally, form 6.06.  

Too late for that I suppose.

My question is what are my options.  Kill the machine?  Seems like the only one, but I suspect I can get a terminal and kill the upgrade process, etc.  But what are teh consequences.

I need a recommended path of escape.  

Thanks, 
Chad

---

### Post by PmDematagoda on 2008-07-15
Were you upgrading from Ubuntu 6.06 to Ubuntu 8.04?

---

### Post by chadmichael on 2008-07-15
yes.  I think so.  The machine is not here with me at the moment, but I'm pretty sure on that.  

It's six something at  least. . .

---

### Post by PmDematagoda on 2008-07-15
> **chadmichael said:**
> yes.  I think so.  The machine is not here with me at the moment, but I'm pretty sure on that.  

It's six something at  least. . .

If it is Ubuntu 6.06 then you do have the ability to directly upgrade to Ubuntu 8.04, perhaps you may need to do that through the command line to get the best results, the upgrade can be done this way:-
> Network upgrade for Ubuntu servers (recommended)

If you run an Ubuntu server, you should use the new server upgrade system.

   1. enable the "dapper-updates" repository
   2. install the new "update-manager-core" package - dependencies include python-apt, python-gnupginterface and python2.4-apt.
   3. run "sudo do-release-upgrade -p" in a terminal window The -p flag is needed because hardy is not being offered as a lts-upgrade until 8.04.1.
   4. follow the steps on the terminal window 
as given [here]("https://help.ubuntu.com/community/HardyUpgrades").

---

### Post by chadmichael on 2008-07-15
But my real question is whether I can simply reboot from the hung dist-upgrade without incurring any damage . . . Can I just flip the switch?

---

### Post by PmDematagoda on 2008-07-15
> **chadmichael said:**
> But my real question is whether I can simply reboot from the hung dist-upgrade without incurring any damage . . . Can I just flip the switch?

If it does not respond after a certain amount of time, that may be what you have to do.

---

