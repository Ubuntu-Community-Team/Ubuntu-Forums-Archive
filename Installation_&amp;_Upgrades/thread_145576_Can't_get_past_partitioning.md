---
title: "Can't get past partitioning"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by cybiant on 2006-03-16
I'm attempting to install Dapper on a Dell Latitude D800 system.  I've tried booting from the cd image to install & from the Expresso installer off the live DVD.  Both will not allow me to get further than defining the partitions.  After which in the Espresso Installer I get the error Failed to create a file system.  I've installed Hoary w/ no issues on this laptop.  Anyone having this issue or a similiar one that could point me in the right direction?

Any help would be most appreciated.

---

### Post by Xian on 2006-03-16
It might be that your disk geometry is no longer correct. I would troubleshoot this by going into a Linux partition or LiveCD and running the 'parted' command from a terminal. Look to see if there are any error messages. You can do the same using the InstallCD by using the keyboard control keys to drop from the CLI to a shell (you'll have to find the exact key sequence).

---

