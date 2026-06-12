---
title: "Install 7.10-server with raid 5 or raid 10 problem"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by fabiotemp on 2008-02-11
Hi everybody.
i'd like to create a server using ubuntu 7.10 server with 4hd sata2 in raid 5 or 10. I've read many guides and howtos but they don't work for me. The raid controller is a cheap bult in intel controller so i can use just a fake raid. The system would be single boot, so just linux.
The point is that, if during the setup i choose manual partition of the hd, i cannot create a raid 5 because it says that the devices are already in use (it finds a md0_raid5 in use). How can i umount it? Or is it a bug of the installer?
Moreover, how to create a raid 10 during the setup? Options are just for raid 0, 1 and 5.
I found a partial solution installing the system and booting from a 5th hd and then moving all the data part in a partition raid 10 created after the setup, using mdadm and webmin. It works. But what if the 5th hd crashes?
However the big problem of this solution is that sometimes the computer doesn't reboot well because during the initialization, it happens that the 5th hd (with boot partition) is seen as hd(4,0) and other times it is seen as hd(0,0) and grub complains, so i have to modify the value of hd() in the boot screen.
But of course this cannot be tolerated as i have to work on the server from remote and at least boot shoul d not have problems...

Any idea about raid 10 or 5?
And how to solve boot problems?

Cheers!

---

