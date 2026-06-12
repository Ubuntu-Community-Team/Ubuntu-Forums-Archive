---
title: "Drive partitioning on install"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by arodulfo on 2012-12-22
Dear all,

I have a Core 2 Duo based computer running on Windows XP.
I found the chance to add a new hdd in and decided to go on dual boot, with xubuntu 64 bits as the new main o.s. for the system.

After much former reading on the subject, where advisors here and there told you to take that chance to make wiser partitioning in your system, I decided to opt for a 50 GiB partition for / and /boot trees, ext4, some 4 GiB for swap (seemed enough in my 2GiB ram system), and the rest of the hdd (some 300 GiB, ext4), for /home tree.

Once I had it installed and running, I realized it had two "antonio" folders; one of the was located in the 50 GiB partition, active and always mounted, under... /home!, which was supposed / expected to be in the bigger partition; the second "antonio" folder appeared under /media/15a9af41-4453-40a2-a0c8-1a6d7627b777/, only visible if I decide to mount that bigger partition.

Taking aside the possibilities to manually overcome this mess, I wonder why did the installer go down that way?, how can I avoid it in the future?

Thank you so much for your time and for your help.
Kind regards

---

### Post by sudodus on 2012-12-22
I think that you had the chance at the partitioning screen in the installer, see the attached picture.

Select 'Something else', which allows you to select mountpoints, one for the root / and another one for /home.

---

