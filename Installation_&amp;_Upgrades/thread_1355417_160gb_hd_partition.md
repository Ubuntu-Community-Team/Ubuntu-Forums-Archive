---
title: "160gb hd partition"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Arpy on 2009-12-14
I partitioned my HD manually as usual during an ubuntu installation. Usually I just make a /boot / and swap partition, however this time I decided to take it a little further and made the following.

/boot 125mb
512 mb Swap
/ 4gb
/urs 70 gb
/tmp 4gb
/var 4gb
/home 76gb
540 mb swap

Is this a good layout, or should I repartition if I did something wrong? (Yes there are two swaps each on different ends of the drive)

---

### Post by oldfred on 2009-12-15
There is no real advantage to two swaps, some think having them on different drives may make it faster but if you have a lot of memory you do not use swap except for hibernation or rarely when running many very large applications.

Ten years ago when installing a red hat desktop it was set up with all the partitions as most servers were that way. Now there is no real advantage and some disadvantage unless you can size the partitions perfectly for your use. Even boot does not need to be separate unless you have an old system with BIOS boot sector limits.

Many recommend the separate /home and I just changed to it but see no advantage since all my data is now in a separate data partition that I can mount with all the versions I install since I have 3 versions of linux currently. The actual data in my /home is very small and just about only the hidden config files, so it is easy to backup. But I found my 3 year old home directory, once the data was removed, still had lots of stuff I did not want to automatically copy to my new /home. Much housecleaning was still required.

---

### Post by gordintoronto on 2009-12-15
I suggest 8 GB at least for root.  You probably won't need it, but if it runs out, it's quite annoying.

I assume /urs is a typo, and you mean /usr.  If so, it doesn't need anywhere near that much room.  Actually, come to think of it, I don't see any advantage to having more than swap, root and home.  Maybe /var if you do web site development.

---

### Post by Ginsu543 on 2009-12-15
If you are going to create separate /boot, /usr, and /var partitions, you don't really need a large / partition. This is how I have my 2 x 74 GB RAID0 array partitioned and it has worked really well for me:

/ = 1 GB
/boot = 100 MB
/usr = 12 GB
/var = 6 GB
/opt = 1 GB
/home = 118 GB
swap = 1 GB

Having said that, it's almost certain that creating this many partitions on a home system is overkill (I just wanted to try it out). You really only need /, /home, and swap. I have found having a separate /home partition extremely helpful even though I too have all my data on a separate data drive, because the /home partition keeps all the configuration files for the programs I like to install and use. If I ever have to reinstall (because I broke the system or what not), I keep the /home file intact and reinstall the OS. Then, as I reinstall each program I need, it automatically "remembers" all the settings I made previously and I don't have to reset it all. This seriously shaves two, three hours from the time it takes to get my system back to how I like it (I confess I am quite anal about my computer and I like it to be just "so").

---

