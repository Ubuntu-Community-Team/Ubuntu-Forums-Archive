---
title: "Can't login to VMware Server 2 after kernel update and reinstallation"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by MichiGreat on 2011-04-23
**Hi!**

After I updated the kernel (which is not clever when using VMware products) from 2.6.35-25 to 2.6.35-28, I had to reinstall VMware Server using that "raducotescu-vmware-server" script because recompiling with "/usr/bin/vmware-config.pl", as I did with VMware Server 1.0.6, didn't work, it said, the header files in "/usr/src/linux-headers-2.6.35-28-generic" are wrong, although they are obviously *not* wrong. I tried to boot with the old kernel but that trick - which I have done multiple times in the last years - did also not work, VMware was just dead. Then I booted again the new kernel and tried to reinstall VMware Server which worked. But now I can't login to the VMware Infrastructure Web Access, I always get an error message:

You do not have permissions to login to the server.

What to do now? Migrating from VMware Server to some other solution that doesn't cost me dozens of hours for nothing is already on my list, but first I must succeed starting my virtual machine again.

/etc/vmware/pam.d/vmware-authd looks interesting, but I have no idea what do change there.

Thanks for any hint!

Best regards,

*Michael*

---

