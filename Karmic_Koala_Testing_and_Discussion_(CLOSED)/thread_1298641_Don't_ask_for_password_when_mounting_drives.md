---
title: "Don't ask for password when mounting drives"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-10-23
In jaunty there was an option so you wouldn't have to retype your password every time you mounted a partition that doesn't get automounted. This was great because you could then use a gnome-do plugin to mount things as needed. That option seems to be gone (atleast I can't find it) in karmic and this makes the gnome-do plugin of dubious value as it just silently fails instead of prompting for a password. Is there anyway to enable this option or something similar?

---

### Post by LKjell on 2009-10-23
I you need the **user** option in fstab.

For more info check man fstab and man mount.

---

### Post by metalk9 on 2009-10-23
I think what Longinus00 means is that when you try to mount a partition from the Places menu, you get an authorization dialogue without any option to remember password. It is also no longer possible to setup authorizations using the polkit gui due to the migration to devkit. I can't seem to find any configuration gui for devkit and I seem to remember reading that they haven't written one yet :( Might of been an idea to sort that out before using devkit as this is a major usability issue for people with multiple disks/partitions who didn't set up mount points during the install and don't know how to edit fstab.

---

### Post by ingegnerlillo on 2009-10-23
+1!

We definitely need this features back!

---

### Post by Longinus00 on 2009-10-23
> **metalk9 said:**
> I think what Longinus00 means is that when you try to mount a partition from the Places menu, you get an authorization dialogue without any option to remember password. It is also no longer possible to setup authorizations using the polkit gui due to the migration to devkit. I can't seem to find any configuration gui for devkit and I seem to remember reading that they haven't written one yet :( Might of been an idea to sort that out before using devkit as this is a major usability issue for people with multiple disks/partitions who didn't set up mount points during the install and don't know how to edit fstab.

I was pretty sure them dropping policy kit had something to do with this too but I posted with the hope somebody else might have come up with something.

---

