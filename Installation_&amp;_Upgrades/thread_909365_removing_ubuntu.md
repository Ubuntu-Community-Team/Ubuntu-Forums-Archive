---
title: "removing ubuntu"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by tinkerbell_pete on 2008-09-03
i installed 8.04 about 4 hours ago. first time i restarted i could load into windows, next time i reloaded i couldnt even select which OS to boot into and says error 2 or 21 or it just hangs without doin a thing. i can boot into the live cd but thats it.

how can i fix the problem or undo the installation or ubuntu?

thanks 

TiNkErBeLl {Pete}

---

### Post by sayakb on 2008-09-03
Use Supergrub Disk ([http://supergrubdisk.org](http://supergrubdisk.org)) to reconfigure the boot loader.

---

### Post by sayakb on 2008-09-03
To remove ubuntu, insert your Windows Setup disk, goto recovery mode (press R), and type in **fixmbr**. This should boot you straight into Windows. From there, right click on My Computer, click Manage, click Disk Management and Format/Delete the Ubuntu partition.

---

### Post by tinkerbell_pete on 2008-09-03
which version for the supergrub disk do i use?

thanks

---

### Post by tinkerbell_pete on 2008-09-03
**Bump**

---

