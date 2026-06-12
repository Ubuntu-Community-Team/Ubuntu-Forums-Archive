---
title: "100% Remote Upgrade from 10.04 to 12.04 Lubuntu"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by TheFu on 2012-11-29
**Background**
In 2010 I switched Mom from WinXP to Lubuntu 10.04.  Last May I had planned to upgrade her to 12.04 during a visit, but her system would not boot from USB - the method that I'd prepared, so it was delayed.

Over the summer, that Pentium4 box died and was replaced by a Core i7 (THANKS to a generous relative).  We just swapped the old SATA HDD into the new box and all was well. I didn't even have to visit.

This week a request to read PPT and PPTX files was made by Mom. Initially, I assumed that either open or libre office was installed. Neither were and neither would install with a quick - apt-get install. Unmet dependencies all over the place.  After tracking down all the unmet dependencies, I became convinced that the Ubuntu change in Java providers was the culprit. I could be wrong - it doesn't matter, since the Thunderbird PPA for Lucid seems to be gone now too.  

**I've put the update from 10.04 to 12.04 off long enough.**

I remote do updates all the time, but don't do remote system upgrades often where a console isn't possible.  Most systems that I manage have a VNC console under KVM as a fall-back if something bad happens. With the OS running on a physical machine, I don't have that.

**The Real Question**
Can the Lubuntu 10.04 desktop to 12.04 desktop update be completed 100% over the network using just ssh or is there a portion after the first reboot before networking AND ssh is available where questions need to be answered?  Also, a remote desktop will probably not be possible since the NeatNX or FreeNX servers will not be installed as part of the upgrade. Only ssh should be expected, I believe, if I'm lucky.

Is local, non-network, access required during the upgrade?

Mom can wait a few days, but I'd rather not force her to wait until I visit for Xmas to get the 12.04 update.  At least the new box will boot from USB. ;)

Of course, a critical part of this update is having her app settings migrate over.  She uses Firefox, Thunderbird and Quicken (under WINE) with the current box. Reading PPT and PPTX files would be important. Seems that's what the grandkids provide their Xmas lists with now.

**Short-Term Alternatives**

[LIST]
[*]I did suggest that the grandkids "Save As PDF" and provide those files. Grandma was unwilling to make the request.
[*]I offered to convert the PPT files myself.
[*]I could install virtualbox/KVM remotely (assuming the dependencies are met), then installed 12.04 inside it, load LibreOffice and teach her to start the VM and run libreoffice to view the files.  That complexity for an 80+ yr old is probably too much. At least the Core i7 could do it, when the P4 could not.
[*]Setup an NX remote desktop client back to a system here, give her a desktop with LibreOffice and teach her to remote here, to view the files.
[/LIST]
Other options that I'm missing?

---

### Post by Rex Bouwense on 2012-11-29
Unfortunately, you can not upgrade directly from Lubuntu 10.04 to Lubuntu 12.04.  Neither version is a LTS.  You must do a new install or upgrade from 10.04 to 10.10 to 11.04 to 11.10 to 12.04.  In either case back up your files because murphy's law applies.

---

### Post by TheFu on 2012-11-29
> **Rex Bouwense said:**
> Unfortunately, you can not upgrade directly from Lubuntu 10.04 to Lubuntu 12.04.  Neither version is a LTS.  You must do a new install or upgrade from 10.04 to 10.10 to 11.04 to 11.10 to 12.04.  In either case back up your files because murphy's law applies.

Are you sure these aren't LTS?  I think the direct upgrade is possible, since I'm seeing this when I ssh into the box:
```

RSA host key for IP address 'xxx.xxx.xx.x' not in list of known hosts.
Linux moms-pc 2.6.32-45-generic #99-Ubuntu SMP Tue Oct 16 16:31:11 UTC 2012 i686 GNU/Linux
Ubuntu 10.04.4 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

New release 'precise' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Thu Nov 29 08:28:35 2012 from xxx.xxx.xxx.xxx
```

My real concern is whether the upgrade can be performed remotely without a console available.

---

### Post by dannyboy79 on 2012-11-29
don't listen to Rex, he is misinformed! Both 10.04 and 12.04 are LTS releases. What ssh is informing you is correct. It can be done over ssh,  however, might I suggest the other alternatives just in case something goes wrong. If the upgrade fails in anyway when the box is restarted and ssh isn't started (for whatever reason) you would surely have to visit her to get it back up and running.

If I were you, simplist thing would be to have her email you the files, you convert them to pdf and send them back. I am confused why you can't get openoffice installed though. the lucid lynx proposed repo should ahve open office 3.2.1 in it.

---

### Post by Rex Bouwense on 2012-11-29
I beg to differ.  There is no LTS in Lubuntu as of yet.  If the OP is talking about Lubuntu as he has written, then an upgrade cannot be made that way.  If Ubuntu 10.04 and Ubuntu 12.04 were meant then it can be done.

---

### Post by dannyboy79 on 2012-11-30
he may have installed ubuntu and then LXDE on top of it. SSH clearly shows an upgrade to precise is available.

---

