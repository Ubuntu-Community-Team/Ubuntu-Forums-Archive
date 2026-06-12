---
title: "Windows 10 corrupted ubuntu linux partition more details"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by oldspammer on 2016-05-04
[http://ubuntuforums.org/showthread.php?t=2303775&page=3](http://ubuntuforums.org/showthread.php?t=2303775&page=3)

Additional details are that the iso boot and install of the same 15.10 over itself was troubled to start with due to the /boot partition being full of a very large number of linux image binary files with associated cruft.

I did not want to bother with sifting through /boot to sort out what to keep, so I removed all files via rm -rf *

I rebooted via the boot / install iso DVD, installed again, rebooted, then re-installed via the internet all the missing applications that failed to be recovered.

As usual LAN based PC names did not resolve to IP addresses so an entry had to be added to the /etc/hosts file.

This time the fstab update with the cifs entries worked fine the first time.

---

