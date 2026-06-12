---
title: "A question on partitioning and performance..."
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by Ozitraveller on 2005-03-31
I'm planning to do a rebuild when Hoary finally releases next week. I'd like to get some feedback on which is a good partitioning scheme. Currently I have a simple scheme /, swap, /home (Desktop). swap I set at 1gb and the performance is ok. I've tried less swap but performance fades off. 

I have a PII/400 with 2 X 10gb 7200rpm ide drives, and 389mb ram, 64mb Nvidia card. This is only a test machine, I do have a quicker pc.


If I create partitions for /usr, /var, /tmp (Workstation) will this offer better performance? Does creating partitions give better performance than the single bucket approach?

---

### Post by arctic on 2005-03-31
> 
If I create partitions for /usr, /var, /tmp (Workstation) will this offer better performance? Does creating partitions give better performance than the single bucket approach?

my personal experience is that it slows down the system as your root filesystem needs to mount more partitions and jump from partition a to b to c all the time. one root and one home partition along with swap is the best solution imho.

my sugestion:

hda
hda1 swap 800 mb
hda2 ext3 5gb /
rest for secondary linux distro if you want (maybe for recovery or tweaking, development,...)

hdb
hdb1 ext3  /home

---

### Post by alastair on 2005-03-31
I think you're fine as you are i.e.

/
/home
swap

The most important thing is to keep /home separate I think because it makes reinstalls, upgrades etc. a little easier (if required). Other schemes (/tmp, /var etc.) are more skewed towards server installs (for log files, cache etc.).

---

### Post by Ozitraveller on 2005-03-31
Thanks. I was hoping that tweaking the partitions would help.

---

