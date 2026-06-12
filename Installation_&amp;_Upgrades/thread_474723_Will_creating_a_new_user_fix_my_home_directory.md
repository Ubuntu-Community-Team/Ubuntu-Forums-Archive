---
title: "Will creating a new user fix my home directory?"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by emgator on 2007-06-15
Let me explain:

I installed Edgy x86 (again) last night after an unsuccessful go at Feisty AMD64. During installation, I tried to separate my HDD into 3 partitions: 10GB (/), 1GB (swap), and 102GB (/home). Somehow I screwed this up and ended up with TWO swap partitions, one being 102GB.

I managed to format the 102GB partition as ext3 and mount it as /home in my fstab, but in the process it deleted ALL of the information in my original home directory (.firefox and other various hidden directories). I logged in as root (I know, a sin) and copied root's home to my /home. I relogged in as my normal user almost fine, but, obviously, nothing is how I want it, and I'm worried about the long term effects of not having those important hidden directories.

My question is, then, can I just create a new user and all will be good in the world? I'm slowly resigning to the fate of reinstallation, but I always spend two days making Ubuntu exactly how I want, and I don't really want to run that gamut again.

Any help/advice would be GREATLY appreciated!

---

### Post by dreadlord_chris on 2007-06-15
> **emgator said:**
> Let me explain:

I installed Edgy x86 (again) last night after an unsuccessful go at Feisty AMD64. During installation, I tried to separate my HDD into 3 partitions: 10GB (/), 1GB (swap), and 102GB (/home). Somehow I screwed this up and ended up with TWO swap partitions, one being 102GB.

I managed to format the 102GB partition as ext3 and mount it as /home in my fstab, but in the process it deleted ALL of the information in my original home directory (.firefox and other various hidden directories). I logged in as root (I know, a sin) and copied root's home to my /home. I relogged in as my normal user almost fine, but, obviously, nothing is how I want it, and I'm worried about the long term effects of not having those important hidden directories.

My question is, then, can I just create a new user and all will be good in the world? I'm slowly resigning to the fate of reinstallation, but I always spend two days making Ubuntu exactly how I want, and I don't really want to run that gamut again.

Any help/advice would be GREATLY appreciated!

That *should* work fine. The big problem with copying root's home to your home folder is - everything is still **owned** by root, so you can't do anything with them. You could at least fix that part by:
```

sudo chown -hR UNAME:UNAME ~

```
replace UNAME with your user name. This command will change the owner & group of all files & folders in your home directory to your user:group. Logout & log back in - you should now have access to all you configs...

Creating a new user would be a good way to start out "clean" - just be sure to add it to the **admin** group so it has access to **sudo**

---

