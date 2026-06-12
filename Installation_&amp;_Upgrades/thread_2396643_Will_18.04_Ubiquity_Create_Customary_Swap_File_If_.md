---
title: "Will 18.04 Ubiquity Create Customary Swap File If Install on RAID O Array?"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by lostmoonofsaturn on 2018-07-18
The plan here is to build a new machine this weekend and use 2 identical NVME SSD&#8217;s in a RAID 0 setup, via mdadm.

But first... two questions:

1.  All the advice Google has turned up for me relates to 16.04.  Has anything changed in 18.04 regarding software RAID creation and use? Can&#8217;t find any Ubuntu docs to say it has, but the RAID docs aren&#8217;t all fully current.

2.  It&#8217;s a UEFI motherboard.  If I tell the installer &#8212; Ubiquity&#8212; to &#8220;Use the Entire Disk&#8221; AND that disk is the RAID partition, e.g., /dev/md0, will Ubiquity create a swap file as it would during a normal non-RAID install? (I am assuming that swap file will be striped and otherwise treated as any other FILE.)

(Should add I&#8217;ll be booting from the RAID array.)

---

