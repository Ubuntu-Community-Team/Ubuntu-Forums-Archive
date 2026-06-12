---
title: "/etc/fstab and /home partition"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Xswitch on 2008-11-29
Is there a better way?

I have a separate /home partition, and every time that I upgrade, I have to edit the /etc/fstab.  

Is there a better way to do this?

---

### Post by taurus on 2008-11-29
What sure what you mean you have to edit /etc/fstab to mount /home when you upgrade?  /home should always be mounted if you have an entry in /etc/fstab for it.  However, if you reinstall, then you have to tell the installer to mount that partition to /home with ext3 filesystem but do not format it if you want to keep all your personal files on $HOME.

---

### Post by Xswitch on 2008-11-29
Thanks Taurus...  When I installed, I would always just leave my "/home" partition alone and just format /.  I now know better...  Thanks a ton...

---

