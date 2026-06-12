---
title: "My system won't boot after upgrading from 14.04 to 15.04."
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by Mate_Timar on 2015-10-25
It sends the following error message:

starting version 219
Target filesystem doesn't have requested /sbin/init.
/bin/sh: 0: Can't open splash
[      5.668912] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00007f00
and so on....

Please help me fix my system, or at least retrieve my data on the hard drive.
Thank you.

---

### Post by kansasnoob on 2015-10-25
What method did you use to upgrade? I ask because it's not possible using the update-manager (aka: software updater) to upgrade from 14.04 to 15.04. It is possible however to upgrade from 14.10 to 15.04 or 15.04 to 15.10 using the update-manager. It's also possible to perform upgrades using the live DVD/USB if certain criteria are met. We just need to know which method you used.

Also, do you have an Ubuntu live DVD or live USB? It'll be needed (or at least helpful) for either repairing your current system or backing up your data before reinstalling.

Also, click on the Report Post button in the lower left hand corner of your original post and ask that this thread be moved to Installation & Upgrades:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

Folks with a lot of installation and upgrade experience tend to frequent that section of the forums, and the mods don't mind being asked to move a thread :D

---

### Post by Mate_Timar on 2015-10-26
Hi kansasnoob.

I reported my post (to move it to Intallation and Upgrades).

I used the Software Updater. I had Ubuntu 14.04 LTS, and it offered me an upgrade to 15.04 straightaway. 

I couldn't find out what's the problem, so yesterday I grabbed my data and reinstalled my system.

---

### Post by howefield on 2015-10-26
Thread moved to the *Installation & Upgrades*"" forum.

---

### Post by kansasnoob on 2015-10-26
> **Mate_Timar said:**
> Hi kansasnoob.

I reported my post (to move it to Intallation and Upgrades).

I used the Software Updater. I had Ubuntu 14.04 LTS, and it offered me an upgrade to 15.04 straightaway. 

I couldn't find out what's the problem, so yesterday I grabbed my data and reinstalled my system.

I wonder if you'd changed the software sources to notify you of any new version rather than leaving it set to notify of only LTS versions:

[ATTACH=CONFIG]265171[/ATTACH]

In that case the update-manager would offer an upgrade to 14.10 if it weren't EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

It shouldn't do that though, I checked on my system using update-manager -d and it does offer the upgrade to 14.10 but maybe maybe the -d overrides the smart protocol of avoiding EOL upgrades:

[ATTACH=CONFIG]265172[/ATTACH]

Regardless that test confirms that the update-manager will not offer an upgrade from 14.04 to 15.04. I guess since you reinstalled we'll never know.

---

### Post by kansasnoob on 2015-10-28
**Mate_Timar** was right. I tested this myself and Trusty is now offering a direct upgrade to Vivid. I think this is incorrect so I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510920](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510920)

---

### Post by kansasnoob on 2015-10-28
Turns out this was intentional:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

So I guess when 15.04 reaches EOL 14.04 will offer a 14.04 -> 15.10 upgrade as well.

---

### Post by John_LaRocque on 2015-11-24
I have the exact same problem - upgraded from 14.04 to 15.04 with update-manager and I am unable to boot in any mode.  Fortunately I have nothing critical on that partition and I can use my windows partition for the moment but I've never had a problem upgrading before.

---

