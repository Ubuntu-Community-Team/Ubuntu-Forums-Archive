---
title: "Re-configuring a dedicated server"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by DirtyMonkey on 2008-04-07
I need to reconfigure the default installation on my dedicated server but I'm new to Linux/Ubuntu 6.06 LTS (Dapper Drake)  and really need a step-by-step guide to reconfigure the server ready to install Plesk.

Currently I can SSH in to the chroot no problem, and then I have to SSH from the chroot to the real root using the ```
ssh -p57 root@localhost
```

I wish to remove that additional step and be able to SSH straight into the real root, is this possible? can it all be done over SSH and if so how do I go about it?

Thanks in advance, DM.

---

### Post by Oldsoldier2003 on 2008-04-08
> **DirtyMonkey said:**
> I need to reconfigure the default installation on my dedicated server but I'm new to Linux/Ubuntu 6.06 LTS (Dapper Drake)  and really need a step-by-step guide to reconfigure the server ready to install Plesk.

Currently I can SSH in to the chroot no problem, and then I have to SSH from the chroot to the real root using the ```
ssh -p57 root@localhost
```

I wish to remove that additional step and be able to SSH straight into the real root, is this possible? can it all be done over SSH and if so how do I go about it?

Thanks in advance, DM.

it would be best to talk to the hosting company because if you break it you are likely to get charged for support bring the box back up to a usable configuration.

---

### Post by Rocket2DMn on 2008-04-08
If you are paying somebody to host the server for you, they should be able to reset it to the default configuration for you.  Otherwise, the only way to really do that is to do a fresh reinstall since there is no "revert to original settings" program or process.

---

### Post by DirtyMonkey on 2008-04-09
My webhosts WebFusion have informed me that apparently this is not possible. 

Unfortunately their advertised root access is not 'direct' root access.

Personally with the right knowledge I think it is possible. I have now cancelled this dedicated server account and gone with redstation who have been like a breath of fresh air!

DM.

---

