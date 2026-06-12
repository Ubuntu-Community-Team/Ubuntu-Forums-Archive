---
title: "shutdown does not run /etc/rc0.d/S1umountfs"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by bkleine on 2011-11-19
Hi,
since the upgrade from 11.04 to 11.10 did not run well, i reinstalled the entire ubuntu two days ago. For the first time in months after the update, I got a ordered shutdown and all filesystems were umounted properly. However, after having run the actualisation yesterday morning, again umount during shutdown does not happen and after rebooting all filesystems have to recover their journals. 

 I do not have any network filesystem, any raid, only two drives with 7 partitions. Is there any possibility to log the shutdown to see where the process goes astray? Since it takes me minutes every morning when booting to wait for the recovery, I can investigate some time into elucidation of this unnormal behaviour. But I need help.

Any help welcome!

Greetings from the Black Forest!

Bernhard

(I can provide the list of files which were updated before the configuration got wrong)

---

