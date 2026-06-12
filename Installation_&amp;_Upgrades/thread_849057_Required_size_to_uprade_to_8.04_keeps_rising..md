---
title: "Required size to uprade to 8.04 keeps rising."
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by bubble_bobble on 2008-07-04
In my first attempt to upgrade to 8.04 I got an error message notifying me that I don't have enough space, and that I should have 1.1 GB of space to be able to upgrade.

Well I free up the necessary space and..

In my second attempt, I am told that I need to have 1.6 GB of free space to perform the upgrade. 

Ok... strange, I free up the necessary space.

I try to upgrade two more times, and every time the size requirement keeps rising, albeit more slowly every time, so, for example, the last time I tried to upgrade to 8.04 I got this message

The upgrade aborts now. The upgrade needs a total of 1833M free space on disk '/'. Please free at least an additional 3067k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I am upgrading from 7.10 by clicking System->Update Manager.

I've been upgrading every 6 months since 5.10, so this is a new experience for me.

---

### Post by SkonesMickLoud on 2008-07-04
Do you have a separate /home partition?

If so, it is advisable, as well as faster to simply wipe / and reinstall, marking /home as /home.

---

### Post by bubble_bobble on 2008-07-04
My home directory is just in my regular / . These are my partitions. ```


/dev/sda5             10325748   8026320   1774908  82% /
varrun                  256256       220    256036   1% /var/run
varlock                 256256         0    256256   0% /var/lock
udev                    256256       104    256152   1% /dev
devshm                  256256         0    256256   0% /dev/shm
/dev/sda1                64086      7494     56592  12% /media/sda1
/dev/sda2             48636784  48554376     82408 100% /media/sda2
/dev/sda3              4858184   4858048       136 100% /media/sda3
/dev/sda6             12032652  12017244     15408 100% /media/sda6
/dev/sda7              2040328   2029934     10394 100% /media/sda7 
```

---

### Post by bubble_bobble on 2008-07-17
Problem was resolved. I attempted to upgrade and it went through. A fact that might be of significance is that it worked when I came to the USA, but didn't when I was in Russia.

---

