---
title: "should I select dontuse?"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by confusa on 2007-07-17
About to install Feisty on a PC that already has WinXP. I have already setup the partitions using GParted roughly like so:

Win 40GB
Root 10GB
Swap 1GB
Home 29GB

As I go through the installer on the LiveCD I choose manual which takes me to the partition screen. Now I do not want to touch the Win partition AT ALL! When I hit the edit button I get the option to select dontuse. Should I select that? Or, will that simply not mount it and cause issues? Only slightly confused...

---

### Post by yabbadabbadont on 2007-07-17
You can use it, just make darn sure NOT to format it.  I think the option should say, "Keep existing data" or something like that.

---

### Post by Pumalite on 2007-07-17
If you already partition with Gparted, you should use: Guided>Use Largest Available Space.

---

### Post by yabbadabbadont on 2007-07-17
> **Pumalite said:**
> If you already partition with Gparted, you should use: Guided>Use Largest Available Space.

Ummmm.  His largest available space is his Win partition....  Better to do the manual partitioning and be careful than *hope* that the installer works the way you think.  ;)

---

### Post by confusa on 2007-07-17
> **yabbadabbadont said:**
> You can use it, just make darn sure NOT to format it.  I think the option should say, "Keep existing data" or something like that.

So what is the purpose of selecting dontuse? It isn't very clear what that means.

---

### Post by Pumalite on 2007-07-17
Choosing largest available space doesn't not touch XP because XP is 'not available'. 'Available' means empty space.

---

### Post by yabbadabbadont on 2007-07-18
> **Pumalite said:**
> Choosing largest available space doesn't not touch XP because XP is 'not available'. 'Available' means empty space.

He doesn't have any empty space according to his first post.  He has already created the partitions for Ubuntu using GParted.  :D

---

### Post by yabbadabbadont on 2007-07-18
> **confusa said:**
> So what is the purpose of selecting dontuse? It isn't very clear what that means.

It means that the partition that is marked as "dontuse" will not be added to the /etc/fstab file on the installed system.  Which means that it won't be mounted automatically when you boot Ubuntu.  You can still mount it in Ubuntu, but you will have to do it manually from either the command line or a terminal window.

---

