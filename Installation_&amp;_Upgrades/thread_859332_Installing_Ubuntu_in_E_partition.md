---
title: "Installing Ubuntu in E partition?"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by DLLN on 2008-07-14
Have have two partitions on my computer C and E.  C is the one i have always used and E is empty.  Is it possible to install Ubuntu in the E drive even though it doesn't have windows?

---

### Post by estyles on 2008-07-14
When you install Ubuntu, it will bring up a partition manager.  What you'll want to do is delete the empty partition, and that will free up space for an Ubuntu partition.  What size is that partition?

Depending on size, you'll be best off splitting it into 3 paritions.  A swap drive, which would be about 4 GB, a user (/home) drive, which should probably be at least 10 GB, and a system (/) drive which should probably be at least 5 GB and preferrably 10 GB.

Before installing, you should definitely check out the guide at [psychocats.net](psychocats.net).  It is very helpful, and gives detailed instructions for how to install, as well as some other common tasks.

---

### Post by DLLN on 2008-07-14
The drive is 104Gb so theres lots of room.

Thanks for the help

---

### Post by Pumalite on 2008-07-14
Make it:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.

---

### Post by Sef on 2008-07-14
> A swap drive, which would be about 4 GB, a user (/home) drive, which should probably be at least 10 GB, and a system (/) drive which should probably be at least 5 GB and preferrably 10 GB.

Swap should never be more than 1 GB.  The 1 1/2 - 2 times ram applies only if you have 512 ram or less.

---

### Post by Pumalite on 2008-07-14
In laptops /swap should be equal to RAM if you want hibernation. So if you have a laptop with 2 GB of RAM and you want hibernation, /swap should be 2 GB.

---

### Post by estyles on 2008-07-14
Sorry for the misinformation there.  Maybe I was thinking of Windows - my windows pagefile tends to always be around 2.5 GB.  I have plenty of space, and am not at all averse to buying a new HD if I end up using what I have, so I made my swap drive 4GB, and I'm happy with that.  Unless you have a very small drive, I would probably still make the swap drive 2GB - just to be safe.  Extra space never hurts, as long as you don't desperately need that 1GB for something else.

---

### Post by Pumalite on 2008-07-14
Sef is right. You should not waste hard drive space with /swap unless you need it. For general purposes 1 GB is more than enough. I have 1 GB and never use it.

---

