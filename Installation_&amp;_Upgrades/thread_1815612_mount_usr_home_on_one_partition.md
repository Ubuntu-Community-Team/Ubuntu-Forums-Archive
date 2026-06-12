---
title: "mount /usr /home on one partition?"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by paridoth on 2011-07-31
Usually on a windows install the first thing I do is move the program files and users folder tO my second hard drive or D: drive to increase performance and have more space.
 I know i can mount /home (equal to users in windows) to my second hard drive, but I don't know how, or even if i can mount the equivalent of program files to my second hard drive without partitioning it in half.
 Also would /usr even be what I want to mount? I wan't programs like gimp, firefox, and rythm box to load from my second hard drive so would I want /usr or something else?

thanks for your time.

---

### Post by ajgreeny on 2011-07-31
> **paridoth said:**
> Usually on a windows install the first thing I do is move the program files and users folder tO my second hard drive or D: drive to increase performance and have more space.
 I know i can mount /home (equal to users in windows) to my second hard drive, but I don't know how, or even if i can mount the equivalent of program files to my second hard drive without partitioning it in half.
 Also would /usr even be what I want to mount? I wan't programs like gimp, firefox, and rythm box to load from my second hard drive so would I want /usr or something else?

thanks for your time.
I think you are very confused about the siting of files and programs in Linux.

There is no real equivalent of **Windows\Program Files** folder because the whole filesystem works in a different way.  In linux there are many library files, a bit like the .dll files in windows, that are shared by lots of different applications, and the lib files are generally put in /usr/lib and the executables in /usr/bin.

Most linux users nowadays put /home on a separate partition, but not necessarily a separate disk, and I wonder if you are getting the two terms confused, as windows shows everything as separate drives, eg C:\  D:\ etc etc, even if they are just partitions on the same disk.  Some users do mount /usr as a separate partition, and there is nothing to stop you putting it on any disk you have in your computer, but if you want both /home and /usr on a second disk, you will certainly have to use separate partitions for each.

I personally suggest you forget about your windows ideas and preconceptions, and use just separate / (root), and /home partitions, along with the required swap.  Root normally needs about 10-15GB, swap approximately 2-4GB, and /home can be as large as you can manage as that is where all the data files will sit.  As an example, my / root partition (the OS itself) is 10GB, and even after a year of installing everything I need in this version of ubuntu, 10.04, it uses 4.3GB of that space, and don't forget my / root partition contains everything except my data files, so it includes /usr.

Have a good read of [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) for lots of info on the details of the linux filesystem layout.  It may help you decide.

---

### Post by paridoth on 2011-07-31
So would mounting /usr on a separate hd from / give me a performance boost for loading programs as they wouldn't be bottle necking my main hd that has /?

---

### Post by ajgreeny on 2011-07-31
> **paridoth said:**
> So would mounting /usr on a separate hd from / give me a performance boost for loading programs as they wouldn't be bottle necking my main hd that has /?
Not in my experience, no.

---

### Post by paridoth on 2011-07-31
thanks for your help =)

---

