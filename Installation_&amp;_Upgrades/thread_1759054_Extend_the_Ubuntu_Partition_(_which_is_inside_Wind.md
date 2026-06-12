---
title: "Extend the Ubuntu Partition ( which is inside Windows )"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by arul001 on 2011-05-15
[SIZE=2]Hi everyone ,

I have installed Ubuntu 11 inside Windows 7 .
Initially i had allocated 8 GB for ubuntu in wubi installer . 
Now i've a free space of about 1.5 GB only .

I've decided to install Oracle and you know  it requires at-least 5 GB space to properly work .
How can i extend the partition ?

I've installed GParted and it doesn't detect this ubuntu partition . ( since it's inside ntfs )

I've attached the screenshot of GParted .

( I'm not sure if this question was previously posted . )[/SIZE]

---

### Post by lindsay7 on 2011-05-15
Since both partitions are ntfs, you can change the partition size using windows.  I would make sure that you back everything up before doing anything with your partitions. I have had bad luck with changing windows partition sizes like losing the system.  I think you can find what you need under "disk management" in the control panel.

I would **[COLOR="Red"]not[/COLOR]** use Gparted to change a windows system partition in any way.

---

### Post by arul001 on 2011-05-15
[SIZE=2]Yep , i've always used the Disk management utility in WIndows .

But it will detect only the ntfs and can you please explain how to change the Ubuntu partition ?
[/SIZE]

---

### Post by lindsay7 on 2011-05-15
Ok, I misunderstood you.  I have not done this but it looks complicated and I would not risk my windows installation to try this. I would say that If you like Ubuntu, you should do a real dual boot and repartition as you see fit. Here is some info on what you are looking for, good luck. and Back up, back up, back up.

[http://ubuntuforums.org/showthread.php?t=633857](http://ubuntuforums.org/showthread.php?t=633857)

---

