---
title: "Sysadmin tools fail after 8.04 upgrade"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by jzwanzig on 2008-05-12
Dear Colleagues, I've just upgraded a Lenovo T60 laptop from 7.10 to 8.04. I had the same wireless network problems others have reported and so also installed the backports package. That helped. However, at no time since the upgrade (yesterday) have the following tools worked: Administration->Hardware Drivers, Software Sources, Synaptic Package Manager, Update Manager. All "launch" with the clock icon and then after about 10 seconds disappear, without asking for a root password or anything else. Can anyone suggest how to address this problem?

thanks much,
Joe Zwanziger

---

### Post by slewis01 on 2008-05-28
Me too! Exactly the same - is it a problem with keyring manager?

I can't run admin tools, so no updates despite update notification telling me that they are available. I cannot shut down either, icons all disappear and I'm left with my desktop wall paper. Any help appreciated

---

### Post by rorsino on 2008-05-28
I also am having the same problem.  Anyone have a fix ??

---

### Post by dstew on 2008-05-28
See [this thread]("http://ubuntuforums.org/archive/index.php/t-613521.html"). Maybe this is the problem.

---

### Post by slewis01 on 2008-05-29
> **dstew said:**
> See [this thread]("http://ubuntuforums.org/archive/index.php/t-613521.html"). Maybe this is the problem.

This works for me!

Edited my hosts file in network settings so that 

127.0.1.1 slewis01-ubuntu.pcs

became 

127.0.1.1 slewis01-ubuntu

and everythings back, internet still works and my windows network is still visible.

Result!:)

Thanks dstew \\:D/

---

