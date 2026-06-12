---
title: "Upgrade to 13.10 - Cannot auto-mount drives"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by adjohnson916-gmail on 2013-10-25
Just upgraded from 12.10 to 13.10 through the automatic upgrade.

Now when I try to mount disks through Nautilus, I get an error dialog saying "Unable to mount $DRIVE" and "Not authorized to perform operation".

I've tried changing the gvfs mount path from "/home/$USER/.gvfs" to "/run/user/$USER/gvfs/" in "/etc/mtab", but no luck.

I've also tried making myself the owner and group of "/media/$USER/$DRIVE", with recursive write permissions.

Here's a relevant line from `mount` output:
```
gvfsd-fuse on /home/anders/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=anders)
```

I can still mount drives manually using `mount` on the command line.

Any suggestions?

---

### Post by jjaison-daniel on 2013-10-26
I am having the same issue after upgrade from 13.04 to 13.10.
. No automount for usb devices
. Unable to shutdown/reboot from the menu
. Network list is empty (but via sudo the network list are there)
. unable to edit User manager, the unlock button is grayed out always.
. ......

---

### Post by adjohnson916-gmail on 2013-10-26
> **jjaison-daniel said:**
> I am having the same issue after upgrade from 13.04 to 13.10.
. No automount for usb devices
. Unable to shutdown/reboot from the menu
. Network list is empty (but via sudo the network list are there)
. unable to edit User manager, the unlock button is grayed out always.
. ......

I have all of those issues as well. Could these be related?

---

### Post by dexter4096 on 2013-10-28
me too!

---

### Post by russ-ricks on 2013-11-03
I, too, am having all of these issues.  Cannot mount anything: SD card, Kindle, MP3 player.  Cannot restart or shutdown only given option to Log out or Lock.  Unable to edit user settings, lock bar grayed out. admin users hangs.  Nothing!  help!

And, unable to even use Software Updater/application center. Says I am unauthorized, not permitted.  What gives?  Had no issues yesterday.

---

### Post by jjaison-daniel on 2013-11-05
Please check the following bug, If you are facing the same please click the link "This bug affects X people. Does this bug affect you?" ([https://bugs.launchpad.net/ubuntu/+bug/1248211/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+bug/1248211/+affectsmetoo)). This will bring more attention to the developer.
[https://bugs.launchpad.net/ubuntu/+bug/1248211](https://bugs.launchpad.net/ubuntu/+bug/1248211)
If you are not affected the same then don't click that link.
Thank You.

---

### Post by ivan.salines on 2013-12-11
I have experienced the same issue after upgrade from 13.04 to 13.10 "Unable to mount $DRIVE" and "Not authorized to perform operation".

I have found "Inhibit udisks2" policy active. The rule is in this location /var/lib/polkit-1/localauthority/90-mandatory.d/udisks2-inhibit.pkla
This is the content:
[Inhibit udisks2]
Identity=unix-user:*
Action=org.freedesktop.udisks2.filesystem*;
ResultActive=no
ResultInactive=no
ResultAny=no

I have removed the rule... reboot and solved.





   Can someone verify the adventitious presence of the rule ?

---

### Post by Carlos_Moreira on 2014-04-29
> **ivan.salines said:**
> I have experienced the same issue after upgrade from 13.04 to 13.10 "Unable to mount $DRIVE" and "Not authorized to perform operation".

I have found "Inhibit udisks2" policy active. The rule is in this location /var/lib/polkit-1/localauthority/90-mandatory.d/udisks2-inhibit.pkla
This is the content:
[Inhibit udisks2]
Identity=unix-user:*
Action=org.freedesktop.udisks2.filesystem*;
ResultActive=no
ResultInactive=no
ResultAny=no

I have removed the rule... reboot and solved.

I'm having the same issue, however, the above stated rule was not present in my system, though, the 90-mandatory.d directory was. Any ideas? I still can't mount external drives by plugging them in.

---

