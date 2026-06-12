---
title: "Issue with sound after update"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by inkd on 2010-12-03
Hello,

I recently blindly accepted Update Manager's recommendations, and after I restarted my computer I no longer have sound, and it's not recognizing my mouse. Does anyone know if I can revert back in some way, or how to find out what the conflict is? Thanks,

Jay

---

### Post by inkd on 2010-12-04
bbbump

---

### Post by rstoya05-lx on 2010-12-05
I also lost sound after updating yesterday on Ubuntu 10.4.

---

### Post by rstoya05-lx on 2010-12-05
Try the following. IT worked for me.

System -> Administration -> User Settings
Click "Advanced Settings"
Click "User Privileges" tab
Enable "Use audio devices"

After that reboot and hopefully you'll get your sound as well. 

My sound was working before the upgrade even without this option being enabled so something changed. Maybe someone else has a better explanation.

---

### Post by inkd on 2010-12-06
> **rstoya05-lx said:**
> Try the following. IT worked for me.

System -> Administration -> User Settings
Click "Advanced Settings"
Click "User Privileges" tab
Enable "Use audio devices"

After that reboot and hopefully you'll get your sound as well. 

My sound was working before the upgrade even without this option being enabled so something changed. Maybe someone else has a better explanation.

hello rstoya,

When I go to System -> Administration, there is no User Settings option. Mind you, I am in Ubuntu 10.10.

And while that may solve my audio problem, there's still the issue of the mouse being disabled too, which means there's something bigger going on.

---

### Post by rstoya05-lx on 2010-12-06
Sorry I should have written "Users and Groups" but Ubuntu 10.10 may have moved things. The command line alternative should be "sudo users-admin".

Can't help with the mouse problem.

---

