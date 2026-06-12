---
title: "Software updater:  Not enough disk space"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by SiflOlly on 2014-07-26
I'm getting this error when trying to install the auto updates:  

The upgrade needs a total of 79.6 M free space on disk '/boot'. Please free at least an additional 8,131 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I've done the sudo, and nothing happens.  I have many hndreds of gigs of disk space.  Any ideas?

---

### Post by bapoumba on 2014-07-26
Please post the outputs of :
```
df -h
df -i
```

---

### Post by ibjsb4 on 2014-07-26
```
sudo apt-get autoclean
```

Is suppose to clean old kernels out of /boot.  Just be sure its not removing any necessary packages.

---

### Post by SiflOlly on 2014-07-26
> **bapoumba said:**
> Please post the outputs of :
```
df -h
df -i
```

matt@OptiPlex-745:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  143G   30G  106G  22% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        388M  1.1M  387M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  156K  1.9G   1% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/sda1                    236M  156M   69M  70% /boot
/home/matt/.Private          143G   30G  106G  22% /home/matt
matt@OptiPlex-745:~$ 


matt@OptiPlex-745:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 9494528 282830 9211698    3% /
none                         496483      2  496481    1% /sys/fs/cgroup
udev                         492680    504  492176    1% /dev
tmpfs                        496483    504  495979    1% /run
none                         496483      4  496479    1% /run/lock
none                         496483      7  496476    1% /run/shm
none                         496483     25  496458    1% /run/user
/dev/sda1                     62248    317   61931    1% /boot
/home/matt/.Private         9494528 282830 9211698    3% /home/matt
matt@OptiPlex-745:~$

---

### Post by bapoumba on 2014-07-26
/boot is 70% full with 69M free, which is not enough for your upgrade.
Did you run ibjsb4's command ? That should clear unused kernels. Here is a link for lubuntu, but that will work on any flavor : [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
I always keep the current one (the one showing up with **uname -a**) *and* the last working one, which usually is the previous one.

---

### Post by SiflOlly on 2014-07-28
> **bapoumba said:**
> /boot is 70% full with 69M free, which is not enough for your upgrade.
Did you run ibjsb4's command ? That should clear unused kernels. Here is a link for lubuntu, but that will work on any flavor : [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
I always keep the current one (the one showing up with **uname -a**) *and* the last working one, which usually is the previous one.


That command didn't work, but manually removing them did.  My question is how/why did I run into this problem?  Is this going to happen for future updates, or is my problem solved.  Why is my Ubuntu keeping these files around if they aren't needed?

---

### Post by ibjsb4 on 2014-07-28
My bad, I gave you the wrong command.  Its ..
```
sudo apt-get autoremove
```

---

### Post by bapoumba on 2014-07-28
> **SiflOlly said:**
> That command didn't work, but manually removing them did.  My question is how/why did I run into this problem?  Is this going to happen for future updates, or is my problem solved.  Why is my Ubuntu keeping these files around if they aren't needed?
Your /boot is not that big, so you will need to keep an eye on it.

> **ibjsb4 said:**
> My bad, I gave you the wrong command.  Its ..
```
sudo apt-get autoremove
```
Oh dear, yes.. Saw your post, probably read autoclean but understood autoremove.. Did not even notice :D

---

### Post by ibjsb4 on 2014-07-28
Some handy maintenance commands

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by SiflOlly on 2014-08-14
Sorry to dig this up... So you are saying that everyone that has Ubuntu has to continually manually delete these or run that auto delete command every time they update?  If so, I think I might be done with this, because that is pretty absurd.

---

### Post by ian-weisser on 2014-08-15
No. It's a bug that only affects users with encryption or LVM or some other reason to have a separate /boot.
The majority of users, who do not have /boot, do not suffer from the bug.

Feel free to poke around /etc/kernel/postinst.d/apt-auto-removal , the script that marks old kernels as eligible for autoremoval when a new kernel is installed.

---

### Post by TechieZero on 2014-08-15
I am in essentially the same boat.

I have an inspiron 910 that I loaded Lubuntu on. After the install finishes I am left with about 250 meg...

I do have an additional SD card in the machine that has about another 1/2 gig. Is there a way to redirect the file manipulations of the Lubuntu's Auto Update installer to take advantage of the SD card?

---

### Post by TechieZero on 2014-08-15
> **SiflOlly said:**
> Sorry to dig this up... So you are saying that everyone that has Ubuntu has to continually manually delete these or run that auto delete command every time they update?  If so, I think I might be done with this, because that is pretty absurd.

You could automate this by going to the Lubuntu menu select Preferences > Default applications for LXSession, then click on the Autostart tab and under "Manual autostarted applications" type the command you want to do, then click the "+ Add" button on the left.

---

### Post by ian-weisser on 2014-08-15
> **TechieZero said:**
> I do have an additional SD card in the machine that has about another 1/2 gig. Is there a way to redirect the file manipulations of the Lubuntu's Auto Update installer to take advantage of the SD card?

Change package manager settings? Not really.
However, you can store parts of your filesystem, like var/cache/apt/archives on the SD card, so the actual packages live there instead of the HDD.


> **TechieZero said:**
> You could automate this by going to the Lubuntu menu select Preferences > Default applications for LXSession, then click on the Autostart tab and under "Manual autostarted applications" type the command you want to do, then click the "+ Add" button on the left.

Well bug is that the packages are not marked as eligble for autoremoval. Automating the autoremoval command won't help...autoremoval is *already* automatic.

---

