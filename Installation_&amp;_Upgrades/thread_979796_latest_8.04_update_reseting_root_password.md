---
title: "latest 8.04 update reseting root password?"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by frankdn on 2008-11-12
% uname -a
Linux D830 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
%

I took an auto-update this morning that seems to have reset the root password.

I tend to use su, rather than sudo, when I want to do something as superuser.  However immediately after taking this am's update, su began denying authentication.  I can think of no other perturbations to the system that might cause the root password to be changed without my knowledge. (I am the only user of this machine.)

I used sudo to reset the root password, so the problem wasn't disabling, but it is a bit alarming that this should happen.

I'd be glad to share which updates my system took this morning, if someone would be kind enough to tell me how to find and dig through my update history.  /var/lib/dpkg/status doesn't seem to include an install date.

Thanks!

---

### Post by tuxxy on 2008-11-12
> **frankdn said:**
> % uname -a
Linux D830 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
%

I took an auto-update this morning that seems to have reset the root password.

I tend to use su, rather than sudo, when I want to do something as superuser.  However immediately after taking this am's update, su began denying authentication.  I can think of no other perturbations to the system that might cause the root password to be changed without my knowledge. (I am the only user of this machine.)

I used sudo to reset the root password, so the problem wasn't disabling, but it is a bit alarming that this should happen.

I'd be glad to share which updates my system took this morning, if someone would be kind enough to tell me how to find and dig through my update history.  /var/lib/dpkg/status doesn't seem to include an install date.

Thanks!

You right this has happened to me also, just checked now I think this needs a bug report Ill post the link soon

---

### Post by tuxxy on 2008-11-12
Heres [the link ]("https://bugs.launchpad.net/ubuntu/+bug/297227")if you would like to comment

---

