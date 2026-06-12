---
title: "Installing Ubuntu 10.10 onto an existing RAID 0 array?"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by kskwerl on 2011-04-17
Sup everyone. I have 4 OCZ Agility 2's in RAID 0 on my comp which is currently running Windows <.<

I was wondering how hard it is to install Ubuntu 10.10 onto that existing RAID array. Is it even possible?

I don't won't to dual boot. I hate windows. Is it possible the Ubuntu install will just see the RAID 0 array as one logical disk and I can "Use the entire disk" and go ahead and install. That would be nice! lol

Thanks for any help in advance.

---

### Post by Hedgehog1 on 2011-04-17
IF you are running a true hardware raid, then you can run Ubuntu on this system without and changes.  To test this, boot from a LiveCD/LiveUSB, select the 'TRY' option and then open your Windows 'disk'.  If you can both see it and open pictures and such, you can install on it as is.

If your RAID is a software RAID and it does not appear or work from the LiveCD/LiveUSB, you still have options.

Before we tell you about the RAID options, Linux/Unix offers the ability to combine drives into larger 'file systems'.  Here is an example of how this is achieved:

[IMG]http://img840.imageshack.us/img840/4129/laptophd.png[/IMG]

Very large servers can be built in the same way, also without using RAID:

[IMG]http://img853.imageshack.us/img853/6228/serverhd.png[/IMG]

The idea is that you can combine the drives using a method like this, and end up with drives that are still readable if separated.

The other two non-hardware RAID options for Linux are FakeRAID and Software RAID.  There are some limits using Software RAID and RAID 0.


***The Hedge***

:KS

---

### Post by kskwerl on 2011-04-17
Thanks for your prompt reply. I ended up getting it to work, it was a software raid. 

Maybe you could take a look at this video I used. This guy uses 2 drives. I used 4 SSD's and everything he did for the second drive, I did for the other 3 drives o.O

I was able to install Ubuntu on the raid volume but I'm getting this "one or more disks are failing" icon at the top. The reason I followed that video is because I really have no clue how to set up swap partitions etc in linux. So I kinda need step by step instructions w/ pictures. I prob messed something up by doing that. 

However I know the drives are failing I just think its got to be the way I set up the raid and partitioned it.

Here is the video:
[http://www.youtube.com/watch?v=-x2rZe2Z9as&feature=related](http://www.youtube.com/watch?v=-x2rZe2Z9as&feature=related)

---

### Post by kskwerl on 2011-04-17
Here are some screen shots. I have no problem reinstalling. I have 4 SSD's but maybe I should just use 2 to make it easier? This array seems functional and I don't know if you can tell anything by these errors but here's some screen shots.

---

### Post by Hedgehog1 on 2011-04-17
> **kskwerl said:**
> Here are some screen shots. I have no problem reinstalling. I have 4 SSD's but maybe I should just use 2 to make it easier? This array seems functional and I don't know if you can tell anything by these errors but here's some screen shots.

Sorry - I just cannot read the screen shots - can you zoom in on the area with the error message, please?

If the message is for a single SSD via Smart Status, the falure message may be real as these errors come from the drive/ssd itself based on the system on-board the disk.  Some example I have seen are like this:

[IMG]http://img225.imageshack.us/img225/7057/diskfail03.png[/IMG]

Also - that video showed you how to do the supported Software Raid for Ubuntu - so you are setup using the proper method.  **Well Done!**


***The Hedge***

:KS

---

