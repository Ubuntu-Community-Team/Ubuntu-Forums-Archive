---
title: "Finding UUID of partition as non-root user"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by Lars Noodén on 2010-08-27
The installer for Ubuntu 10.04.1 LTS fails to allow HFS partitions to be recognized or made.  Adding them manually after installation is possible, but it is hard to find the UUID because blkid seems not to do anything for normal user accounts and must be run as root (using sudo) to get any information.  

[How to find your UUID’s for devices in Ubuntu](http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/) shows how to find the UUID by examining one of the devices.

So, the answer and question in the same post is, that regular users can examine the device **by-uuid** to see the list of UUIDs used by the partitions.

```

$ ls -l /dev/disk/by-uuid

```

---

