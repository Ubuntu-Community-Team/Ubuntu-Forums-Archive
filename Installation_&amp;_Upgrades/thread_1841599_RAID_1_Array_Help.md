---
title: "RAID 1 Array Help"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by dementech on 2011-09-09
Hey Forum,

I'm a new user here and pretty new to Ubuntu administration, but I like learning.  Here's what I got: I have a production backup server running 9.10 with a 1TB RAID 1 array running just fine. I have been asked to add an extra 2TB RAID 1 array to the server for storage.

Now I'm experimenting with sandbox hardware, 11.04 server, a Silicon Image Sil3124 Sata I/II PCI-X32/64 bit host controller card, and 4 sata drives: 1 - 500GB, 1 -250GB and 2 - 2TB.
This time around I used the card to setup 2 RAID1 arrays: 1 - 200GB with a 2GB swap and 1 - 2TB.  Being new and all I'm not really sure if all I am seeing is normal.  I've been poking around a lot on the web and started seeing things like fake-raid and such.

Can anyone give some pointers on the best way to go with install?
I mean like from your experience should I:
use the controller card to setup the arrays, or is it best to use Ubuntu's Partitioner?

What kind of issues have you run in to using the controller card?

Thanks in advance for any constructive input.

---

