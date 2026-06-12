---
title: "&quot;Buffer I/O error on device dm-2&quot; when booting from Desktop CD"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by SEMW on 2006-07-03
Hi,

When I try to boot from the 6.06 Desktop CD, the boot process reaches "Loading enterprise volume management system", then suddenly drops the graphics and gives the following error:

[4294930.526000] Buffer I/O error on device dm-2; logical block 6303340

This then repeats about once ever few seconds, with the first 7-digit number in the brackets and the logical block number both increasing by a few.  The rate is about one logical block per second.  Occasionally it skips ahead by about a hundred blocks, but then continues.

The CD's MD5sum is correct.

What's device dm-2?  A couple of other people have apparently had this before, but they mostly had "device hdd" or "device hcd", which seem more evident.  I've tried removing the hard disk that I put in specially to install Ubuntu on, in case that was the problem, but no luck.  The only other hard drives in the system are a Windows drive and a drive for data, both of which work perfectly (both NTFS).  The only CD drive is the one from which I'm installing Ubuntu.

So, any ideas?  This is my first time trying Linux, so nothing *too* technical please :)

Many thanks,

Simon

---

### Post by SEMW on 2006-07-03
I am now posting this from Firefox, running on Ubuntu!

I posted the previous post from another computer whilst I left it to run through the buffer errors.  After about 3/4 of an hour of errors it recommenced booting.  It now seems to work fine, so I've no idea what the problem was.

Many thanks.

 - Simon

---

### Post by trash on 2006-09-01
I am starting to get 'dm-3' after i get some hdb3 and 5 errors on a fresh install. It's never happened before but I was sort of expecting my hd to die... This problem has only started since I upgraded Xubuntu a few weeks ago, lost it and reinstalled.

---

### Post by myrtille_beer on 2006-09-03
Hi SEMV,

unfortunately, I am not coming up with a solution here.
Exactly the same issue is occuring to me.

In additon to that, once the system gets finally started, I cannot mount any MS windows partitions.

I hope you solved your issue during summer and you or anybody can give me hints here.

Thank you all in advance

A pure newbie](*,)

---

### Post by nadamsieee on 2006-10-23
[http://ubuntuforums.org/showthread.php?p=1653875](http://ubuntuforums.org/showthread.php?p=1653875)

---

