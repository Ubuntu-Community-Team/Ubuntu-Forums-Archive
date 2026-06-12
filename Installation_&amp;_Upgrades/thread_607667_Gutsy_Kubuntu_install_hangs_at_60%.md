---
title: "Gutsy Kubuntu install hangs at 60%"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by steveM49 on 2007-11-09
Upgrading kubuntu fiesty to gutsy via the recommended Adept package manager protocol.  The upgrade has hung at 60% of "installing updates".  The current task is configuring cdrdao.

Is there a way to terminate gracefully?  Is there a way to restart if I interrupt the procedure?  If possible, I'd like to avoid a fresh install.

Thanks for advice.

Steve

---

### Post by steveM49 on 2007-11-09
bump

---

### Post by steveM49 on 2007-11-15
I killed one of the two identical python scripts that were performing the upgrade.  The remaining one complained that there was another process using the apt database and closed on its own.

I used Synaptic to upgrade and everything was fine.  I don't yet know what caused the script to hang, but it left things in good enough shape that I could recover.

Steve

---

