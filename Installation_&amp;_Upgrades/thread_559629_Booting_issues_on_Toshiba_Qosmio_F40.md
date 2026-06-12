---
title: "Booting issues on Toshiba Qosmio F40"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by dgtldaydrmr on 2007-09-25
perhaps a linux guru here has some insight to a non ubuntu issue...

at first boot after installing slackware it would hang at...

cs: IO port probe 0x800-0x80f:


I then tried to boot with option acpi=off
It now hangs at...

io scheduler cfq registered (default)


I could go back to my ubuntu partition (mind you ubuntu worked pretty much perfectly after install)  but I need to know what is causing this to happen or it will drive me mad.

I would almost prefer some hints to get me pointed in the right direction on how to diagnose whats going on to determine where the issue is.

Any help would be greatly appreciated.

I tried other forums more specific to slackware but the response rate to questions is like 200:1

---

### Post by ddrichardson on 2007-09-25
> **dgtldaydrmr said:**
> I tried other forums more specific to slackware but the response rate to questions is like 200:1
In slackware linux we ask *you *questions. ;-)

You could start [here]("http://www.slax.org/forum/viewtopic.php?=&p=76495"). You may also wish to look into SELinux as there are suggestions it's part of the problem. Disabling hotplug may also be of help.

---

### Post by dgtldaydrmr on 2007-09-25
Perfect! 

Thank you.

---

