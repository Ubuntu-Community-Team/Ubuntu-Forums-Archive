---
title: "Ubuntu Server 16 Kernel panic loop"
date: 2019-03-08
forum: Installation &amp; Upgrades
---

### Post by armegeden on 2019-03-08
Hello,

I have a few Ubuntu Server 16 virtual machines on an ESXi 6.5 host.  On one of them I was attempting to do my normal "apt update && apt upgrade -y" routine and was getting a disk full error.  I learned that my /boot was full and I guess I should have been incorporating 'apt autoclean' to my routine.  Too late.  Ended up deleting some older (timestamped) files manually and it looks like I deleted the wrong ones.

Now when I boot the OS it scrolls a bunch of text that I can't make out and ends with this line:
[0.672386] --- [ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Is there any way to recover my mistake?  Boot into a recovery mode and do something from there?  It would be great not to have to reinstall everything.

Thanks for any advice!

---

