---
title: "Rebuilding a System with Large Raid 1 array"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by William_in_Kanata on 2007-10-15
Ubuntu 6.06 server.

I am trying to rebuild a system with a Raid 1 array of two 750 GB SATA disks, and having a number of problems. This system was previously configured with two 320 GB disks, with no problem. We added the two large disks, but then couldn't find a way to set them up. So, as there was nothing of value on the system, we decided to do a reinstall. I get as far as the partitioner, which comes up and sees all four disks just fine. We make the required changes, and save the updated partition tables to disk, and the install process, instead of moving on to the next step automatically, goes to menu, which then steps you through the remaining jobs. Or should do. In fact, no matter which step I select, the Partitioning program restarts. so I can't complete the install. I eventually aborted the install process, rebooted from the CD and selected the "Resue a broken system" option. It starts ok, until it asks you to execute a shell, and allows you select a partition to run on. Of course since there is no system installed, this produces an error no matter which partition is selected. Starting a shell in the installer environment works, but on exit goes back to the menu. Again no matter what item is selcted, the Partitioner restarts, and this time gives the error message "Could Not stat device /dev/md/0 - No such file or directory", and gives the options to retry or cancel. Retry fails every time. cancel returns to the Partitioner startup, and it hangs forever (progress bar shows 47%).

So First question: Is there a limit on the size of disk that this release can handle? I don't ever recall seeing anything.

Second Question: Now What?

For now I have disconnected the two large drives, and rebuilt the system as it was. Any suggestions as how to add the new drives without re-installing would be appreciated. (remembering that this is a server install, with no GUI).

---

