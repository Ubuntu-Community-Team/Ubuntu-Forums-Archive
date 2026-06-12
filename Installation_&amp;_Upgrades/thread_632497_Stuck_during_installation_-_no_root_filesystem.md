---
title: "Stuck during installation - no root filesystem"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by dvijaydev46 on 2007-12-05
Hi i have one hard disk  and had three partitions.  In C; xp, in D: vista ultimate. and E was my backup partition. Now I created an ext2 partition and a swap partition using partition magic. My Ubuntu 7.04 is loading perfectly from CD. but when i  try to install install Ubuntu after allocating ext2 for boot/ media and swap for swap it doesn't let me install Ubuntu. it says "no root file system installed. please correct this from partition menu". I'm struck up here. Please give me a solution. 
Thanks

---

### Post by Pumalite on 2007-12-05
Start again. You have to use Vista partitioner to allocate space for Ubuntu. Otherwise Vista won't let you run anything in that computer.

---

### Post by dvijaydev46 on 2007-12-05
Thanks for the quick reply. But I have had the same problem when I had no vista installed in my system probably  one year ago.  But I some how managed to install Ubuntu 6.10 then and I really don't remember that. I think It's not to do with vista.

---

### Post by aysiu on 2007-12-05
> **dvijaydev46 said:**
> Hi i have one hard disk  and had three partitions.  In C; xp, in D: vista ultimate. and E was my backup partition. Now I created an ext2 partition and a swap partition using partition magic. My Ubuntu 7.04 is loading perfectly from CD. but when i  try to install install Ubuntu after allocating ext2 for boot/ media and swap for swap it doesn't let me install Ubuntu. it says "no root file system installed. please correct this from partition menu". I'm struck up here. Please give me a solution. 
Thanks
You need a / partition

That's the root filesystem

Having /media, /boot, and swap isn't enough.

Actually, I don't even know why you have /media and /boot

What you really need is / and swap. You might want to make a /home.

More details here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

