---
title: "Resize Operation Failure"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by jlaf1169 on 2008-11-01
I tried installing ubuntu 8.10 on my compaq presario c700 (windows vista) and this is what happened when i tried to resize partition using freed space... It stopped at 0% showing the error message...

ERROR MESSAGE

``An error occured while writing the changes to the storage devices...The resize operation has been aborted``

I did defrag my system before i tried to install.

---

### Post by jlaf1169 on 2008-11-01
i red somewhere that the partition could not take more than 50% with vista... the partition that ubuntu wanted to create took more than 50%... is that why it failed

---

### Post by kaingeo on 2008-11-06
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/279778/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/279778/)

---

### Post by Mark Phelps on 2008-11-06
Don't use Ubuntu or Gparted to try to resize your Vista partition -- unless you have a bootable Vista Recovery Disk or Vista DVD.  Linux-based changes to Vista partitions often leave Vista a unbootable, and that can only be fixed (for Vista) by doing a Startup Repair -- and that requires booting from one of the disks mentioned.

---

