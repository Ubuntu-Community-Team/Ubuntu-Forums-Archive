---
title: "[SOLVED] How to set up my harddrives before a clean install?"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by doubledouce on 2007-11-24
Hi!

I've been reading alot of posts on formatting the harddrives but it has confused me more than anything else. :oops:

Anyways, I'm doing a clean install of gutsy. I've got 1 HD with 250 GB, 1 with 500GB (this one is brand new) and one "multimediadisk" (or something... it's a HP thing). How would you guys partition these disks? Should i put ubuntu on the newest one ('cause it's supposed to be fastest)?

And what about /home, /root and all that? I want ubuntu to be as fast as possible, I'll be upgrading when the next version is released, and I'm installing only what I need. The computer will be used for watching movies, listening to music... aka a mediamachinethingy. :)


Hope anyone can answer. Thanks!

---

### Post by Pumalite on 2007-11-24
Are you going to have Windblows in  that machine?

---

### Post by doubledouce on 2007-11-24
No, only linux. :)

And I've got 2 Gigs of ram btw.

---

### Post by Pumalite on 2007-11-24
Get Gparted Live CD; [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it. Format the 250 and the 500 ext3. Leave the 'media' alone. Make the 500 'sda' (first in the boot order and 1st master in the computer. Install Ubuntu there. Guide>Use Entire Disk

---

### Post by doubledouce on 2007-11-24
Thanks!

So I shouldn't partition it at all? In windows I got better performance when I split my 250HD up in one little partition for windows alone and one big for media. Won't linux benefit from this?

And what about the /swap, /root, /user and all those? What is the optimal configuration?


Thanks for the help! :)

---

### Post by Pumalite on 2007-11-24
A good scheme is this:
10 GB for'/'
2x RAM up to 1 GB (laptops: /swap=RAM)
The rest for /home
Install, go Manual and use the partitions already made.

---

### Post by doubledouce on 2007-11-24
Thanks man!
Time to get rid of windows for ever. :)

---

### Post by Pumalite on 2007-11-24
You are welcome. Good luck.
(mark this thread as solved)

---

