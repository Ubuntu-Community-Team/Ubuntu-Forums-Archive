---
title: "Accidental Deletion of Users"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by jervine on 2005-09-14
What is the default password if you accidentally delete your user?? p

---

### Post by mlomker on 2005-09-14
[QUOTE=jervine]What is the default password if you accidentally delete your user?? p[/QUOTE]

Are there any other users that you can login as?  The problem is that there is no password for root unless you've set one.

I'd try selecting 'rescue' mode from the Grub menu and logging in with a blank password.  From there you should be able to:

```

useradd -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,admin,lpadmin,yourusername yourusername

```

Yeah, that's a long line but those are the groups that the first user is in by default (there shouldn't be any spaces in the group names...I'm not sure why they are getting in there).

---

