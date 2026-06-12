---
title: "!HELP! installing ubuntu onto a external hard drive"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by ghost_may_cry_ on 2010-07-14
what im trying to do is install ubuntu on to an external hard drive, partition it and make it work.

ive got a problem, as i have 200GB of games and other things already on that drive, before you say "copy it to another drive and then back" i cant, i dont have any other drives apart from my internal which has only got 20 gig left

all help will be appreciated,
GHOSt_MAy_CRy_

---

### Post by YesWeCan on 2010-07-14
Hi.
A little more info needed, like:
1) What capacity is the external drive?
2) What partitions does it have on it and how big are they?
3) Are you new to linux?

---

### Post by nothingspecial on 2010-07-14
You only need 6 or 7 gigs for Ubuntu so make a partition that size either on the internal or external.

One day one of your drives will fail, that is inevitable. If you have a lot of data you don`t want to loose, purchase another drive and back it all up......trust me, I know.

---

### Post by ghost_may_cry_ on 2010-07-14
> **nothingspecial said:**
> One day one of your drives will fail, that is inevitable. If you have a lot of data you don`t want to loose, purchase another drive and back it all up......trust me, I know.

I know that quite well, as my internal is gonna fail soon (noises and slow load times)

@YesWeCan
1)  its a 640gb wd green (sold as an external) formatted as an ntfs drive with 400 gb of storage left
2) it only has 1 partition and gparted wont let me change it
3) yes i am new to linux but i know a computer inside out (if that helps)

hope that helps

---

### Post by nothingspecial on 2010-07-15
> **ghost_may_cry_ said:**
> I know that quite well, as my internal is gonna fail soon (noises and slow load times)

@YesWeCan

2) it only has 1 partition and gparted wont let me change it


It`s not mounted is it? You cannot partition a mounted drive.

---

### Post by efflandt on 2010-07-15
If you have Vista or Win7 on a computer, you could shrink the USB ntfs partition with Computer Management on them.  Otherwise the USB is probably auto mounted, and as mentioned, you have to make sure that it is NOT mounted before attempting to resize or change partitions with gparted (from live system on CD or USB flash).

If gparted complains about something wrong with the ntfs partition and suggests doing **chkdsk /f** on it from Windows, do that.

---

