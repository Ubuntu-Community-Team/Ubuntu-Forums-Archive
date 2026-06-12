---
title: "Problem with Breezy Partitioning Tool"
date: 2006-03-23
forum: Installation &amp; Upgrades
---

### Post by unixcorn on 2006-03-23
I have tried to replace a previous Hoary-Hedgehog installation with a Breezy-Badger installation. This worked fine on an HP nx9005 laptop, but has hit a problem when it comes to the partitioning stage on a Cyrix MII-300 based desktop system.

With Hoary, the installation process worked just fine, but with Breezy the partitioner just hangs. It goes through the progress bar stage of loading the partitioner, and searching for existing filesystems, then it clears the screen to a light blue background (as it does between each stage of the install). After this, the disk light flickers intermittently for about 20 seconds and then everything stops.

Using Ctrl-Alt-F2 I can get into the second terminal screen, and 'ps' shows that the last numbered process is doing something around automatic_partitioning at stage 10resize.... Since the terminal does not appear to wrap around, I cannot see what is happening at the tail end of the command line so I do not know specifically if there are any parameters to the partial command I can see.

My system has a 40 GB hard drive as the primary on the first IDE channel and a 20 GB drive as the primary on the second IDE channel. The system has several different OS's on both disks, and I am trying to install Breezy onto a 6 GB logical partition on the second drive.

Anyone know why the partitioner gets stuck on Breezy, while it works okay on Hoary? Also, anyone know how to get the partitioner to complete its task?

Thanks.

---

### Post by Sef on 2006-03-27
> Anyone know why the partitioner gets stuck on Breezy, while it works okay on Hoary? Also, anyone know how to get the partitioner to complete its task?

Have you used that disk on another computer?  Possibly it is bad, thus the problems you are having.

---

