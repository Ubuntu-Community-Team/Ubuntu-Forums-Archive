---
title: "Hardly Heroin Software Sources"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by wurx on 2008-08-27
Hi,

I don't know if this is a bug that needs fixing or what the issue is.

I've re-installed Ubuntu on my laptop. Now that I want to add my depositries I click on the ''add cdrom'' in the Third-party tab and then it asks me for the to ''Please inserta disk in the drive''. I load the disk and click ''ok. Then without checking if there is a disk or not it says immediatly
 ''Error scanning the CD''

''E:Failed to mount the cdrom''

The cdrom does mount though. I can enter the disk and clearly see the ''dists'' and ''pool'' folders. I have tried letting the disk mount first and the tried adding the cdrom and even clicked ''ok'' while closing the cdrom immediatly.

But still the same error occurs. I have installed and re-installed it on my Desktop and it's working fine. Got all 6 disks added.

What can the issue be? I really need some of the packages on these disks.

PLEASE help......

---

### Post by overdrank on 2008-08-27
Hi and please correct me if I am wrong but I believe you will need the alt cd for updates.

---

### Post by benny bronx on 2008-08-27
I would also suggest correcting the title of your post, since they do sometimes show up in Google results.  While we always want to attract new users, I do not think the world is ready for Heroinbuntu.

---

### Post by wurx on 2008-08-27
Overdrank, thanks for the idea but I don't know how many cd's that would be. My package contain 6 dvd's. I had them working before the re-installation though.

I see on my desktop those same dvd's mount to:

/mount/cdrom0

And on the laptop it mounts to:

/mount/CDROM

I think that could be my problem. Do you know how I can change the mount point from CDROM to cdrom0?

---

### Post by wurx on 2008-08-27
I do  not support drugs in any sort of way. But I do think

Hardly Heroin

says it well....

---

### Post by wurx on 2008-08-27
Sorted:

I've reinstalled Hardy Heron Ubuntu 8.04 and before I did anything to do with Software Sources, I stuck a normal cd into the rom and let it auto mount. 

I unmounted the thing and stuck the DVD in and clicked ''add cdrom'' and it took the dvd.

Thanks for the support guys....

---

### Post by meindian523 on 2008-08-27
Not exactly,because people will be searching Hardy Heron,not Hardly Heroin,or Heroin.Please change the title to something more appropriate and mark the thread solved.

---

### Post by wurx on 2008-08-27
Happy now?  :-)

Cuz I am.......

;-)

---

### Post by wurx on 2008-08-30
Ignore the fisrt sorted post. It didn't solve the problem.

I had to re-install once again and when I inserted my dvd after the cd I was back at square one.

For the life of me I could not understand it. Then it occured to me, after numerous re-installations, that the problem was from the start.

When I install Ubuntu on my laptop I made  2 partitons, 1 swap and 1 ext3. Everytime I did it this way the dvdrom would not mout to e: drive which software sources were looking for.

Now I have tested this. If I make 3 partitions, 1 swap, 1 ext3, and one ohter (fat32, journaling, etc) and install Ubuntu on the hdd like that it would mount the dvdrom insuch a way that software sources mounts the drive. With only the 2 partitons it didn't.  

Well, there you go. I'm not sure but I think it has something to do with the drive letters being assigned when it detects the drives when installing.

Hope it would help people with the same issue. I've re-installed Ubuntu eight times to prove the theory to myself.....

---

