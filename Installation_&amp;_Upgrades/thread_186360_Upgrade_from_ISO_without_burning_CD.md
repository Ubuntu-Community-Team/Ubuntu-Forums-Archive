---
title: "Upgrade from ISO without burning CD"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by igor4u on 2006-06-01
I downloaded Ubuntu ISO.
How could I upgrade Ubuntu from this ISO without burning it to CD?

---

### Post by llamakc on 2006-06-01
mount -o loop /path/to/....iso /mnt/loop

Will mount the iso but if you're already running any version of Ubuntu all you have to do is follow the upgrade directions. I dunno if the installer runs from initrd or not.

You may want to mount it at /media/cdrom though.

Are you already running Ubuntu?

---

### Post by llamakc on 2006-06-01
You could also just add the cdrom as a repository for the time-being with `apt-cdrom add`

---

### Post by igor4u on 2006-06-03
[QUOTE=llamakc]You could also just add the cdrom as a repository for the time-being with `apt-cdrom add`[/QUOTE]
Thank you it all work! ;)

---

