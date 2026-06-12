---
title: "Installation bug?"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by jnvm on 2005-08-10
Hi All,
I'm pretty new to Linux, and having some installation woes.  

I've  dual boot Win XP machine, with two HDDs.  I installed Ubuntu, no worries, and it worked, but XP couldn't see the second disk (where I'd put Ubuntu).

So, I reinstalled, setting one of the partitions (/home) on the second disk to be FAT32.  When I get to the set up username and passwords part of the process, I enter a username and password, and it just goes around again and asks for a username and password.

If I skip that stage, when I get to later on, it says that I haven't set a root password, and would I like to.  I can do that, but I can't log in as root.

(Windows can now see the partition though.)

Is this a bug that's related to the FAT32, or is that irrelevant?

Thanks,

Jeremy

---

### Post by Juergen on 2005-08-10
> So, I reinstalled, setting one of the partitions (/home) on the second disk to be FAT32Don't do that. 
FAT32 doesn't support Linux-permissions and other stuff - this probably leads to your user/password loop, and would lead to more problems if you could get around this one.

If you need rw-access from both OS, create an independend FAT32-partition and mount this in Linux under e.g. /mnt/shared

And there have been several threads lately mentioning a win-driver for access to ext2/3 partitions from windows. Look at this one:
[http://www.ubuntuforums.org/showthread.php?t=55648](http://www.ubuntuforums.org/showthread.php?t=55648)
If you want to try this, you could make your /home-partition ext3.

---

### Post by jnvm on 2005-08-12
Excellent - that did the trick.

Thanks very much.

Jeremy

---

