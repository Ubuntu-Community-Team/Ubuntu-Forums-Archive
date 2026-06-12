---
title: "Errors when using software center and update manager"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by tlhodgson on 2011-06-16
Hi all,

Using 11.04. Kept up with all the updates.

I was trying to browse through the ubuntu software center (looking for chromium). It opens, and lets me search, but that's as far as it goes. It just continues to sputter (the little symbol in the screen keeps turning round and round). I thought I would try to do an update through the update manager and got a message stating:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
-------------------------------------------------------
My only option at this point is to close the update manager.

I tried updating through a terminal. All seemed to be going well, but at the end I got this message:

Fetched 432 kB in 3min 5s (2,327 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
terry@terry-Inspiron-1564:~$ 
------------------------------------------------------------
As of now, the computer seems to function properly otherwise, but I can't update, and I cant use the software center. What is wrong and how do I fix it?

Thanks in advance for your assistance.
Terry

---

### Post by drs305 on 2011-06-16
There are a couple of files that could be corrupted. If it's just the one, the least intrusive and easiest GUI way of fixing it would be to open Synaptic, then Settings > Repositories > Ubuntu Software tab. Untick the "main" entry, leave it deselected for a few seconds, then reselect it and press "Reload". This will delete the 'main' list files in /var/lib/apt/lists and then re-download it.

If that doesn't work, you can try the more comprehensive:
> sudo rm /var/lib/apt/lists/*
sudo apt-get update
Be careful with the first command, as you are acting as 'root' and removing system files. You will get a message saying 'partial' is a directory, which is ok as you only want to delete the files.

---

### Post by tlhodgson on 2011-06-16
Thanks drs! The code entries worked just fine. Didn't even take long. I appreciate your quick and helpful response. Problem solved.

---

