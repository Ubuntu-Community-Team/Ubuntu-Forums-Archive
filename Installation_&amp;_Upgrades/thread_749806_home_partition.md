---
title: "/home partition"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by Gauvenator on 2008-04-08
If I have a /home partition is it safe to use it for multiple distros on the same PC at one time?

I currently have Arch and am planning to install a couple more distros (including ubuntu), and was wondering if I can use my /home partition for all of the distros.

---

### Post by Pumalite on 2008-04-08
Not a good idea. Settings are kept in /home and each distro has it's own kind.

---

### Post by munkyeetr on 2008-04-08
You can, but I don't know if it would be a good idea, as the configuration files would be getting overwritten time and again whenever you rebooted into a different distribution. I would be worried about this causing some corruption.

What I would do is have a large drive/partition that holds all my documents, pics, music, files, etc which I use as my main storage drive.

I would then install each distro in a single / partition and use their respective /home directories to store their particular config files, and run amount point in each distro to the storage drivel. That way all the distro's know what's theirs, and they can all access the storage drive when you need to.

---

### Post by rsambuca on 2008-04-08
It is fine to use the same /home for different distros, but I strongly recommend having a different user name for each distro.

---

