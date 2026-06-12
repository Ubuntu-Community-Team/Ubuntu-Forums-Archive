---
title: "Can't install on old Dell Precision"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2012-01-03
I have a strange installation problem on my Dell Precision 420 MT with dual Xeon processors.

I have an older version of Fedora installed in the HD (fc6) that runs fine. If I place the Ubuntu live CD (11.10) in the drive while fc6 is running , it reads it perfectly. However when I try booting from the CD it freezes at some point during some network configuration step. If I press the ESC key during boot I immediately see a message that reads something like "Can't find /dev/sdx..." where sdx could be sdb and/or sdc. If instead of inserting the Ubuntu CD I place an XP installation disk it boots perfectly. I tried booting the same Ubuntu CD on a different machine and it boots fine. So with Unetbootin I generated a bootable USB drive that I used to boot. Again, exactly the same issue. So I concluded that is not the CD nor the flash drive, but something in the machine that Ubuntu does not like. The bios is the latest version (A13) and I tried different things, such as disabling the network, disabling one of the processors, etc., to no avail.

I wonder if anybody have any ideas on this.

Thanks,

Daniel

---

