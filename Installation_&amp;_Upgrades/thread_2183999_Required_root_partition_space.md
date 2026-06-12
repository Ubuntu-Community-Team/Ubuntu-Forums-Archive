---
title: "Required root partition space?"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2013-10-27
My netbook is running 13.04 and I'm going to move to 13.10 soon.  I use the LTS version on my bigger, more powerful laptop but this thing is a cedarview gpu machine and 12.04 doesn't work nearly as well.  So for the netbook I'm stuck with the semi rolling release update every 9 months.

SoI figured I'll reinstall rather than upgrade through the software installer and do the smart thing this time.  I.e. set up a separate partition for /home.  I know I could do this before installation but it's more involved and since I'm going to upgrade anyway ...

The thing I'm not sure about is how big a partition / excluding home needs ... and I know that's not a question that can be precisely answered "over the phone" but maybe I can get a rough idea of how much space root outside of user data will take.

I usually just use the netbook outside running around in cafes etc., and frankly the hard drive is bigger than I need at 320Gb for that purpose.  And I don't have that many programs installed on it.  Root - /home is about 22Gb.  But I'd like a very rough idea anyway.  You never know what I may put on later.

---

### Post by ptn107 on 2013-10-27
I've always done a 12-16GB '/' and never even filled half of it (the most I ever filled was like 43% or something), and I have lots of extras installed.  I give 'swap' 2GB (it doesn't ever get used, it's just a safety net) and '/home' the rest of the free space.  Since everything [important] is on '/home' I do a clean install every release cycle which wipes '/' but I keep the sizes the same.  No problems ever.

---

### Post by Rob Sayer on 2013-10-27
Thanks, that's pretty much what figured.  Though I probably should set up a 2Gb swap anyway even though I still have 1Gb in this netbook.

---

### Post by vanadium on 2013-10-27
I work with 10 GB all the time. Usually, this is more than fine. The only problem is that temporary directories also reside on root. Exceptionally, this could cause applications that write a lot of temp data to use significant space on the root drive. It occurred to me that old kernels were already taking a lot of space on the root partition, to the extent that less than 1 GB was available for temp data, and I got my partition filled. To prevent that possibility, I redirect temp space to my /home partition. In addition, I remember now and then to go clean up old kernels.

---

### Post by ajgreeny on 2013-10-27
And I have a Lubuntu 12.04 install on an old Acer laptop with only a 30GB disk in it, and on that my root partition is only 6GB with 3.7GB used, though I admit the machine is too slow to use for any games that might use lots of root space, and I use it only occasionally, mainly for audio recording and playback of sound effects for stage work.

In all honesty it is not worth having a separate root and home partition on a 30GB sized disk, but it is historical and I've never got round to changing it

---

