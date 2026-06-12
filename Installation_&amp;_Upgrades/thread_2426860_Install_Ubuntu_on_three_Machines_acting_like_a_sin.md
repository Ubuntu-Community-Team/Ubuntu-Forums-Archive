---
title: "Install Ubuntu on three Machines acting like a single Machine"
date: 2019-09-14
forum: Installation &amp; Upgrades
---

### Post by jenniferruurs on 2019-09-14
I have three desktops all connected via UTP to the same router.
Each of this individual desktop has 32GB ram and 8 cores
These tree desktops have exactly the same hardware.

I want to Install Ubuntu one time on all of these three Machines acting like a single Machine.

How can I use all the 96Ram and 24 Cores centrally from my Terminal?

---

### Post by Tadaen_Sylvermane on 2019-09-16
Google Beowolf cluster I think. Not sure but it sounds like what you want.

---

### Post by TheFu on 2019-09-16
Only extremely specialized software can be used on a "cluster" in that way. That software would need to be custom created to split up tasks in such a way that different parts of the task can be run by different processes and communicate between each other.  

From a desktop or gaming standpoint the answer is NO.  Gaming software is generally written to use only 4 threads, so more than 4 CPUs/cores isn't really helpful for most games. There are probably exceptions, but they won't go across different computers.

There are many different sorts of clusters, so it really depends on the specific workload you intend.  Most will not scale linearly. There is significant overhead in each node's management of the workload and communications back to the controller.  The easiest pre-made software that can be used across multiple nodes most efficiently would be DBMS software with partitioned DBs.

And I hope you aren't using just UTP, but are on at least a 1 Gbps network on each, 10Gbps would be better, and using CAT6 networking.  UTP cables have extremely limited bandwidth for 2019 ... or 2000.

---

### Post by jenniferruurs on 2019-09-20
Thank you Beowolf cluster was what I was looking for indeed

---

### Post by TheFu on 2019-09-20
Someone else asked a similar question here the last few days.  Gnu-parallel was an option that would work for cluster-unaware software.   [https://www.gnu.org/software/parallel/](https://www.gnu.org/software/parallel/)  lots of documentation, examples, videos, and comparisons at that link.

There are about 50 other tools which try to accomplish the same parallel processing, but most don't also support going across different machines. I routinely split batch tasks manually using a bash script, ssh, taskspooler and inotify to handle long running jobs across different systems.

---

