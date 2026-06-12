---
title: "No McAfee endpoint splashscreen after natty upgrade"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by kristoffd on 2011-05-24
Hi Community
I'm facing today to a serious issue on my business laptop after upgrading to Natty.
I'm running dual (Ubuntu/Win7) and my windows partition is encrypted with McAfee Endpoint.
Since I had upgraded to Natty, I cannot get anymore the McAfee Splashscreen allowing me to access to my Windows partition.
In regular mode, after booting, I have to enter my passcode (endpoint) then I have the grub menu to select the right OS.
When I'm booting now, I have direct access to grub menu and not able anymore to boot on my Win7 OS (saying wrong encryption key...of course).
i don't know exactly what's happened during the upgrade and trying to sort this out, it's like the upgrade owerwrite (I'm thinking Grub) the MBR.
Does anymore faced to this issue and can help me to fix this, any advices? 

Many thanks Guys

Kristoff

---

### Post by Hedgehog1 on 2011-05-24
There is a new grub that ships with Natty, and I do believe when it overwrite the MBR it replace booting to the McAfee endpoint login screen with the boot to he normal grub menu.

I expect that before this update, the MBR ran McAfee endpoint, and then that chain-loaded to the grub menu.

Do you have the installation disks for McAfee endpoint? Or was it installed by the IT department at work?

***The Hedge***

:KS

---

### Post by kristoffd on 2011-05-24
Hi The Edge

Yes indeed, the chain what Endpoint/Grub/ OS selection
I do not have the endpoint distrib cause it is installed based on self distribution package. (similar to former SMS product).

Is there anyway to rollback to initial grub config and restore MBR 

Thanks

/Kristoff

---

### Post by Hedgehog1 on 2011-05-24
There is no roll back that I am aware of.

---

