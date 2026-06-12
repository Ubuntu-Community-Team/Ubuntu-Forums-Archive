---
title: "Installing on secondary hard drive"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by jingyeow on 2011-05-26
I've read the official documentation regarding hard drives and partitions.

My pc has two hard drives.
a 160gb primary hard drive with windows 7
a 1.5 tb secondary hard drive with about 80gb of free space

I would like to know whether I can install ubuntu on the secondary hard drive, without touching any of the data present on that drive. From my limited understanding of storage, files are written all over hard drives during copy, move etc...

Is the ubuntu partition manager smart enough not to overwrite any files during installation? Will I get a warning if there is a risk of any data loss on the secondary hard drive?

I cannot backup any of the data on the secondary hard drive due to all my external drives currently being full.

Thanks

---

### Post by sanderd17 on 2011-05-26
Making backups should always be done. But aside from that, when you choose to install ubuntu next to windows (from a radiobutton list during the install), Ubuntu will search the partition with the most space, shrink that partition, create a new empty partition on that unallocated space and install itself on that space.

So normally it will do what you want. In case you don't trust us, you can always choose the manual configuration. But that's how I lost all my data when I installed ubuntu for the first time, I didn't know anything of partitioning and shouldn't have decided to do it myself.

---

### Post by jingyeow on 2011-05-26
Thanks for the advice sanderd17.

I most definitely do not want to partition the primary hard drive. In my experience two OS should never been on the same physical hard drive.

However the only thing stopping me installing ubuntu onto the secondary hard drive is that my data might be overwritten, and I can't backup the entire drive.

Does the installation actually touch any data, or to create a partition, must the secondary hard drive be empty or defragmented first?

---

### Post by sanderd17 on 2011-05-26
The installer shrinks the partition on the disk, and the shrinking works the best with a defragmented disk.

So yes, while shrinking, the installer moves some blocks around and thus touches data.

In my experience: I always have 2 OS on the same disk. Currently I have Mint 11 on sda6, OpenSuse 11.4 on sda5 and my shared home folder (with all settings and files) on sda7.

Linux can handle different partitions very well. You can mount a partition to any directory you want, so you can share settings or files between different OS'es by putting those in a separate partition and mounting the partition in both OS'es.

---

### Post by YesWeCan on 2011-05-26
> **jingyeow said:**
> I most definitely do not want to partition the primary hard drive. In my experience two OS should never been on the same physical hard drive.
Hi, I agree. It is better from a boot-loader point of view to have them on separate disks.

First, I would disconnect your Windows drive while you do the Ubuntu install. Keeps thing simpler and makes sure the Ubuntu boot-loader's MBR is put on the Ubuntu disk and does not overwrite the standard MBR on the Windows disk. This prevents some future grief.

Normally, installing Ubuntu in your 80GB of free space is pretty easy. Your data will not be damaged in any way. The installer will do what you tell it to do and no more.

However, it is possible to make a mistake. It is possible to tell the installer to overwrite your data partition. These things are unlikely but possible user mistakes, especially for novices. So if this data is really important to you, don't chance it. Buy a cheap HD for Ubuntu or just don't do it. Use common sense.

It is hard to advise because on the one hand the process is fairly easy and very reliable but on the other people do make mistakes from time to time. Ubuntu and linux do not tend to offer as many warnings as Windows does; you usually just get one warning and if you ignore it or don't understand it then linux will still obediently carry out your stated wish.

---

### Post by YesWeCan on 2011-05-26
> **sanderd17 said:**
> The installer shrinks the partition on the disk, and the shrinking works the best with a defragmented disk.
Really? I thought you tell the Ubuntu installer to install in the 80GB of unused space and it does it without disturbing the existing data partition.

I don't think the OP wants the installer to shrink anything! Definitely don't do this if the data partition is touched in any way.

---

### Post by sanderd17 on 2011-05-26
is it 80 GB free space on a 1.5 TB partition or 80 GB unallocated space on a 1.5 TB disk?

in the first case you need to shrink, in the second you don't

---

### Post by YesWeCan on 2011-05-26
Oh I see what you mean. :)

My slightly different advice if you have to shrink the original partition is to use Windows to do it. I assume it is a Windows data partition. This is the safest way to shrink it, IMO.

Once you have unused space on the disk you can install Ubuntu into it without using the installer to shrink the data partition.

---

### Post by jingyeow on 2011-05-26
So if I understand correctly, by shrinking the secondary drive, I remove the amount of space that Windows can see. e.g. hidden space.

I do not at this point partition the hidden space

Then I unplug my primary hard drive, run ubuntu from the cd and choose to install.

When given the option, I partition the hidden space ubuntu likes what it sees and bobs my uncle?

---

### Post by oldfred on 2011-05-26
Herman has a lot of detail on installing. Not as complex as it may look as he explains a lot. Based on 10.10 but while some screens have changed a little the process is the same in Natty.

Dual boot 2 drives -Maverick
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by jingyeow on 2011-05-27
Thank you Oldfred. Exactly what I needed to understand the process. I'm a very visual learner, so endless reading to me isn't as effective as following image or video tutorials

---

