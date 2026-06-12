---
title: "Live cd fails to mount harddrives in Edgy"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by Emess on 2007-06-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/66585](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/66585) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
On trying to install Feisty, I encountered so many errors that I downloaded Edgy to use instead. However this has still given 2 errors which I encountered in Feisty. 

```
ACPI: Getting cpuindex for acpiid 0x2
```

and

```
mount: function not implemented
```

The computer hangs for a bit while booting and displaying the errors but otherwise boots into the desktop without a problem. On installation however, it fails to recognise and drives to partition/install to due to the second error. I have looked all over for a viable solution to these problems but nothing I've tried has worked. I've looked on Launchpad and found some information but the cd is using S20checkroot.sh already and S10 is not present in the directory. Turning acpi off in boot options hasn't helped for the first error either. mount -V shows that mount is indeed present, however I remain unable to mount my drives. Any ideas are greatly appreciated.

---

