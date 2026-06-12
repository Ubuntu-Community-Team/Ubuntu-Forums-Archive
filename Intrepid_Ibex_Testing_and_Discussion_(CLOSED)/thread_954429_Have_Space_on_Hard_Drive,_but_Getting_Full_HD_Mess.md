---
title: "Have Space on Hard Drive, but Getting Full HD Message"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-10-21
Under properties of my home folder, it says that I have 7.4 GB free; however, when I go to download [Knoppix 5.3.1]("http://torrent.unix-ag.uni-kl.de/"), I get a message that I am out of space.   What can I do to fix this problem?  

Note: I just fixed another problem [here]("http://ubuntuforums.org/showthread.php?t=954412").  I was unable to get into the "Lost+Found" there.  Not sure if these two are related are just coincidence.

---

### Post by chrisccoulson on 2008-10-21
Sef: What is the output of 'df -h'. Perhaps you're running low on /tmp?

---

### Post by Idefix82 on 2008-10-21
If you are installing it through Synaptic then the two folders I would check are /var and /usr. Var is where Synaptic stores the downloaded package and /usr is where it will install the software. If one of them is on a separate partition then the space on /home is not going to be of much use to you.
If /var is full then you can just delete the temporary Synaptic files. If /usr is full then I am afraid you will either have to uninstall something or change your partitions to transfer some space from /home to /usr.

---

### Post by Sef on 2008-10-21
df -h results:

> Filesystem            Size   Used   Avail Use% Mounted on
          /dev/sda1               9.2G  8.2G   528M   95%     /
          tmpfs       1004M       0    1004M    0%     /lib/init/rw
         varrun                     1004M  112K 1004M    1%    /var/run
         varlock                   1004M       0    1004M    0%     /var/lock
         udev                         1004M  2.8M  1002M     1%    /dev
         tmpfs                     1004M  404K  1004M     1%    /dev/shm
         lrm                          1004M   2.4M   1002M      1%   /lib/modules/2.6.27-7-generic/volatile
        overflow                   1.0M  1.0M          0     100%   /tmp


What's the best way to clean out that /tmp file?

---

### Post by chrisccoulson on 2008-10-21
You have an emergency overflow /tmp partition due to a lack of space on you root filesystem, so you really need to clear some space on the root filesystem and then reboot. What does 'sudo du -h --max-depth=1 /' show? (this may take a little while).

The most likely culprit is the apt cache. Try running the following to see how much space it frees up from your root filesystem:
```
sudo apt-get clean
```

---

### Post by Sef on 2008-10-21
> You have an emergency overflow /tmp partition due to a lack of space on you root filesystem, so you really need to clear some space on the root filesystem and then reboot. What does 'sudo du -h --max-depth=1 /' show? (this may take a little while).

I get this message:

> 369M    /var
1.1M    /root
du: cannot access `/proc/9005/task/9005/fd/3': No such file or directory
du: cannot access `/proc/9005/task/9005/fdinfo/3': No such file or directory
du: cannot access `/proc/9005/fd/3': No such file or directory
du: cannot access `/proc/9005/fdinfo/3': No such file or directory
0    /proc
8.1M    /sbin
4.4M    /lib32
4.0K    /srv
du: cannot access `/home/sef/.gvfs': Permission denied
4.8G    /home
4.0K    /opt
8.0K    /media
4.0K    /mnt



sudo apt-get clean does not help.

Also I have a problem opening synaptic....not sure if the problems are related or not; hence [another thread]("http://ubuntuforums.org/showthread.php?p=6005760#post6005760").

---

### Post by nystire on 2008-10-21
If you look at the output from "df -h", / is 95% full. You have 528Mb free on it.

---

### Post by chrisccoulson on 2008-10-21
Yeah, that's a bit odd actually. Have you tried rebooting? The overflow /tmp is most likely what is causing your problem, but it shouldn't be created unless there is less than 1MB of space left.

---

### Post by Seq on 2008-10-21
By default you will have a certain percentage (5%) of your filesystem reserved for root useage (if your filesystem is full, you'll want the system to run still, etc).

You can [calculate your block percentage]("http://blog.bigsmoke.us/2008/09/15/ext3-reserved-block-count") manually, and reset it using "tune2fs -m X", where X is whatever percentage you want to use (I use 1).

You should free up some space and/or get a bigger disk and/or separate /home to said bigger disk.

---

### Post by chrisccoulson on 2008-10-21
> **Seq said:**
> By default you will have a certain percentage (5%) of your filesystem reserved for root useage (if your filesystem is full, you'll want the system to run still, etc).

You can [calculate your block percentage]("http://blog.bigsmoke.us/2008/09/15/ext3-reserved-block-count") manually, and reset it using "tune2fs -m X", where X is whatever percentage you want to use (I use 1).

You should free up some space and/or get a bigger disk and/or separate /home to said bigger disk.

You're right, but that 5% is hidden from the output of df (or at least I think it is). df shows the percentage of the available space remaining, and the available space doesn't include the 5% reserved space. So, if df says the drive is 95% full, then it is really only 95% of 95% full (90.25%).

---

