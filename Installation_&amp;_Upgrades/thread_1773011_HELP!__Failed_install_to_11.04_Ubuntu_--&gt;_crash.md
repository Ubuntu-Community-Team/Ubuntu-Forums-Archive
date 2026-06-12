---
title: "HELP!  Failed install to 11.04 Ubuntu --&gt; crashed computer"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by ezm on 2011-06-01
Hi All, I seem to have quite a serious problem that I'm not sure how to approach.  I have a laptop set up for dual-boot with Ubuntu and Win7.  I also have a shared partition which I mounted as the /home directory in Ubuntu.  

The problem occurred as I was upgrading Ubuntu from 10.10 to 11.04.  In the middle of the install, my computer froze for some reason and ultimately I had to shut the computer off and restart.  When I restarted the linux would freeze half-way through boot-up with a message saying that the drive was mounted.  Before the message saying the drive is not mounted it gave the following error:

Can not read 'etc/udev_rule.d/z80_user.rules'

When I boot up Win7 it is unable to mount the shared partition and says that the drive is not formatted. 

I am also unable to run the ubuntu recovery option from GRUB.  It asks me to give the "root password for maintenance," but it won't accept my root password. 

Does anyone have any idea how I should begin to solve this problem?  Would the upgrade have wiped my partition???  Or am I just locked out somehow because it was in the process of changing config files?

Any help would be greatly appreciated! 

p.s. I found someone else had a similar problem on this thread: [http://ubuntuforums.org/showthread.php?t=1725054](http://ubuntuforums.org/showthread.php?t=1725054).

---

### Post by ANetTow on 2011-06-01
I had a similar problem when installing 11.4 for the first time on a Toshiba NB505.  I got to the partitions section of the installation and it just crashed.  For now, I'm trying 10.10 instead, but I'm curious to see what replies you get.

---

### Post by jerrrys on 2011-06-01
your partitions should be fine and your ubuntu install should be toast.  TestDisk has a way of working wonders.  even though this should not be a partition problem, i would give it a shot.  its fast and simple

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by ezm on 2011-06-03
Thanks...The installation was definitely toast.  I ended up getting frustrated and reinstalling from a disk.

---

### Post by mörgæs on 2011-06-03
Good, please mark the thread 'solved'.

---

### Post by ezm on 2011-06-03
Hmmm...I can't figure out how to mark it solved.  Can you tell me how to do that?

---

### Post by mörgæs on 2011-06-03
It is in 'thread tools'.

---

