---
title: "installing updates"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by David2009 on 2015-05-07
When the "updates" icon appears I am no longer able to install the updates.  I'm told that I must delete "x" number of megabytes of data.  I have a 300mb hard drive that barely has anything on it, apart from the OS.

Using Gparted, a tech came over and said that the error is coming from my having it set to "secure". 

I was able to get updates installed by going to a terminal and entering:
sudo apt-get update and then sudo apt-get upgrade

This installs the available updates.  

I had hoped it would update the update icon, but that's not the case.

A suggestion to me was consider updating the manager core.  Useful suggestion?

Thank you for your help.

David

---

### Post by ajgreeny on 2015-05-07
I think you must mean a 300GB drive, not MB, but aside from that, I do not know what you (or your tech person) mean by 
> Using Gparted, a tech came over and said that the error is coming from my having it set to "secure" 
Has your system been installed using encryption?
If so, you will have a small separate /boot partition which can get filled up with unnecessary old kernels.

Is the update icon you speak of the notification icon that appears in the panel when updates are available?

Run command ```
ls /boot | grep vmlinuz && df -m
```in terminal which will show all the kernel version on your system, then the partitions on disk and free space on all of them.

---

### Post by David2009 on 2015-10-29
Sorry for the long time between posts.  I moved, and started a new job.  Anyway, I have the information:

david@david-Satellite-A305:~$ ls /boot | grep vmlinuz && df -m
vmlinuz-3.13.0-43-generic
vmlinuz-3.13.0-44-generic
vmlinuz-3.13.0-45-generic
vmlinuz-3.13.0-46-generic
Filesystem                  1M-blocks  Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root    296043  5687    275295   3% /
none                                1     0         1   0% /sys/fs/cgroup
udev                             1961     1      1961   1% /dev
tmpfs                             396     2       395   1% /run
none                                5     0         5   0% /run/lock
none                             1976     1      1976   1% /run/shm
none                              100     1       100   1% /run/user
/dev/sda1                         236   159        65  71% /boot
/home/david/.Private           296043  5687    275295   3% /home/david
 
I wonder what the vmlinuz editions are?  I thought I had downloaded the Ubuntu 14 LTS from the website.  What did I do wrong?

---

### Post by David2009 on 2015-11-01
If anyone has any ideas on how I might fix my problem, I need the help.  I can't install updates.  Yes, I used the "security" option during the initial installation.  If this was not the best choice, is there a way to remove that option?  Thank you.

David

---

### Post by David2009 on 2015-11-07
david@david-Satellite-A305:~$ ls /boot | grep vmlinuz && df -m
vmlinuz-3.13.0-43-generic
vmlinuz-3.13.0-44-generic
vmlinuz-3.13.0-45-generic
vmlinuz-3.13.0-46-generic
vmlinuz-3.13.0-66-generic
Filesystem                  1M-blocks  Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root    296043  6158    274824   3% /
none                                1     0         1   0% /sys/fs/cgroup
udev                             1961     1      1961   1% /dev
tmpfs                             396     2       395   1% /run
none                                5     0         5   0% /run/lock
none                             1976     1      1976   1% /run/shm
none                              100     1       100   1% /run/user
/dev/sda1                         236   196        28  88% /boot
/home/david/.Private           296043  6158    274824   3% /home/david

Good morning.  Would you, please, help me to correct the errors of having the extra kernels and not having room for updates?
 
Thank you.

David

---

### Post by David2009 on 2015-11-07
Success!  I found a message mentioning UBUNTU TWEAK, so I found the version that corresponded with 14.04, installed it, and found the utility to remove old kernels.  

Here's what I have now:
 
david@david-Satellite-A305:~$ ls /boot | grep vmlinuz && df -m
vmlinuz-3.13.0-66-generic
Filesystem                  1M-blocks  Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root    296043  5267    275716   2% /
none                                1     0         1   0% /sys/fs/cgroup
udev                             1961     1      1961   1% /dev
tmpfs                             396     2       395   1% /run
none                                5     0         5   0% /run/lock
none                             1976     1      1976   1% /run/shm
none                              100     1       100   1% /run/user
/dev/sda1                         236    47       177  21% /boot
/home/david/.Private           296043  5267    275716   2% /home/david

 
I found one of the kernels was using almost all of the available space.  Wow.  Anyway, thanks to ajgreeny for giving me the helpful command to find old kernels.


David

---

