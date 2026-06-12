---
title: "Ubuntu Upgrade 11.10 from 10.04 with minimum disk space and partition limitation"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by overcast on 2011-11-07
I have installed 10.04 on laptop under 8GB partition. 4GB is taken by the installer and remaining 4gb requires manual or auto-mount during startup. I don't know how that happened. But i want to merge the remaining 4GB so that i can upgrade to the latest version of ubuntu. I don't have much high speed connection so downloading 800+MB iso will take time and upgrading from one version to another seems to be the only way left for now. 

So my questions are - is it possible to merge that 4gb remained partition to the boot partition? if so how ?

another question is as i'm on 10.04, how much space will it take to reach 11.10 if i do the version by version upgrade ?

---

### Post by MuppetandChums on 2011-11-07
Yes...I wish I'd known this.

I was on 10.04 tried to get to 11.10.
The dual boot machine failed somewhere at 2942MB half way thru 11.04. No warning.

Don't bother with grub rescue.

I'm back on only Win7 after FIXMBR. Should've left 10.04 alone

---

### Post by Mark Phelps on 2011-11-07
Upgrading step-by-step from 10.04 to 10.10, 11.04, and then to 11.10 is fraught with problems, especially since 11.10 introduces a new version of Gnome.

If you have an external drive, the first thing you should do is install Clonezilla and use it to image off your existing 10.04 install to that external drive. Since Ubuntu had no System Restore or Roll-back capabilities, if the upgrade(s) go bad, you will need this backup to restore 10.04.  There's no way to remove the updates and go back without having a backup.

---

