---
title: "Grub Rescue Mode on Fresh Install"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by timsorr on 2012-11-27
Hi all, I have done some searching but cannot find the answer to my problem.  A few weeks ago I created two partitions on my hard drive for desktop (so I can try some different os's without loosing media).  I installed debian on the first partition and was able to use it for a week and access media on 2nd partition.  I decided to give 12.04 a shot yesterday.  I installed on 1st partition using a thumbdrive and later a cd.  After both installs I get this message on bootup:  "grub loading.  welcome to grub  error: symbol not found 'grub_divmod64_full'. entering rescue mode... grub rescue>"  During the installs I chose manual install and chose to install on first partition and format to ext3.  I also made this the root directory (/).  Am I doing something wrong?  Both installs completed successfully, except for the error message on reboot.  Thanks for the help.

---

### Post by timsorr on 2012-11-27
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd-pendrive.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd-pendrive.html)

This fixed it!

---

