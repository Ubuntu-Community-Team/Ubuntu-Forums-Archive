---
title: "[SOLVED] kernel updates and partition names"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by theonlykman on 2007-06-10
Hi,
Everyone time I get a kernel update my grub menu gets automatically updated as well, which would be ok, except it keeps on changing the root= field to some "uuid...." that doesn't actually represent the device that I have ubuntu on...so it doesnt boot. I have to go into menu.lst and change it manually to /dev/sda3 (the right partition). Also on bootup I get an error that says something like "boot sector doesn't match it's backup". Does it have anything to do with the fact that I moved ubuntu to another partition via a reinstall and a backup restore? So, in conclusion, its not that big of deal, but I'm pretty sure what I'm doing now isn't ideal. Thanks for an explanation.

---

### Post by Jussi Kukkonen on 2007-06-10
Regarding automatically changing root-variable: You have probably misunderstood how menu.lst should be edited. See an earlier discussion here: [http://ubuntuforums.org/showthread.php?t=457135](http://ubuntuforums.org/showthread.php?t=457135) . Hope it helps.

---

### Post by theonlykman on 2007-06-11
Thanks for your help!

---

