---
title: "Deleted the content of /usr/locol/lib"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by Zohair08 on 2010-06-01
Guys,

I have committed a stupid mistake, I deleted the content f this folder. Do I need to totally reinstall ubuntu or there's a resoration tool??

Thanks
Zoh

---

### Post by lemming465 on 2010-06-04
No, you don't need to totally reinstall Ubuntu (unless you want to; it might be easiest).  No, there isn't a restoration tool; ext[234] don't really have undelete capabilities.  Someday BTRFS will.

In general, only 3rd party stuff you installed from non-Ubuntu repositories will be in /usr/local, including /usr/local/lib.  On my system this is only a flash plugin.  If *ls /usr/local/bin* is empty, just do *mkdir /usr/local/lib*, maybe reinstall flash if you use that, and you are probably OK.

---

