---
title: "Upgrade to another partition"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by jules98 on 2010-10-21
Hi all,

Is it possible to upgrade (in my case from 8.04 to 10.04) into another partition?

Explanation: I have a system with 2 200GB disks:

Disk 1:
1. swap (4 GB)
2. / (20 GB)
3. /home (40 GB)

Disk 2:
1. /srv (200GB)

Is it possible to create a 4th partition on the first disk and to let the upgrade procedure to use the new partition as target?

The advantages will be:
1. Possible to execute without disturbing the running system.
2. Possible to keep the original partition as a fallback.
3. Very simple activation/fallback procedure: reboot on the correct partition.

I must say that I'm using Sun Solaris at work and I'm doing this operation regulary with the "Live upgrade" tool.

BR, Jacques-D. Piguet

---

### Post by VMC on 2010-10-21
It depends on your experience level.I don't know of a tool or script that would do would your asking.

What I would do, and have done, is to make the new partition then copy the current partition to the new and change any reference to UUID's - fstab, initramfs-tools, etc. Then you would need to update grub in incorporate the new OS.

There's a lot of issues with Gparted that I keep reading about. I would back up your current partition using Clonezilla first.

---

### Post by psusi on 2010-10-21
Boot the livecd, create your new partition, then copy all files to it ( with cp -a ).  Reboot from the hard disk and upgrade.  The copy will be left as is, and if you need to, you can direct grub to boot from it.

---

### Post by jules98 on 2010-10-23
Booting from a live CD/DVD is NOT a solution as the system will not be running anymore.

The most important and valuable point in a "Live upgrade" procedure is to have the fully running all the time (out of the reboot itself).

BR, Jacques-D.

---

### Post by perspectoff on 2010-10-23
> **psusi said:**
> Boot the livecd, create your new partition, then copy all files to it ( with cp -a ).  Reboot from the hard disk and upgrade.  The copy will be left as is, and if you need to, you can direct grub to boot from it.

Hey, that's exactly what I did yesterday!

So, to flesh out this advice, I booted into the Ubuntu LiveCD and started GParted (System -> Administration -> GParted). I created an additional logical partition (for me /dev/sda7) within my extended partition, of filesystem type ext4.

From the command-line interface Terminal, I made directories and mounted the two partitions (the source partition (/dev/sda6) and the destination partition (/dev/sda7).

sudo mkdir /media/partsda6
sudo mkdir /media/partsda7
sudo mount /dev/sda6 -t ext4 /media/partsda6
sudo mount /dev/sda7 -t ext4 /media/partsda7

Then I merely copied the contents from one partition to the other:

sudo cp -a /media/partsda6/* /media/partsda7

Then I rebooted the machine into the original OS, and updated Grub2 using
sudo update-grub

which then recognized the new partition and added a menu item to the Grub2 menu.

(I happen to use a Grub Legacy boot partition, so I edited the Grub Legacy menu there, too, but not everyone does that).

Rebooting again, I boot into the newly copied partition's OS. There I edit my /etc/fstab file to make sure all the settings are correct (since the copied fstab keeps the UUIDs of the original partition when mounting partitions, and that may need to be tweaked). To be sure of all UUIDs, I use

 sudo blkid

and use the appropriate UUIDs in the /etc/fstab file.

Now I have two (nearly) identical OS's. I then do an upgrade of the new one. It the upgrade fails, I have the old one still running.

---

### Post by psusi on 2010-10-23
> **jules98 said:**
> Booting from a live CD/DVD is NOT a solution as the system will not be running anymore.

That's the point.  You don't want the system to be running when you copy it.

> **jules98 said:**
> The most important and valuable point in a "Live upgrade" procedure is to have the fully running all the time (out of the reboot itself).


Who said anything about "live upgrade", whatever that means?  The OP just wants to upgrade but keep a copy of the old, working system on another partition.

---

### Post by perspectoff on 2010-10-23
If you're trying to run both the old OS and the new OS at the same time, of course, you will have to run Virtual Machines.

So perhaps you are asking how to copy the original OS into a virtual machine?

Perhaps someone has the answer to that one. I'm not sure how to do that using cp -a.

What I do instead is to create a filesystem archive (of the original OS) using fsarchiver, store it somewhere, and then restore it to the virtual machine. 

That may be too much of a roundabout method, though, and there may be an easy way of using cp -a directly.

The only problem is, naturally, you can't copy the entire filesystem of an OS that is currently running (because some of the system files can't be copied while it is running). That's why you have to use a LiveCD.

---

### Post by jules98 on 2010-11-02
I will try to explain better what i would like to do:

1. I have a system running 8.04 from sda1, sda2 is swap, sda3 has same size as sda1 and is not in use.
2. I format sda3 and create a file system.
3. I install 10.04 on sda3, WHILE system is still running from sda1.
4. I copy all the configuration from sda1 to sda3
5. I reboot the system into sd3: 10.04 is running with the configuration of 8.04

Advantages:
- The system down time is reduced to the reboot duration
- I still have the old partition if anything is going wrong

Inconvenients:
- None...

I'm doing this on a regular base on Sun Solaris systems with the "Live Upgrade" toolkit.

Does anybody knows if this kind of operation is possible with Ubuntu?

BR, Jacques-D.

---

### Post by oldfred on 2010-11-02
I have 3 root partitions that I rotate around. But I do clean installs. I have old install, current install, and future (starting with beta). 

I do clean install and copy any data from the old that I may want. Almost all my data is actually in a separate /data partition that I just mount & relink into my new install.

I also export a list of installed applications and reinstall those. Only once or twice have I had to go back to /etc to find some customized setting that I have done.

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by psusi on 2010-11-02
> **jules98 said:**
> I will try to explain better what i would like to do:

1. I have a system running 8.04 from sda1, sda2 is swap, sda3 has same size as sda1 and is not in use.
2. I format sda3 and create a file system.
3. I install 10.04 on sda3, WHILE system is still running from sda1.
4. I copy all the configuration from sda1 to sda3
5. I reboot the system into sd3: 10.04 is running with the configuration of 8.04

Advantages:
- The system down time is reduced to the reboot duration
- I still have the old partition if anything is going wrong

Inconvenients:
- None...

I'm doing this on a regular base on Sun Solaris systems with the "Live Upgrade" toolkit.

Does anybody knows if this kind of operation is possible with Ubuntu?

BR, Jacques-D.

No, the best you can do is copy the existing system to the other partition and then upgrade.

---

### Post by jules98 on 2010-11-03
> **psusi said:**
> No, the best you can do is copy the existing system to the other partition and then upgrade.

It's exactly what I want to do: copy the system on another partition and update it.

The basic question is how an update is done: it's one (or more) script reading files and writing others. In the usual case it is handling the current root partition, but why would it not be possible to chroot it and let him work while the system is still running his normal tasks?

BR, Jacques-D.

---

### Post by jules98 on 2010-11-03
Just for the sake of understanding what I mean with "Live upgrade", you can have a look the following documentation:

[http://docs.sun.com/app/docs/doc/817-5505/luoverview-1?l=en&a=view]("http://docs.sun.com/app/docs/doc/817-5505/luoverview-1?l=en&a=view")

BR, Jacques-D.

---

### Post by psusi on 2010-11-04
> **jules98 said:**
> The basic question is how an update is done: it's one (or more) script reading files and writing others. In the usual case it is handling the current root partition, but why would it not be possible to chroot it and let him work while the system is still running his normal tasks?


I suppose you could chroot after the copy and run the upgrade that way.

---

