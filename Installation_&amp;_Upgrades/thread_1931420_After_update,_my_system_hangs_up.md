---
title: "After update, my system hangs up"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by jemvyc on 2012-02-25
I was running Ubuntu 11.10 with kernel 2.6.38-12-generic and I updated.  Now the system tries to start kernel 3.0.0-15-generic and the system hangs at the start of boot.

Obviously there is an error and I would try to reload the update, but I can't get this to go away without removing the battery, and running update from the prior installation tells me that the new one is done.  Please help me to get rid of the bad install.

I don't know how to copy the screen of the hung up computer so I am typing this by hand.  I will try to catch all the typing errors.

After boot my screen reads:

Boot from (hd0.4) ext3  553fc2f3-dcd1-4bdb-a045-86fc64439be9
Starting up ...
[    0.789927] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0.0)
[    0.789981] Pid: 1, comm: swapper Not tainted 3.0.0-15-generic #26Ubuntu
[    0.790027] Call Trace:

There is more if you need it.

Thanks

---

### Post by gordintoronto on 2012-02-25
You should be able to select the older kernel at the grub stage. If you are not seeing that choice, try holding the shift key down as soon as your system starts up.

Also, how did you get to this position: "Ubuntu 11.10 with kernel 2.6.38-12-generic"? That kernel is not part of 11.10.

---

### Post by jemvyc on 2012-02-26
Grub shows kernels 2.6.38-8 2.6.38-10 2.6.38-12 and 3.0.0-15  I got them by updating using update manager to update the software over several months.  The problem with 3.0.0-15 came about when running kernel 2.6.38-12 and running update and accepting all of the updates offered.

the kernel 2.6.38-12 still runs fine, but trying to update from there right now, it says there is an update downloaded but not installed.  

I just ran update using 2.6.38-12 and it looked like it was installing kernel 3.0.0-16 but grub is unchanged and the broken 3.0.0-15 is still at the top of the list.

Can you help me get beyond the mess I have made with the system?

---

### Post by jemvyc on 2012-02-26
Not knowing what I was doing, I took a chance using apt-get to delete the 3.0.0-15 kernel.  I used sudo apt-get remove --purge linux-image-3.0.0-15-generic 

Now I have kernel 3.0.0-15-generic and it works.  Thanks for helping.

---

