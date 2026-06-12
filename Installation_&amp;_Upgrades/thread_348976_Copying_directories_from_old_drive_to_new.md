---
title: "Copying directories from old drive to new"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2007-01-29
I am in process of upgrading from 5.04 to 6.10. The 5.04 was my first Linux install and the partitioning was basic. I have partitioned a new drive with 6.10, including /, /swap, /home, and a fat32. I want to get my /home, /etc/, and /var transferred from the old drive to /home on the new drive.

Question one is, without thinking it through, I named the 3rd partition on the new drive as /home. Is this going to be an issue if I want to transfer /etc and /var to the same partition or am I limited to only transferring /home to it? (Not very sure of the significance of the "name" of the partition)

Secondly, I have found out how to do this using tar, but am curious if using tar gives me any advantage over just mounting the new drive and copying /home (and /etc and /var) over from the old to the new, and if any advantages, what are they? (Obviously a straight copy is a lot simpler than using tar.)

---

### Post by danpre on 2007-01-29
I would suggest you to:
1. Make a copy of all the data you to external hard drive (cd, flash, network drive?)
2. Check the data!!! Once I have made a backup to DVD, formated a hard drive and half of the data was not on the DVD.
3. Remeber: to make a copy of some files from  /etc or /var you will need a root privilleges
4. I would stop all servers: ex.: stop mysql server to copy mysql bases 

DANIeL

---

### Post by Odyssey1942 on 2007-01-29
Daniel, Thanx yours. Would copying from one internal hdd to another internal hdd not be the same result as copying to an external (i.e., USB) hdd?

I'm a newbie, as you can prob tell from the original post, so unfamiliar with stopping servers, Is this necessary if I am only copying /home, /etc, and /var? If so, I would be obliged if you would  please elaborate for my future understanding.

(Both drives are already installed with 5.04, and 6.10 respectively)

---

### Post by danpre on 2007-01-30
> **Odyssey1942 said:**
> Daniel, Thanx yours. Would copying from one internal hdd to another internal hdd not be the same result as copying to an external (i.e., USB) hdd?

Well, yes it is the same result but with external drive you are able to check data on both systems and you have additional backup just in case of something goes wrong.

> **Odyssey1942 said:**
> I'm a newbie, as you can prob tell from the original post, so unfamiliar with stopping servers, Is this necessary if I am only copying /home, /etc, and /var? If so, I would be obliged if you would  please elaborate for my future understanding.

(Both drives are already installed with 5.04, and 6.10 respectively)

I don't know what if you are using any servers (there is a lot of software which uses mysql - example: AMAROK, OpenOffice - depending of settings). Mysql databases are stored in /var. 

To stop a server, example for mysql:
```
sudo  /etc/init.d/mysql stop
```


DANIeL

---

### Post by Odyssey1942 on 2007-01-30
Daniel, thanks for the clarification.

Does anyone have any thoughts on:

> Question one is, without thinking it through, I named the 3rd partition on the new drive as /home. Is this going to be an issue if I want to transfer /etc and /var to the same partition or am I limited to only transferring /home to it? (Not very sure of the significance of the "name" of the partition)

Secondly, I have found out how to do this using tar, but am curious if using tar gives me any advantage over just mounting the new drive and copying /home (and /etc and /var) over from the old to the new, and if any advantages, what are they? (Obviously a straight copy is a lot simpler than using tar.)

(above from original post in this thread)

TIA

---

### Post by dannyboy79 on 2007-01-30
i don't think you want to put /etc and /var INSIDE of your /home partition. this may result in having /etc and /var within your /home folder which you DON'T want, trust me. /etc and /var are both suppose to be under /. if what you mean is that you want to have 1 partition that contains your /home data, your /etc data and your /var data then I think this can be done. i am from windows so I always get confused when talking about partitions and mount points. if you're concerned about /var and /etc partitions than why not to be on the safe side just create seperate partitions for these!

---

### Post by Odyssey1942 on 2007-01-30
You have confirmed my anxiety about having "named" the third partition "/home". I did not think ahead to the possibility of having other directories in the same partition.:confused: 

Although your suggestion would solve the issue, I prefer not to have 3 additional partitions because when you get more than four, you have to go to logical partitions and I would prefer to avoid this.

Clearly I do not understand the significance and import of "naming" a partition. What I mean is if the / partition can contain /home, /etc, /var as well as several others, how does one set up a separate third partition (i.e, / being first partition, /swap being second, etc) to hold the three named (/home, /etc, /var) directories? This presumeably should be done during the install process, but maybe it can be done after installation also (e.g., "re-naming" my current third partition, now called /home to another name?)

---

### Post by dannyboy79 on 2007-01-31
check out this link for moving /home to  seperate partition after you install / and /home originally on the same partition. you could maybe do this for /etc and /var. [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

i have to be honest though, i don't see this as being possible, at least I know you can't tell fstab to mount /dev/hda3 to /etc as well as /home as well as /var, see what I am saying. there's no way that I can think of to get this accomplished. i know it's done during the install, which puts /etc and /var within the same partition, but this is all under /. so how during the install do you tell it that you want /etc to be on partition 3 along with /home and /var? not sure about this. the easiest headache free is to make each a seperate partition. there is nothing wrong with extended partitions and logical partitions! if there was, they wouldn't have ever made it possible. I have seen plenty of partition schemes for servers where /tmp, /usr, /var, /etc, /boot, /home, /, all have their own partitions which obviously uses an extended partition. it's fine! plus when you do this, you'll never have a problem about needing to ever create another partition because I don't think it's possible to create an extended partition after the fact without possible losing data, I could be wrong on this though. For instance, I have a /boot (hda1), / (hda2), /home (hda3), extended partition containing /swap (hda5 because hda4 is really the extended partition but doesn't get used), and then unused space in case I want to install another distro. good luck.

---

### Post by Odyssey1942 on 2007-02-01
Danny, I believe I understand what you are saying about having several partitions and have now found other threads that say pretty much the same thing. So I think that I will just have /, /swap, /home, and a fat32 partition (for file exchange with Windoze) to keep it simple

I have seen several posts where there is a /boot partition, /, /swap, and sometimes others as in your case. What are the advantages of separate boot and root partitions? Thnaks.

---

### Post by dannyboy79 on 2007-02-01
the advantage of having a /boot partition is that if you have 2 or even 3 operating systems on 1 machine, then you have a / partition for each of them and they both share the same /boot partition. this way, if one or the other or hell, even both get screwed up, your boot partition (grub) is still in tact. this way if winxp was one the os's, your winxp install would still boot because your /boot partition wasn't affected. here are some more advantages of having seperate partitions for various mount points:

-You can choose the best performing filesystem for each partition or volume 
-Your entire system cannot run out of free space if one defunct tool is continuously writing files to a partition or volume 
-If necessary, file system checks are reduced in time, as multiple checks can be done in parallel (although this advantage is more with multiple disks than it is with multiple partitions) 
-Security can be enhanced by mounting some partitions or volumes read-only, nosuid (setuid bits are ignored), noexec (executable bits are ignored) etc. 

here is the link that I got the above info from. it's a good read if you're interested in finding out why some people create /usr and /var and others as a seperate paritition as well. [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4)

---

