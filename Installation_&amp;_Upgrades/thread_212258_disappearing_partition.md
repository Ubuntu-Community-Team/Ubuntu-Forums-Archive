---
title: "disappearing partition"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by kaskennedy on 2006-07-09
I began installing Dapper Drake from the live CD, using the desktop version. I worked through all the steps up until I got the options for partitioning. I chose to resize my partition, but after a couple minutes cancelled the process because I thought there would be another step before it actually began to partition my hard drive. Now, my C: drive is half the size it should be (60 GB instead of 120) and the other 60 GB partition is nowhere to be seen. Dapper Drake is not installed and now I do not have the choice to resize the partition, only to wipe the entire hard drive and to use the largest open space. How do I get my 60 GB back and install Ubuntu? The goal of this process is to dual-boot both XP and Ubuntu. I definitely don't want to wipe the drive. Please help!

---

### Post by tonyr on 2006-07-09
Can you still boot Windows?

---

### Post by kaskennedy on 2006-07-10
Yes, windows still boots fine. All my files seem to be intact and there are no problems starting up. I can go into "My Computer" and look at the specs on my C: drive and that's how I know that it's half the size it should be. My system is a Compaq presario s4200nx with a Celeron 2.5Ghz, 512Mb. I'm running Windows XP Home sp2. If I need to provide any more info just ask.

---

### Post by jonrkc on 2006-07-10
What I would do is to run cfdisk and see what it reports, without making any changes whatever.  If it looked like cfdisk can create a new partition at the END of the Windows partition, then I'd back up all my Windows data as best I could, and proceed to create a new partition starting at the end of the (good) Windows one, using cfdisk.  Cfdisk is a very straightforward and easy-to-use program, but as with any partioning effort, there IS a chance of losing data, so I'd certainly want to back up anything I couldn't afford to lose, first.  Chances are, the procedure will go just fine, though.

---

### Post by tonyr on 2006-07-10
With the LiveCD (PC desktop 6.0.6) booted, run **gparted**
(System->Administration->Gnome Partition Editor).  You will probably
see your 60GB Windows (NTFS) partition and 60GB of unpartitioned
space.  If that is the case, you can create an **Extended**
partition in the rest of the space.  Inside the **Extended** partition,
Create a 7GB **Logical** partition and another Logical partition 
that is about 1.5x your physical memory size. (There are a couple of 
schools of thought about howbig this one should be, but 1.5x should be OK).  Leave the rest of the **Extended** partition alone for now.  I don't 
remember whether the LiveCD offers you the option of partitioning manually.
If it does, make the 7G partition your root (/), and the other
one swap.

There are a couple of good guides for this process.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by kaskennedy on 2006-07-10
Ok, I've created the new partitions. Can I install Ubuntu now?

---

