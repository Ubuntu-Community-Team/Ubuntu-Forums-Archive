---
title: "Upgrade to Kubuntu Gutsy, problem with partitions"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by mythik on 2007-09-28
My problem is not specific to upgrading, but only appeared due to upgrade.  

I recently tried the steps found here :  to upgrade form feisty to gutsy.  Unfortunately, I get an error saying my /boot partition does not have enough free space (needs 60 something MB, I only have 45 or so free on the partition).  First, is there a way for me to tell the upgrade to use a different folder for the work it needs to do and then later COPY the kernel/config all that stuff over to /boot later?

Secondly, this brings up a good point as to how big my /boot needs to be.  Mine is only 100 MB, and the first partition on a whole drive dedicated to kubuntu.  So, provided I can't copy the contents to boot afterwards, I guess that means I need to make /boot bigger.

I googled "partition magic linux" and came up with gparted/qtparted.  I installed qtpared, but cant mess with the partitions I need to...I'm assuming it's because I'm currently USING those partitions.  So then I realized I need to get a live disk and boot into that and mount the drives and then resize partitions.

So, is there an easier way to modify it while using the system?  I know partition magic would pretty much queue up the operations it needed to, reboot, and then would perform those operations.  Is there a program out there that does the same kind of thing?

---

### Post by ajgreeny on 2007-09-28
Get a copy of the gparted live CD, you'll find it easily with google or go here:-
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It won't do things the way you want but it's a great program and a small download of about 30MB and always worth keeping handy for any partition work you need to do.

---

### Post by mythik on 2007-10-01
> **ajgreeny said:**
> Get a copy of the gparted live CD, you'll find it easily with google or go here:-
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It won't do things the way you want but it's a great program and a small download of about 30MB and always worth keeping handy for any partition work you need to do.

Will gparted move my data if I resize some partitions or will it wipe out everything?  My drive is set up so that the order is "/boot  /swap  /"  with no unallocated space.  So if I have to, I can make the swap space just a bit smaller and expand /boot.

---

### Post by Tohvu on 2007-10-03
I actually ran to the same problem while trying to upgrade from 7.04 to 7.10 kubuntu

my setup is 
/ 10gb
/home 50gb
/boot 400mb

and I get the error saying my /boot needs to be 503MB minimum... whats going on?
and yea, is there any software that can handle resizing my boot partition, meaning I'd have to resize some other partition first to free up space. I know this works with windows filesystems. 

Please reply, need help :)

---

