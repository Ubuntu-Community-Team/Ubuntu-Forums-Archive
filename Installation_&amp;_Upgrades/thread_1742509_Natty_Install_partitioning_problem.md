---
title: "Natty Install partitioning problem"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by merlinus on 2011-04-28
When I choose the manual partitioning scheme (the bottom radio button), I cannot specify mountpoints manually for some of my partitions.

I have tried clicking in the mountpoint box, to no avail.  The only choices I have are in the dropdown menu.

My current partitions include ones for /data, /storage, and /art, in addition to / and /home.

---

### Post by Hedgehog1 on 2011-04-28
The non-standard mount points will need to be added to the fstab file after install.  You will need to install '/' and '/home' now, and add the other back in after the install.

You can save your current /etc/fstab file to a safe place so you can harvest those lines later.


***The Hedge***

:KS

---

### Post by merlinus on 2011-04-28
Thanks for the info.  The change from 10.10 and all other releases seems absurd, in terms of not being able to manually enter a mountpoint.  I fail to understand the reason for this.

Another question, por favor.  Since I have a separate /home partition, what should I put in for user when prompted?  I am afraid if I put in my existing username then the install will overwrite everything in that directory.

---

### Post by Hedgehog1 on 2011-04-28
> **merlinus said:**
> Thanks for the info.  The change from 10.10 and all other releases seems absurd, in terms of not being able to manually enter a mountpoint.  I fail to understand the reason for this.

Another question, por favor.  Since I have a separate /home partition, what should I put in for user when prompted?  I am afraid if I put in my existing username then the install will overwrite everything in that directory.

I know there is a thread about this happening.  I suspect that the poster didn't realize they had the 'format' box checked on the '/home' partition, and that is what really caused the issue.

As long as you **do not** check the format box on the '/home' partition, you will not lose any data.  **HOWEVER it is always wise to backup your data & documents before any install or large upgrade.**

***The Hedge***

:KS

---

### Post by merlinus on 2011-04-28
Yeah, that's what I thought.  I never format /home or my other partitions when installing a newer version, only /.

Thanks, and also for the reminder to always backup important data beforehand.

---

