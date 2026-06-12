---
title: "Keep -or- Modify Config file? after upgrade to v16.04"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-09-20
Towards the End of upgrading from v14.04 to v16.04 we get the following message;

"Configuration file '/etc/ld.so.conf' 
==> file on system created by you or a script.
==> file also in package provider by package maintainer
What would you like to do? Options are:
Y : install the pkg maintainers version
N : keep your current version
D : show the difference
Z : start a shell to examine the situation
The default action is to keep current version."

Don't understand the significance of Keeping or Modifying the file. Any suggestions ? ? ?

Thanks!

---

### Post by mandavi2 on 2016-09-20
> **Rick St. George said:**
> 
D : show the difference


and post it here.

---

### Post by howefield on 2016-09-20
Try show the difference if you are unsure, then make a decision.

That file on my system is only a one liner, might be different on yours but easy enough to take a copy in case you get to a point where you want to revert back.

hugh@xenial-laptop:~$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf
hugh@xenial-laptop:~$

I'd suggest accepting the new file with a copy of the old one safely tucked away.

---

### Post by Rick St. George on 2016-09-20
Keeping current version. After checking with "cat", only thing in there was BITDEFENDER. 
The new file - etc/ld.so.conf.dpkg-new, had nothing in it.

However, after viewing ... Accepted the newer version of "rcS".  The "cat" is usefull to verify contents before continuing. 

Thanks!

---

