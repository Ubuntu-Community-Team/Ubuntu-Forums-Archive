---
title: "samba update failed[Solved]"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by banjopikker on 2007-11-17
I received an update notice for Samba.  Here is what returned .
failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.3_i386.deb)
  404 Not Found. 
The requested URL /ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.3_i386.deb was not found on this server.
Is that a server problem , or is something wrong with my system?     Thanks.

---

### Post by taurus on 2007-11-17
Try

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jader2toesbumpy on 2007-11-17
> **taurus said:**
> Try

```
sudo apt-get update
sudo apt-get upgrade
```

same problem but with amd and that worked. thank you

---

### Post by banjopikker on 2007-11-17
sudo apt-get upgrade. That worked .   Thanks a bunch.

---

### Post by caro on 2007-11-17
Thanks!

---

### Post by PositiveK on 2007-11-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/54234](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/54234) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/54234](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/54234) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I encountered the same problem and had to do a web search to fix it (which is how I found this post).  I don't think this samba update failure is "solved" given that the update software did **not** do the appropriate thing.  If apt-get needs to be run (update, upgrade) before I get security updates, then the update manager is not doing its full job.  For non-tech heads and, indeed, for anyone, the update software should handle this or inform the user to do something like the previously mentioned workarounds.

I'll look for a bug in the bugs database and if I can't find one, I'll create one and add a link to this thread, too.

I'm attaching the Ubuntu Bug URL for what might be a related bug.

---

