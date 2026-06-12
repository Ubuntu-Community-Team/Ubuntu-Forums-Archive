---
title: "Upgrade issue: Ubuntu 8.04 to Ubuntu 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by raghunath22 on 2008-11-02
I read the other threads on the same topic and didn't find a solution or the same exact problem so am creating a new thread. New here so apologies if I transgress :)

I recently upgraded from a beautifully running Heron to a crippled Ibex :(

As soon as I upgraded and restarted the machine, after the orange logo screen, I get moved to a shell and a command prompt that says,

> 
Gave up waiting for root device. Common problems:
 - Boot arguments (cat /proc/cmdline)
   - Check rootdelay = (did the system wait too long?)
   - Check root = (did the system wait for the right device?)
 - Missing Modules (cat /proc/mod/(I can't remember what this was); le/ dev)

Alert! /dev/disk/by-uuid/[long hash string] does not exist. Dropping to a shell!


And then it says: BusyBox something or the other.

I am not very technical adept but have been doing decently with Ubuntu for the last year or so. Still scratching my head trying to figure this out.

Another thing I tried was booting with the .24-21 kernel instead of the new version. There I was able to boot, but into a low graphics low res Ubuntu :(

feeling sad and wanting to move back to Hardy unless someone can help me understand and diagnose this issue. 

P.S. I tried the update, upgrade, dist-upgrade thing and that did not work either.

Sad,
Raghu.

---

### Post by Pumalite on 2008-11-02
Get into Recovery Mode and try 'xfix'

---

### Post by raghunath22 on 2008-11-02
Will try that now and update the thread. Hope that helps. Thanks :)

---

### Post by Pumalite on 2008-11-02
'Fix Broken Packages'
'Fix xorg'

---

### Post by raghunath22 on 2008-11-02
worked like a charm on the old kernel. Still doesn't work on .27-7 

Didn't understand what u meant by the above instructions ...

Thanks a lot, Pumalite

---

### Post by Hazer on 2008-11-02
He means go into recovery mode by selecting the 2.6.27-7 generic (recovery mode) at grub, and selecting the actions he said

---

### Post by raghunath22 on 2008-11-02
Thanks Hazer. If it go into the recovery mode for .27-7 and enter xfix, it says xfix not found. Ibex works perfectly in .24-21 as of now. 

Thanks again for the help and patience.

---

### Post by Hazer on 2008-11-02
xfix means select fix x server

---

