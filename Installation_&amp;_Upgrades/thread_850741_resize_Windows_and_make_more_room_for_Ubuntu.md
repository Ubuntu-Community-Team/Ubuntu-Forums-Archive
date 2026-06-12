---
title: "resize Windows and make more room for Ubuntu"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by caliva on 2008-07-05
I am running Vista - installed first with Ubuntu. However I want to make the Vista partition smaller and resize/enlarge the Ubuntu partition.

the Ubuntu partition lives in an 88 GB extended partition. If I resize the Vista partition from inside Vista and then use Gparted to resize the extended Ubuntu partition, could I set it to add the newly freed space to only the "home" partition inside this extended partition? (the NTFS and the ext3 extended partition should be contiguous then)

was it a good idea to establish the partitions this way, with Ubuntu in an extended partition, *or* should I have made the swap, root and home separate partitions? (I am just wondering if in case I have to reinstall Ubuntu and want to leave the home partition intact)

Wiping out the two 1GB unallocated partitions wont cause any harm, will it?

(note: the fist NTFS dev is for the manufacturer's recovery console)
[IMG]http://xtort.net/Screenshot.png[/IMG]

---

### Post by Partyboi2 on 2008-07-05
> the Ubuntu partition lives in an 88 GB extended partition. If I resize the Vista partition from inside Vista and then use Gparted to resize the extended Ubuntu partition, could I set it to add the newly freed space to only the "home" partition inside this extended partition?
You would probably find that after your shrink down the vista partition the unallocated space would have to be moved step by step all the way down to your /home partition.

---

### Post by logos34 on 2008-07-06
>  Wiping out the two 1GB unallocated partitions wont cause any harm, will it?


Actually if you look closely they're 1 and 1.57 **MB**.  Try to grow sda1 to absorb the first one, and reclaim the second either by extending sda2 or the extended (and then the swap so there's no gap). 

> **Partyboi2 said:**
> You would probably find that after your shrink down the vista partition the unallocated space would have to be moved step by step all the way down to your /home partition.

That's the safest way (remember, you'll have to do it from the live cd), and if at all uncomfortable working with partitions that's probably how you should resize them.  However it will take hours and hours...

But if it was me, I think I'd do this:

1. Resize vista using it's own disk utils

2. Reboot into Vista a couple of times to let error check run/make sure it's ok

3. Boot the ubuntu live cd and install **Partimage**:

 - >system>software sources>enable 'universe' repo

open terminal:

[B]sudo apt-get install partimage

sudo partimage[/B]

4.  Mount your vista partition, sda2 (make sure it does so read-write).

5. back in Partimage, make images of / and /home.  Put in a path to sda2 (that's where it will save the images).  Use default compression (gzip).  Should take only about 15 minutes or so (your combined used space is only ~12 gb).

6.  Once that is done, use Gparted to delete the logical partitions and the extended.  Create a new extended partition comprising the entirety of the unallocated, and recreate the /swap, / and /home, the same size, in that order.  

7. Restore the images of / and /home to the new partitions.

8.  That's basically it.  The partition numbers shouldn't have changed so you won't need to edit any files.  

9. Reboot into ubuntu.  If successfull, reboot to the live cd and use gparted to expand the /home to take up the rest of the remaining space and the end.  

Done.  (hope I didn't forget something)

That's the fastest way I can think of.  But unless you've used partimage before, you'll probably opt for the slow but sure way and I don;t blame you.  But there it is anyway.

---

