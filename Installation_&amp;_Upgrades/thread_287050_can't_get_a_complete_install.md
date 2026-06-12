---
title: "can't get a complete install"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by george56 on 2006-10-28
I've got a dell dimension.  I'm using a ship-it version of dapper.  before installing I put an old (working) 8 gig hard drive in.  I boot off of the CD and it goes well until I answer who am I, where I live and the keyboard.  It's when I get to the partition question that it asks if I want to use the whole drive or not.  I selected initially, the entire drive, but after it hits 7% complete, it just hangs.  I cold start and go through the whole process, but when I select the "Install" icon, it runs off the CD for a few seconds and just stops.

(Before I did the first install, I wiped out the original partition.)

Help, please!

---

### Post by meng on 2006-10-28
You might try an alternate CD install, but you have to download and burn it yourself. However, you will have the option of going for Edgy if you like. How much RAM do you have?

---

### Post by george56 on 2006-10-28
I was trying to avoid buying a CD burner, but I guess I should anyway.

I have 256 MB of RAM.

Would a flash drive (1 GB) work for this?

Thanks.

---

### Post by meng on 2006-10-28
Although 192MB RAM is the advised minimum for a LiveCD install, I don't consider this a hard limit, and 256 MB is not much extra. Therefore I would strongly advise the alternate CD install.

I don't know for sure whether a flash drive would work, but I do know that you can use syslinux to boot from flash drives. The general instructions are here:
pendrivelinux.com
and although there isn't a specific tutorial for Ubuntu, you should be able to follow the same steps as for Knoppix.

---

### Post by Amorphous_Snake on 2006-10-28
I have the same problem, but with Edgy. I have 384 MB of RAM and I am trying to install Kubuntu 6.10.

[http://ubuntuforums.org/showthread.php?t=286954](http://ubuntuforums.org/showthread.php?t=286954)

Will the alternate CD work?

---

### Post by meng on 2006-10-28
Could be a badly burned CD. I had a very similar problem installing from the _Alternate_ 6.10 CD, was fixed with a re-burn. So consider re-burning the LiveCD or else trying the Alternate.

You'll notice I didn't advise the OP to reburn the LiveCD, because he has Shipit.l

---

### Post by Amorphous_Snake on 2006-10-28
I did a check from the boot screen of the CD. Also, when I used Nero to burn it, I chose a verify test and it was OK.

I will try to burn it again though, and using my other burner. I hope it's not an error with the HDD.

---

### Post by meng on 2006-10-28
If you're comfortable with a text-based installer (which is really just as easy to use as the graphical installer, IMHO) then by all means go for the Alternate CD.

---

### Post by pattymnaish on 2006-10-28
> **meng said:**
> If you're comfortable with a text-based installer (which is really just as easy to use as the graphical installer, IMHO) then by all means go for the Alternate CD.
 
Personally, I've had issues with the Alternate CD too. (For 6.06)

---

### Post by Amorphous_Snake on 2006-10-28
What do you mean with a "text installer" is it like the installation of Ubuntu 5.10?

---

### Post by meng on 2006-10-28
Yes it is.

---

### Post by Amorphous_Snake on 2006-10-28
For a minute there I thought "command line installation"!!!

If it's like Ubuntu 5.10, then that's easy!

---

### Post by dbott67 on 2006-10-28
> **george56 said:**
> ..it runs off the CD for a few seconds and just stops...

I had this issue with an early edgy beta.  As soon as I changed the time zone, the computer seemed to freeze.  Can you try installing without changing any of the default system values (date/time/location/time zone/etc.)?  Those options can be adjusted after installation --- about the only thing I entered was computer name, username & password & everything worked.

I've also had issues with CDs that were burned too fast, but you mention that they are "ShipIt" CDs, so I'm sure that it's probably not a burn issue.

The other thing I would try is a manual partition vs. automatic partition.

-Dave

---

### Post by Amorphous_Snake on 2006-10-29
I fixed my problems. Thanks meng!

[http://ubuntuforums.org/showthread.php?t=288257](http://ubuntuforums.org/showthread.php?t=288257)

---

