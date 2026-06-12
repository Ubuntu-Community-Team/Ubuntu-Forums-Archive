---
title: "Query regarding partitions"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by Vormeph on 2013-07-17
So I want to run some tests on partitions and knowing how they can work. **I'm running Ubuntu 13.04 64-bit on a VirtualBox.**  1. I've successfully created a /home partition and Ubuntu boots fine on the virtual machine; however the home folder is situated in the /root partition, instead of the /home partition. How do I fix this so that the home folder is in the /home partition?  2. I have two hard drives on this virtual box: each 20 GB. If I want to use the storage on my second hard drive, how do I go about this? If I intend to add 10 GB of storage from my SECOND hard drive to the /root partition on my FIRST hard drive, how do I do this?

---

### Post by oldfred on 2013-07-17
I do not know about VirtualBox and what idiosyncrasies that may create. 

When you install you have to use manual install or something else and choose which partition is /home and mount that. If it also has older data you want to keep you must be sure NOT to check off the format box.
You can convert an install to use another /home. Either move a home or add fstab entrires like this, if it already exists you can skip rsync, but you may want some of the settings and then should run rsync anyway:
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You cannot directly add space from one partition into another unless you use LVM. But you can mount partition and link folders from that partition into your /home so it seems like it all is one space.
      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by Vormeph on 2013-07-17
Would it be more logical to dedicate the second hard drive to a /home partition and mount the home folder in that instead? That way, I can dedicate the swap and /root partitions to the first hard drive. What's the recommended partition size for swap by the way?

---

### Post by oldfred on 2013-07-17
I prefer to have the entire bootable system on one drive (actually I have a full bootable system on every drive), so I know it will boot. Then I have data partitions on other drives that I link into my installs.
But you can have /home on the other drive if you desire.

How much RAM do you have? The old rule was 2X when you only had 256 or 512MB of RAM. Then it became 1X with more RAM primarily to support hibernation. But if not using hibernation then 2GB is plenty as just in case. Some with lots of RAM 8GB or more may not have any swap although I still suggest some.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Vormeph on 2013-07-17
> **oldfred said:**
> I prefer to have the entire bootable system on one drive (actually I have a full bootable system on every drive), so I know it will boot. Then I have data partitions on other drives that I link into my installs.
But you can have /home on the other drive if you desire.

How much RAM do you have? The old rule was 2X when you only had 256 or 512MB of RAM. Then it became 1X with more RAM primarily to support hibernation. But if not using hibernation then 2GB is plenty as just in case. Some with lots of RAM 8GB or more may not have any swap although I still suggest some.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I have 8GB of RAM. Should I still use 2GB of swap then?

---

### Post by oldfred on 2013-07-17
I would, but it is up to you and maybe how you use system. To use all that RAM you just about have to load every application or edit videos which may use an unlimited amount of RAM. But if you do not load lots of apps and check use occasionally with free then you may not need swap.

Free may show all RAM in use as Linux caches apps as you often go back and reuse an app. But if needed and not using an app then that RAM is released and reused. Only if all apps are currently active then is RAM fully used.

I had not looked lately and am a bit surprised that I had used some swap with my 4GB of RAM. I show more swap than I suggest only because installer finds all the swap partitions- one on each drive. I have several and default find all.

```
fred@fred-Precise:~$ free
             total       used       free     shared    buffers     cached
Mem:       4048520    3726044     322476          0    1605776    1033024
-/+ buffers/cache:    1087244    2961276
Swap:      7268664        900    7267764

```

---

### Post by Vormeph on 2013-07-19
I've now installed Ubuntu, overriding my previous Linux installation: Xubuntu. I had 8GB of swap with the latter, and now I have partitioned my hard drive to accommodate 2GB instead. In both distros, none of my swap is being used. Regardless, I have manually partitioned my new Linux successfully and mounted the home folder to the /home partition on my second hard drive. I used the below link and so far nothing catastrophic occurred; not unless I wanted to. :-P  [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) - for anyone interested.  -SOLVED-

---

### Post by oldfred on 2013-07-19
Glad you got it working. :)

---

