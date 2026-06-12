---
title: "Boot fails after upgrading from 10.10 to 11.10"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2011-10-17
My sister just upgraded her system from 10.10 to 11.10 from a Live CD because her system had networking problems that went away when we tried the Live CD.  (not hardware)

The first time she rebooted after the upgrade, we got two failure reports:

Fallback graphic devices
Auto crash report generation

and it hung until I used a three-finger-salute to reboot.

The second time, there were two different failures:

Pulseaudio configuration for pre user sessions
System V runlevel comapatibility

The last step completed was:

Starting Light DM Display Manager

What do we do next?

---

### Post by sideburns on 2011-10-17
More information: we just went back and checked and it's farther along in the boot process than it was before.  It looks like it's still trying to boot, it's just going exceptionally slowly.  Still, this isn't how it's supposed to work, and on 10.10 it booted quite quickly.  In fact, when we tested it with a Live CD, it booted off of the CD in a reasonable length of time.  If and when it comes up, what can we do to get things working the way they should?

---

### Post by foresthill on 2011-10-17
Could you list some hardware info?

---

### Post by sideburns on 2011-10-17
Since my last post, we've completely reinstalled 11.10 with the exact same results, showing that whatever's hanging isn't caused by a failed upgrade.  It still gets to checking the battery status (on a desktop, btw) with one or two fairly random fails, then hangs.

As far as giving hardware info, I'd be glad to if you'll tell me what you want to know.  If nothing else, we can always reboot from the Live CD, because that's the only way the computer boots now.  (Rescue mode is remarkably useless for something like this.)

---

### Post by sideburns on 2011-10-18
The computer is now hanging with these messages:

No Caching mode page present
Assuming drive cache: write through

repeated three times.  Checking with my hardware guru, the drive's bad and needs replacing.  This may be why she was having trouble in the first place.  Consider this thread solved.

---

### Post by sideburns on 2011-11-07
As it turns out, the hard drive wasn't the issue.  We replaced it, reinstalled from scratch and got the same result.  My sister ended up taking it to the IT dept of the community college she's attending and they found the issue in under half an hour.

This HP computer has both an onboard video card and an auxiliary card, and the latter card had gone bad.  Disconnecting it cleared everything up.

---

