---
title: "mounted SwapFile not in use..."
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by a7j_72 on 2009-11-23
[B]About 2 weeks ago I installed Ubuntu Studio 64-bit with the encryption setting on.
Everything went well, except that at startup I would get:[/B]
[COLOR=Blue]One or more of the mounts listed in /etc/fstab cannot yet be mounted:
swap: waiting for /dev/mapper/[/COLOR][COLOR=Blue]cryptswap1
Press ESC to enter a recovery shell[/COLOR]
**at boot. It seems a lot of users had issues with the encryption setting.**



**After trying a couple of things, and not wanting to reinstall... I unmounted the partition, deleted it, and created a 2gig swapfile called: **

[COLOR=Blue]/swap_file 
[/COLOR]
[B]mounted it, 
set it as swap under fstab.[/B]

[COLOR=Blue]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc[/COLOR][COLOR=Blue]   proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e5d60159-62cd-43fd-9351-3d20edea3d43 /     ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
**/swap_file   none   swap   sw   0   0**[/COLOR]

[B]free -m show it as mounted but it is never used, no matter how much load I put on my system
I have included a screenshot of free -m.
I was rendering a video in the background using Kino.[/B]

---

### Post by a7j_72 on 2009-11-26
bump...

---

### Post by John Bean on 2009-11-26
Have you tried "swapon -a" ?

---

### Post by a7j_72 on 2009-11-26
first, thanks for ur response...

Yes... I dont get any errors when using [COLOR=Blue]swapon -a[/COLOR] .
I verify w/      "[COLOR=Blue]free -m[/COLOR]"
and I have listed for swap   
[COLOR=Blue]total: 2199mb
used: 0mb
free: 2199mb[/COLOR]

therefore it is mounted.
I understand that swap it is not used heavily until ram has nearly filled up. 
But I'm not getting any usage at all. Even when rendering videos, using multiple simultaneous apps. etc
 *I don't believe swappiness is an issue here *

---

### Post by a7j_72 on 2009-11-29
bump...

---

### Post by presence1960 on 2009-11-29
> **a7j_72 said:**
> bump...

How much RAM do you have? I have 4GB and have never seen my swap in use.

---

### Post by a7j_72 on 2009-11-30
UPDATE: Well turns out that I finally got to see extremely small action from my swapfile...
I had to encode a video, play a flash app,  fire up multiple firefox instances simultaneously to use up >.25mb of swap... 

Now all I have to do is edit my **swappiness**. 

So presence1960, u were right. thanx.

---

