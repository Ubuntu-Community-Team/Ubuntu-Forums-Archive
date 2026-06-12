---
title: "Grsync question after upgrade to 22.04"
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by Panawe on 2022-08-31
Hi,

A small thing but since upgrading Grsync has duplicated the hard drives I use by putting a "1" after the name. It shows now two backup hard drives, but only the one amended with a "1" seems mounted. Bit irritating, anyone got a fix?

Otherwise the upgrade went well.

TIA

---

### Post by TheFu on 2022-09-01
Unmount all external HDDs and delete the mointpoint directories.   On reconnection, only 1 should be added back.

I don't think this is related to grsync - it is from the Gnome automatic mount.

If you don't want stuff like this in the future, don't let Gnome (gvfs/gio) control mounts.  You need to control them using either fstab or autofs.

Those are my best ideas.

Always remember, "the power to mount is the power to destroy."  Do you really want any automatic mounts for random storage to happen?  I don't.

---

### Post by Panawe on 2022-09-01
Thanks for responding.

However - "delete the mointpoint directories" - how do I do this?

Thanks again.

---

### Post by TheFu on 2022-09-02
[https://askubuntu.com/questions/1237929/how-to-delete-unused-mount-points](https://askubuntu.com/questions/1237929/how-to-delete-unused-mount-points) - found by google "delete the mointpoint directories" query. The comments and questions in that link should address any other problems completing the task.

---

