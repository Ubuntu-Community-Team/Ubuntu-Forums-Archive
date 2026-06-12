---
title: "Preseeding with single HHD+ RAID - /dev/sda changes"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by bmckim on 2011-08-02
I have an LVM partition recipe that works fine, but we want to start adding in a separate disk to put the operating system on. The problem I am running into is I do not know whether the RAID will be /dev/sda or the single HD will be /dev/sda. Is there a better way to tell the OS which drive to install on?

---

### Post by psusi on 2011-08-02
What?  sda is always a single hard drive, md0 is a raid array.

---

### Post by bmckim on 2011-08-02
I am using hardware RAID and it just shows up as /dev/sd*

---

### Post by psusi on 2011-08-02
Then the OS does not know or care whether you are using a raid or not, so it makes no difference.

---

### Post by psusi on 2011-08-02
Oh wait, you are saying that you are going to have two disks basically, and don't know which one is which?  Well yea, that is always a problem.  Even if you only have a single disk, if you are installing from a LiveUSB stick, sometimes the usb stick gets sda and the hard disk becomes sdb.  You can not rely on device designations like that because they can change even on the same machine across reboots.

---

### Post by bmckim on 2011-08-02
Correct. But I have to specify which disk to install to. So is there a better method to use rather then /dev/sda?

---

### Post by psusi on 2011-08-02
I think you just can't preseed the installation disk properly.

---

### Post by bmckim on 2011-08-02
Not really an option :(

---

