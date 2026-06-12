---
title: "failed to create enough space for installation"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by think13 on 2006-09-24
I installed Ubuntu once, and got mixed up with the partition.  The linux partition was the size I wanted the windows one to be.  So I removed the linux partition and expanded the windows one to its former size.  Big mistake, but I have fixed that.

Now I can run windows again, and I wish to install ubuntu correctly (from live cd).  I run the installer and get to the partition part.  When I try to make a partition, it says "Failed to create enough space for installation". 

I have searched this forum before and found that defragmentation should fix the problem.  I defragmented my hard drive using the windows defragmenter twice.  I still get the error message.

I have included (hope this works) screenshots of the error message and my partitions.

---

### Post by henriquemaia on 2006-09-24
[I]You failed to upload the images.

[/I]Nevermind. Not valid anymore.

---

### Post by think13 on 2006-09-24
Also, in the install, if I click on "manually edit partitions", the install freezes.

It looks like something may be wrong with the FAT32 partition. Could that be the problem?

And do I need to get rid of the 'extended' and 'linux-swap' partitions, that are left over from the previous Ubuntu install?

---

### Post by ajgreeny on 2006-09-24
If you're sure windows is properly defraged, run gparted from the live CD, or from knopix or anything which has gparted on it and delete all partitions EXCEPT your windows one.  This will get rid of your old linux ext3 and swap.  Now reduce the size of your windows partition to whatever you want.  Don't make any new partitions at this point, ubuntu will do this for you later

Now run installation of ubuntu again and when you get to the partitioning bit chose the largest unused space option (Can't remember the exact wording) which will be the size of the two you got rid of plus size of the reduction of your windows partition.  Should work without problem.

Good luck.

---

### Post by think13 on 2006-09-24
Ok, thanks.
Trying that now, I will let you know the results.

---

### Post by think13 on 2006-09-24
Thanks, it installed nicely now! The dual-boot with windows works great!

---

### Post by Efaustus9 on 2006-11-19
> **ajgreeny said:**
> If you're sure windows is properly defraged, run gparted from the live CD, or from knopix or anything which has gparted on it and delete all partitions EXCEPT your windows one.  This will get rid of your old linux ext3 and swap.  Now reduce the size of your windows partition to whatever you want.  Don't make any new partitions at this point, ubuntu will do this for you later


I was installing ubuntu on yet another one of my computers and ran into the same problem as this threads creator. I did a search and found this page and I followed the directions as quoted. When I went to designate partition space the smallest size it would allow was 18.9GB of the computers 40GB HD, about 9GB more then I want to designate, so I decided to forgo the installation for the time being. I shutdown and restart but instead of windows starting up I get "could not read from selected boot disk". I figured I would run recovery console but for some reason it wont take my admin password so now im stuck... suggestions anyone?

---

