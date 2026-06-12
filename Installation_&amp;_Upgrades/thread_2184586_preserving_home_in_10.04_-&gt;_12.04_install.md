---
title: "preserving /home in 10.04 -&gt; 12.04 install"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by bookherd on 2013-10-29
I want to update my netbook from 10.04 to 12.04.  Should I create a separate partition for /home in order to preserve my data, or is there an option on the 12.04 installer that will allow me to keep it?  (Essential data is backed up online, but I'd really prefer to avoid downloading it all again.)

---

### Post by papibe on 2013-10-29
Hi bookherd.

I would recommend a clean install, because...
> **bookherd said:**
> ...there an option on the 12.04 installer that will allow me to keep it?
Yes, it is not evident, but you should go advance when formating your hard disk, and then select to not format your current /home and keep the mount point, and just reformat the root (/) partition.

Regards.

---

### Post by bookherd on 2013-10-29
Exactly what I was looking for, papibe, thanks for the swift reply!

---

### Post by bookherd on 2013-10-29
Okay, now that I am in the installer, I see that I need more info.

> select to not format your current /home and keep the mount point, and just reformat the root (/) partition.

How do I select to not format /home in the "advanced" install option?  Remember that my /home is not currently in a separate partition.  My current partitions are sda1 ext4 (153.9 GB), and sda5 swap (6.2 GB).  Is there a way to save /home without putting it into a new partition?

---

### Post by papibe on 2013-10-29
You either chose advance or manual and you'll be presented with a similar tool like Gparted.

There's a column to select if the partition should be format or not. Take a look at this: [Keeping the same home partition after a clean install]("http://askubuntu.com/questions/285212/keeping-the-same-home-partition-after-a-clean-install").

Regards.

---

### Post by bookherd on 2013-10-29
Okay. So just to be sure I understand: you are advising me to create a separate /home partition before I do the install, correct?

---

### Post by papibe on 2013-10-29
Ohh, yes. Sorry If that wasn't clear.

A prerequisite for this is that your current /home is in its own partition.

Regards.

---

