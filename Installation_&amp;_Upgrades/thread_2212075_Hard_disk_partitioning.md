---
title: "Hard disk partitioning"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by fangorn2 on 2014-03-19
Hello.

I am going to install Ubuntu.
First of all I am still undecided between Ubuntu 12.04.4 LTS and Ubuntu 13.10. I do not understand why the last release should have support only for 9 months, whilst Ubuntu 12.04.4 LTS will be supported until 2017. Usually one may think that the best thing to do is to install the last release of whatever software. Is this kind of 'support' fundamental?

I read something about the convenience to create partitions and allocate to them a certain amount of space.
For instance, I read it might be convenient to create a swap partition as big as the physical memory, a /usr partition big enough to receive the applications, a /home partition big enough for users and their documents. It might be useful to think about how big /, /var and /boot will be.

In the fourth step of the full installation instructions, it is written that 'you can create or resize partitions yourself, or choose multiple partitions for Ubuntu'. However I would also install Ubuntu alongside Windows 7. Is that possible? Or if I want to install Ubuntu alongside Windows 7 I should create the partitions for Ubuntu (with GParted live, for instance) 'before' installing Windows and Ubuntu?

I would do this: I would create partitions for Windows 7 and Ubuntu, then I would install Windows 7 and then I would install Ubuntu selecting what:
'something else' during the Ubuntu installation or
'Install Ubuntu alongside Windows 7'?

If I choose the latter, will I still be able to select for Ubuntu the partitions previously created?

What partitions would you advise to create and how big they should be?


Many thanks in advance

---

### Post by ajgreeny on 2014-03-19
> **fangorn2 said:**
> Hello.

I am going to install Ubuntu.
First of all I am still undecided between Ubuntu 12.04.4 LTS and Ubuntu 13.10. I do not understand why the last release should have support only for 9 months, whilst Ubuntu 12.04.4 LTS will be supported until 2017. Usually one may think that the best thing to do is to install the last release of whatever software. Is this kind of 'support' fundamental?
Every two years there is an LTS version with, in the past, a three year support period which has now been increased to five years.  That is still a short period when compared with other OSs where the basic system has been supported for many more years before a new version arrives.  The system of ppa repositories allows many of the applications in that LTS version to be upgraded faster than using the standard repos, eg, on my 12.04 version I now am running Libreoffice 4.2 by adding the LO ppa repository.

> I read something about the convenience to create partitions and allocate to them a certain amount of space.
For instance, I read it might be convenient to create a swap partition as big as the physical memory, a /usr partition big enough to receive the applications, a /home partition big enough for users and their documents. It might be useful to think about how big /, /var and /boot will be.I suggest you avoid making your system as complicated as that information suggests and make partitions for root (/) of about 15 - 20GB, swap of about 2 - 4GB, unless you will want to hibernate which will require as much swap as your physical ram, and the rest of available space for /home

> In the fourth step of the full installation instructions, it is written that 'you can create or resize partitions yourself, or choose multiple partitions for Ubuntu'. However I would also install Ubuntu alongside Windows 7. Is that possible? Or if I want to install Ubuntu alongside Windows 7 I should create the partitions for Ubuntu (with GParted live, for instance) 'before' installing Windows and Ubuntu?You can certainly install ubuntu alongside windows 7 and you are making life easier by installing windows first, though I can not help with partitioning for windows, not having used it for several years.
You do not have to make partitions in advance of installing ubuntu, but it is something I usually do as it makes it easier to see what is on disk and means you have everything waiting for your choice when you install;  see below.
> I would do this: I would create partitions for Windows 7 and Ubuntu, then I would install Windows 7 and then I would install Ubuntu selecting what:
'something else' during the Ubuntu installation or
'Install Ubuntu alongside Windows 7'?

If I choose the latter, will I still be able to select for Ubuntu the partitions previously created?

What partitions would you advise to create and how big they should be?


Many thanks in advanceSee above for comments about making partitions in advance (or not) and their sizes, but whichever way you choose, I think you must for safety's sake use the "Something Else" when you get to the partitioning stage of installation.  I have seen too many cases of installations wiping out an installation of windows accidentally; using "Something Else" almost removes that as a possibility: almost but not totally, so be very careful!

---

### Post by sudodus on 2014-03-19
I agree withe *ajgreeny*, and I want to add one point. ***Backup***.

If you haven't done backups before, I suggest that you start now. Editing partitions is risky but in general, things can go wrong any time. If your whole system, or at least your personal data are backed up in a separate drive (external drive or network drive), you have peace of mind. There are many ways to backup your data. Find methods and intervals, that work for you.

---

### Post by Mark Phelps on 2014-03-19
When you install Win7 to an unformatted drive, it automatically creates two partitions -- a boot partition and an OS partition.  

To avoid this, do the following:
1) Boot using the Ubuntu install media
2) Create a 40GB NTFS partition on the drive using GParted
3) Reboot using the Win7 installation media -- and select the partition you just created and choose the option to FORMAT it -- that's important.

When done, you will STILL only have one partition on the drive -- but it will contain both the OS files and boot loader files for Win7.

---

### Post by fangorn2 on 2014-03-19
Thanks for your answers and advice.

My hard disk is 250 GB. I have planned to allocate 100 GB to Windows (so more than 40 GB: would that be a good idea?), 50 GB NTFS partition available to both OS (for documents) , and 100 GB to Ubuntu. I would create these partitions before any installation, with GParted.
So, I will have to divide the 100 GB for Ubuntu into three partitions, according to ajgreeny suggestion: 20 GB for root (/), 2 GB for swap and the remaining for /home. Is that correct? 

Wouldn't be 78 GB too much only for /home? I am the only user and I would mount the 50 GB NTFS partition for my documents.
What about /usr? Wouldn't be /usr included in the 20 GB for root? Is that enough?

Would you make different partitions/different sizes?

---

### Post by sudodus on 2014-03-19
I would use only / (root partition) and a swap partition for Ubuntu. I think it would be enough with 50 MB for this root partition. Then I would *get a bigger shared **data** partition* available from Ubuntu and Windows.

---

### Post by ajgreeny on 2014-03-19
> **sudodus said:**
> I would use only / (root partition) and a swap partition for Ubuntu. I think it would be enough with 50 MB for this root partition. Then I would *get a bigger shared **data** partition* available from Ubuntu and Windows.

Yes, I agree with sudodus, now I know more about your disk size etc etc.

If you are sharing a data partition with win7 there is not a great need for a separate /home partition for your ubuntu data files, so keep /home within the root partition and use just root and swap partitions.  In this case I believe 50GB for root is more than enough andf wuld probably reduce that by 50% to 25GB.  I recommend that you do not make separate partitions for any other ubuntu folders normally in root; it can end up making life a lot more difficult and often makes more problems than it is trying to solve.

Once this is all sorted come back with the output from the ```
command sudo blkid -c /dev/null
``` and we can show you how to mount the shared ntfs partition at ubuntu boot so it is available straight away when you need to access your files; it simply needs an edit of /etc/fstab.

---

### Post by fangorn2 on 2014-03-19
Ok then, 50 GB for root.
I also read in a magazine that it is advisable not to exceed the size of the physical memory for the swap partition.
I have 2048 MB of RAM. Would that means that I should not allocate more than 2048 MB to the swap partition?
Anyway, as I understood, 2 GB would be enough.

---

### Post by sudodus on 2014-03-19
If you want to hibernate, you need at least as much swap as RAM in Gibibytes (base 2). Otherwise, you can get along with less swap. 2.2 GB will be fine (2 Gibibytes = 2147483648 bytes) even for hibernating, otherwise 1 GB is probably enough.

---

