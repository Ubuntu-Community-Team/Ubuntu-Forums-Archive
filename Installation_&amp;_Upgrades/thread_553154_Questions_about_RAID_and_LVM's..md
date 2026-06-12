---
title: "Questions about RAID and LVM's."
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by misconfiguration on 2007-09-17
All,

I have a RAID controller card that is set to RAID 10 (1+0), I have what may be a simple questions to most.

When I'm installing an OS, since I have a hard RAID controller do I still need to setup softRAID devices? Also where does LVM come into play on a setup like this?

I have 4 hard drives, I would like for all of them to be mirrored (hence the RAID 10 controller) Should I setup RAID partitions and throw them in a LVM then make sure each hard drive is set to that particular logical volume?

Something like this

1.) Setup RAID devices
2.) Add the raid devices to a logical volume
3.) Make sure the LVM is set on each physical disk
4.) Install the OS

I'm wondering if this will mirror properly in order to have the system boot with straight mirroring + striping, I'm under the impression that the hardware controller would do this automatically but I found out that it doesn't. 

Any suggestions would be greatly appreciated!

---

### Post by misconfiguration on 2007-09-17
Still reading about LVM's with not much luck on understanding this particular setup.

---

### Post by misconfiguration on 2007-09-18
I understand LVM's now, I guess my question would be this;

Is there a way to pool multiple partitions from multiple physical devices and make them one huge partition AND have it backed up with RAID?

I understand LVM can do this but if I have 120gb hdd's and I want all of them to be combined, how would I set this up in a RAID group?

Also where does a RAID card come into place when using one do I still need to setup softRAID or does the hardware controller handle all of it?

---

