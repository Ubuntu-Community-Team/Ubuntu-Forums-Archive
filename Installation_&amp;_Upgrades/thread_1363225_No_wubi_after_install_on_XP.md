---
title: "No wubi after install on XP"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by eljopc on 2009-12-24
I installed 2x Wubi on my Win XP Home and there is no place to choose for wubi. Not on startup no icon on windows desktop.

---

### Post by lloyd_b on 2009-12-24
I had that problem recently - turns out that it had set a default timeout of 0, so it was immediately booting XP.

Open up a command prompt "Start->Programs->Accessories->Command Prompt", change to the root directory ("cd C:\"), make the "boot.ini" file editable ("attrib -R -H -S  boot.ini"), then "edit boot.ini" (or at this point you can edit it using any program).

Check the "timeout" line to make sure that it's a reasonable number of seconds (not zero), and change it if necessary.

Lloyd B.

---

### Post by eljopc on 2009-12-25
> **lloyd_b said:**
> I had that problem recently - turns out that it had set a default timeout of 0, so it was immediately booting XP.

Open up a command prompt "Start->Programs->Accessories->Command Prompt", change to the root directory ("cd C:\"), make the "boot.ini" file editable ("attrib -R -H -S  boot.ini"), then "edit boot.ini" (or at this point you can edit it using any program).

Check the "timeout" line to make sure that it's a reasonable number of seconds (not zero), and change it if necessary.

Lloyd B.

Thanks, will try this.

Is this reported to the BUG list of Wubi?

---

### Post by lloyd_b on 2009-12-25
> **eljopc said:**
> Thanks, will try this.

Is this reported to the BUG list of Wubi?

Yes, it has been reported and acknowledged on Launchpad ([Bug #382614]("https://bugs.launchpad.net/wubi/+bug/382614")).  Note that this bug has been around a while - they just haven't gotten around to fixing it.

Lloyd B.

---

