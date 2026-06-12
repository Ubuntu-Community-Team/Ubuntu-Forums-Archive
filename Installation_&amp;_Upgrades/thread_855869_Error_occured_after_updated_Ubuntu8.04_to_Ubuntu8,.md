---
title: "Error occured after updated Ubuntu8.04 to Ubuntu8,04.1"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by shrewdwolf on 2008-07-10
After setuped the system  "Ubuntu 8.04", I update the system to Ubuntu 8.04.1 underlying the system hint.

It may update successful.But I cannot update then,not noly from terminal,but also from update tools.
------------------------------------------------------------------------------------------------------------------------------------------
The hint may be as follows:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
------------------------------------------------------------------------------------------------------------------------------------------
When i run 'sudo dpkg --configure -a', it failed again.The hint is as follws:

configuring initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: sub-processor post-installation script returned error NO.1
------------------------------------------------------------------------------------------------------------------------------------------

Then how could i do to resolve the problem?

---

### Post by Partyboi2 on 2008-07-12
looks like you could have run out of space. What is the output to this command
```
df -h
```

---

### Post by shrewdwolf on 2008-07-16
3Q!
That's really the correct reseaon.
I only allocate 100M fro /boot/

---

### Post by Partyboi2 on 2008-07-16
You can use gparted to increase the size of your boot partition or remove some of the old files. You can open up synaptic package manager and do a search for linux-image and remove the ones you don't need. eg linux-image-2.6.xx-xx-generic****

---

