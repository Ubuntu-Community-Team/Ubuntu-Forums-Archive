---
title: "System Partition too small"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by chilloutmo on 2011-11-11
Hello everybody,

I just reinstalled Ubuntu 11.10 and used the "delete Ubuntu and reinstall Ubuntu" function in the installation menu. There is nothing wrong with the system in itself, as a matter of fact the reinstall really speeded things up after I had only done upgrades and no clean installs since 10.04. 

The problem I have is that the installer decided to put my whole system on 7.5GB although my old one was on about 120GB. Now I don't have enough space in my home folder and need to mount an external file system which is empty and has loads of free space (about 100GB). 

That's why I would like that my system partition swallows the empty partition. How can I do that?

I attached a GParted screenshot: dev/sda7 is my system partition, dev/sda6 is the big empty partition I would like to integrate into the system partition. 

I would really appreciate any help.

Thank you very much.

chilloutmo

---

### Post by darkod on 2011-11-11
Did you have a separate /home partition? What is/was /dev/sda6?

---

### Post by chilloutmo on 2011-11-11
In my previous Ubuntu 11.10 install, dev/sda7 (where /home is currently) used to include dev/sda6. For no apparent purpose it just created another huge partition. What I would like to do now is just have it like it was before, i.e. that dev/sda7 (where /home is) is a very large partition, because currently, with my documents alone, I am already almost at the limit. And I can't add any music or picture into the respective home folders because I don't have enough space.

---

### Post by darkod on 2011-11-11
I have never used (or seen) an option called "delete and reinstall ubuntu" but I always use manual option so I don't pay too much attention to the auto options.
But what I do know is that ubuntu will never delete existing partition before checking with you to make sure it doesn't delete your data. I think that's what happened. It looks like the previous swap is still there (/dev/sda5) and the previous root (/dev/sda6). I don't know what this option for installing is supposed to do but it doesn't seem to be reinstalling ubuntu.

But lets talk about the current problem: Since you were happy to delete and reinstall, does that mean you have your documents/data backed up somewhere?
In that case, just start another installation, in the partitioning step select Custom/Manual, when the list of partitions shows up select one by one and delete /dev/sda5 trough /dev/sda7. That should leave one big unallocated space inside your extended partition (/dev/sda3).

From that space create new root and swap partitions with the size you want. I would recommend also a separate /home partition, it makes future clean installs much easier.

That should do it. Note that deleting the partitions suggested above will delete all data on them. Only you know if you have a backup of it. Don't delete anything before backing up. :)

---

### Post by chilloutmo on 2011-11-11
Thank you very much for your help, but I ended up finding another solution. With a live cd it is possible to use GParted in a way to move and resize partitions. It was a bit complex because partitions can only increase in size at the expense of their direct neighbour so I had to move a lot of them but it worked out pretty much exactly like I wanted. 

Thanks anyway!

chilloutmo

---

