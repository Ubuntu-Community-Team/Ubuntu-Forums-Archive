---
title: "failed to wpawn udevtrigger post-post proccess: unable to exectue: no such file or di"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by highspider on 2011-03-02
failed to spawn udevtrigger post-post proccess: unable to exectue: no such file or dir
this sucks because I can't even use tty1


I was in between an upgrade from 10.04 up to 10.10. and killed it good.  at frist it failed with the 
  unable to mount / press S for skip or M for Manuel error. I could only s and mount read only root file system. which seems kind of pointless as far as not being able to right or fix anythihng 

I rebuilt the fstab via live cd 10.04 to skip fsck (0 0) on drive and blocked out all drives execept / and proc.
   they are correct UUID and everything else.

I think because it was in the middle of upgrading It would be easier to reinstall. 

MAIN QUESTION
 Is there a repair option on live cd 10.10 or a good way to rebuild with out data loss.

---

### Post by highspider on 2011-03-02
solved.

Reinstalling Ubuntu 10.10 does not destroy anything except your extra packages.
It's not bad at all for config files and stuff.

step 1) back up data. (was not needed)
step 2) reinstall but do not format the drive
step 3) give the same exact user name as your old user name (password can be different)
step 4) after install. reinstall the exact the same extra packages you had.

it will load with your old home folder intact and all-most config match.
  I had to add freebsd to fstab but \etc\network\interfaces and \etc\resolv.conf where fine.
 I had reinstall comiz-fusion and cairo and screenlets but all my original con fig files where intact.
   (i did have to re-enable desktop effects and turn the sphere on yet the config files where all there so it even had my last pictures where all set.
  My firefox history is even the same and all links aka /home/user/.mozilla


I heard a reinstall would kill most stuff, even heard new ubuntu vers would have repair because of data loss. but they where wrong!

---

