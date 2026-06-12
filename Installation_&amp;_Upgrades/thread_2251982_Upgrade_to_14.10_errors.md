---
title: "Upgrade to 14.10 errors"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2014-11-08
During upgrade the following errors occurred:

A dialogue box asking for password came up about a 100 times
"Authentication is required to update SMART data from ST#### (/dev/sda)"
"action: org.freedesktop.udisk2. ata-smart-update"
"The udisk Project"
<<<<>>>>
could not install "syslinux-themes-debian"
<<<<>>>>
subprocess installed post-removal script returned error exit status1
<<<<>>>>
Error during commit install archives () failed
-----------------------------------------------
PC seems to be working OK after reboot

---

### Post by vasa1 on 2014-11-08
> **mayagrafix said:**
> ...
<<<<>>>>
could not install "syslinux-themes-debian"
<<<<>>>>
...
PC seems to be working OK after reboot
Ditto. I seem to have got round the issue by running **sudo apt-get install --reinstall syslinux-themes-debian**.

---

