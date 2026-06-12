---
title: "ubuntu 12.04 to lubuntu 14.04 - backup and restore"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by Tim_Johnson on 2015-03-12
My intention is to upgrade a desktop from [COLOR=#0000cd]**ubuntu**[/COLOR] 12.04 to **lubuntu** 14.04.
The current configuration is partitioned to / (root) /home and /usr/local.
I would install by formatting **/** (root) only. If something goes wrong with /home, I have been backing up /home with duplicity.
I.E. System Settings->System->Backup
However AFAIK lubuntu 14.04 does not have duplicity installed by default.
1)Can duplicity be installed successfully on lubuntu 14.04?
2)Is there a backup app that might be recommended as an alternative? NOTE : must be able to restore from duplicity backup.

thanks 
- tim -

---

### Post by TheFu on 2015-03-13
Yes, you can install any ubuntu package you like into Lubuntu.  Desktop specific applications can cause configuration issues if the two programs are incompatible and write to the same config files.  This is more a risk when switching DEs, not applications like duplicity.

Should be fine. Just make certain you have the keys to the backup stored outside the backup - right?  It will be hard to decrypt any part of the backup without those keys at restore time.

BTW - if there is a GUI for the backup tool, then that isn't duplicity.  duplicity is a shell command.  I thought Ubuntu use DejaDup or Duplicati as an interface to duplicity. Same backend processing, just different GUIs - compatible.

---

### Post by Tim_Johnson on 2015-03-13
> **TheFu said:**
> Yes, you can install any ubuntu package you like into Lubuntu.  Desktop specific applications can cause configuration issues if the two programs are incompatible and write to the same config files.  This is more a risk when switching DEs, not applications like duplicity.

Should be fine. Just make certain you have the keys to the backup stored outside the backup - right?  It will be hard to decrypt any part of the backup without those keys at restore time.

BTW - if there is a GUI for the backup tool, then that isn't duplicity.  duplicity is a shell command.  I thought Ubuntu use DejaDup or Duplicati as an interface to duplicity. Same backend processing, just different GUIs - compatible.
Thanks for the reply. 
I installed lubuntu 14.04 on a little netbook here and then got deja-dup (DejaDup) and duplicity through synaptic. 
They installed without any apparent issues. I will just go with that on the desktop.
cheers
- tim -

---

### Post by TheFu on 2015-03-13
Please mark thread "solved", if this is solved.

---

