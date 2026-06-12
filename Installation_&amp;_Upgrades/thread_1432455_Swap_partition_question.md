---
title: "Swap partition question"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by tgeer43 on 2010-03-17
I've noticed that every time I install a new version of Ubuntu alongside the others, a new swap partition is created as well.

I've finally got 9.10 x64 to the point where I'm happy and secure enough to get rid of all prior versions and consolidate the disk space. I'm gonna have to delete the swap partition that was created with the most recent install in order to reclaim all of the space after it. I'll be creating a new swap partition at the end of the disk.

My question is: Other than creating an entry for the new swap partition in /etc/fstab so it will be automounted at boot time, is there anything else I need to do so that Ubuntu knows to use this new swap instead of the one that was created for it (that I am deleting per the above)?

I've already moved my 'keeper' installation to the beginning of the disk (no mean feat in itself) and only need an answer to this one question before I can complete the entire consolidation process.

Thanks in advance,

tgeer

---

### Post by woodmaster on 2010-03-17
with 4 GB of RAM you shouldn't even need a swap partition.  monitor your RAM usage with an applet (I use sysmonitor screenlet) and you'll probably find you don't come anywhere close to using 4 GB.  If that's the case, eliminate tour swap altogether would be my advice

---

### Post by 2hot6ft2 on 2010-03-17
> **woodmaster said:**
> with 4 GB of RAM you shouldn't even need a swap partition.  monitor your RAM usage with an applet (I use sysmonitor screenlet) and you'll probably find you don't come anywhere close to using 4 GB.  If that's the case, eliminate tour swap altogether would be my advice
Eliminating swap eliminates the ability to suspend or hibernate, so not the best option.

Ubuntu will detect the linux swap partition automatically you don't need to tell it which one if there is more than 1 or if you remove the one it was using. It will just use what's available.

---

### Post by tgeer43 on 2010-03-19
Thank you 2hot6ft2. Exactly what I wanted to hear.

tgeer

---

