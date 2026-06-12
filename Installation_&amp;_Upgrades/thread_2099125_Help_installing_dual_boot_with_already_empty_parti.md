---
title: "Help installing dual boot with already empty partition."
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by JohnCUbu on 2012-12-28
Help! I use Ubuntu everyday, but rarely get under the hood, so i still consider myself a beginner. 
I'm installing Ubuntu alongside windows 7. But i used to have this drive encrypted with truecrypt system encryption. I removed the encryption. This leaves windows on 73gb /dev/sta1 then /dev/sta2 is extended with /dev/sta5 a still encrypted  73gb partition i want to use for Ubuntu. There are 2 other partitions my hp machine uses for restoring windows.
When i try to install, it doesn't give the option to install alongside windows, so i have to pick "something else". I wanted to do that anyways to set partitions for swap, home, ect. 
But I'm not sure how to continue. Do i put the bootloader on /dev/sta? Should i go into my USB Ubuntu install, and wipe that partition first with gparted? Then set all the individual swap, home, ect. Then go install?
Any recommedations on partitions? I've had usr,var and the others on their own when I've installed on empty drives.

---

### Post by rajhanschinmay on 2012-12-29
ok

You are right till the what you want to do screen.

Now if u select first option, it will format or erase everything.
Generally u should select it if u r not sure.
But I suggest u select third option which is something else.

Now for Ubuntu, u need to give the following 3 partitions:
/, /home and swap.
Typically / can be 10GB, /home can be 10GB and swap can be 4GB.
If u have more disk space, then give more space.

If you already have Ubuntu installed on the system and u just want to upgrade then, just select the same drives again and ask them to be mounted as same. But do not select format i.e. make sure that format is unchecked or not ticked. This will upgrade ur Ubuntu without formatting the drives again.

I suggest u to use software like partition manager/magic etc. to partition the space.
These software give option to resize the previous partitions and u can create a blank space for Ubuntu.
Once u got to Ubuntu setup, u can create new partition table only for this new space which u created.

In Ubuntu setup also u get opyion to delete existing partition. Use it and then re-create the partitions as you need.

I hope this helps.
Thank you.

---

### Post by oldfred on 2012-12-29
You should not need the other system partitions with a standard desktop.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    
My suggestion, but not really a lot different than rajhanschinmay's, but maybe a bit large / (root if you have the space. I find tmp needs an extra 4GB when writing my backup DVDs, so I like to be generous with /. 

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

    
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

