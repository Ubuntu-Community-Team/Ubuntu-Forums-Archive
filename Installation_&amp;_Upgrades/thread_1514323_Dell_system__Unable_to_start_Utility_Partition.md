---
title: "Dell system:  Unable to start Utility Partition"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by Talon2 on 2010-06-20
The system is a Dell 530n.  It came preinstalled with Ubuntu 8.04.  I didn't care for the way Dell handled its repositories (they don't keep them current) so I installed Ubuntu 10.04.

Now when I select "F12 Boot Options" while the BIOS is bringing things to life, I still get the various boot options, however, when I select "Utility Partition" all I get is "Not found. No boot device available."

For those not familiar, the Dell Utility Partition is a hidden partition that has various utilities to help troubleshoot hardware problems.

What did Ubuntu 10.04 do and how do I fix this?

---

### Post by PRC09 on 2010-06-20
Depends on the type of install.Unless you did a manual install and told Ubuntu where to install and not use whole disk then it may have over written that partition......

---

### Post by psusi on 2010-06-20
Yea, if you told the installer to use the whole disk, then the utility partition is gone.

---

### Post by Talon2 on 2010-06-20
> **psusi said:**
> Yea, if you told the installer to use the whole disk, then the utility partition is gone.

The utility partition is not gone.  I did not select "whole disk" during the installation.

---

