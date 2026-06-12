---
title: "Ubuntu 11.04 Upgrade Overwrote My Truecrypt MBR"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by user2037 on 2011-06-24
It appears the upgrade to 11.04 has overwritten my Truecrypt MBR. And since the Truecrypt partition uses system encryption Ubuntu can not even mount it.

Does Ubuntu installation or upgrade make a backup of the boot sector anywhere?

---

### Post by YesWeCan on 2011-06-25
> **user2037 said:**
> It appears the upgrade to 11.04 has overwritten my Truecrypt MBR. And since the Truecrypt partition uses system encryption Ubuntu can not even mount it.

Does Ubuntu installation or upgrade make a backup of the boot sector anywhere?
I don't think so, but it darn well ought to.

---

### Post by oldfred on 2011-06-27
I would suggest filing a bug report or check if one exists and add your problem to it. The more that report an issue the sooner a correction may happen.

bug reports info on how to do:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
Check bugs
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

You do have to also sign up for launchpad. Many of us just use or same userID as here, but it is totally separate.

---

### Post by YesWeCan on 2011-06-27
@oldfred: Good idea.
The more I think about this the more obvious it seems to me that the installer should always create a backcup copy of the MBR and maybe all 64 sectors for recovery purposes. It also seem obvious to me that the Ubuntu live CD should have a menu option to restore a standard MBR. Lots of folks would benefit.

---

