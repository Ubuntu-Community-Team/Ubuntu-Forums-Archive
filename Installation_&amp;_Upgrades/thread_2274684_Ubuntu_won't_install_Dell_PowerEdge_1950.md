---
title: "Ubuntu won't install Dell PowerEdge 1950"
date: 2015-04-21
forum: Installation &amp; Upgrades
---

### Post by Stece_The_Dev on 2015-04-21
It keeps telling me that I need to have at least 6.3 gb free.
I have no way of knowing if the drive is formated because the drive has the SAS interface and I don't have SAS on my pc. Server is brand new out of the box.

---

### Post by Vladlenin5000 on 2015-04-21
Well, you need at least one recognizable drive or array to work with. Dell Poweredge 1950 uses PERC5/i RAID controllers which are supported in Ubuntu since many years ago. What Ubuntu version/flavor are you trying to install?



PS - How is it "brand new"? Has it been sitting on a shelf for the past decade?

---

### Post by SeijiSensei on 2015-04-22
Boot from the installation CD, then choose Try Ubuntu.  You should then be able to launch gparted, examine the machine's hard drive, then re-partition as needed.  I don't know whether the SAS device will be automatically recognized, but if it is, the RAID array should appear as a single device like /dev/sda.  You should also be able to inventory all the devices on the machine if you go into the boot setup.

I use CentOS on servers because RedHat flavors usually handle hardware like PERC cards transparently.

---

### Post by Vladlenin5000 on 2015-04-22
Indeed. Dell recommended RedHat 4 or SuSe Server 9. Yes, that's how old the machine is.

---

