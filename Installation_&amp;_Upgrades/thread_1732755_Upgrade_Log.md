---
title: "Upgrade Log"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by agentsmith.android on 2011-04-18
I am running ubuntu 10.10 in a vm. I recently did new updates and wired network access went off. I need to figure out what made network go off. So, I need to see the log of the updates which took place. Is there any way to do so? Can I revert to previous state? 
(I am running in VM and I don't have grub.So, can't boot from previous state as can be done natively)

---

### Post by garvinrick4 on 2011-04-18
```
gedit /var/log/apt/history.log
```

---

### Post by agentsmith.android on 2011-04-18
thnx. :)
Do u know if we can revert the changes?

---

### Post by garvinrick4 on 2011-04-18
> **agentsmith.android said:**
> thnx. :)
Do u know if we can revert the changes? Never used VM do not want to answer what I am not positive about.

---

### Post by drs305 on 2011-04-18
Here is a command that can show you recent activity. Keep the 'space' in the command so "installed" shows but "half-installed" doesn't.
```
grep ' installed' /var/log/dpkg.log 
```

I sometimes clone my VMs before doing a major update. You might be able to retrieve a previous version of a package from the Launchpad site and force install it, but there isn't an automated 'reversion' option in Ubuntu.

---

