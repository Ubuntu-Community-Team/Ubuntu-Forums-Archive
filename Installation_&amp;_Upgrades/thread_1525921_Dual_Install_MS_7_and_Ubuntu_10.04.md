---
title: "Dual Install MS 7 and Ubuntu 10.04"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2010-07-07
I purchased a new laptop with MS Windows 7 installed. 
In the past, I always followed this procedure:
1. Shrink the Windows partition.
2. Set up two partitions in the shrunken area, one for fat32 data and one for the Ubunbtu O.S.
I have had zero problems doing this.
Now I have heard that Windows 7 won't allow this procedure. Is this true or can I follow my usual way of doing things?

---

### Post by quimkaos on 2010-07-07
Apart from the fat32 partition, that's exactly the setup i have now and what i usually do when i have to have windows eating up space in a pc. I just don't see the need for that fat32 partition. Linux can read and wright in NTFS. The only blind OS here is windows, that can not (will not) see your Linux (NFS, ext4) partition.
Windows 7 (or vista) have nothing to do, or is able to not let you repartition your HD. If you can't do it with any windows native application, do it with an application like partition magic, or better yet try doing it with partitioner of the Ubuntu install CD. Just backup any data, so if anything goes wrong you are safe.

One of the problems i usually face is only finding a laptop without windows! :mrgreen:

---

### Post by tammerlane on 2010-07-07
U am pretty much a NOOB in the Linux/Ubuntu world. Dual booting is handled very well by most Linux distros and all Ubuntu variants. Windows provides few tools to accomplish this and will not acknowledge the existence of any OS on your computer besides Windows. I've had six Ubuntu type distros and Windows on the same computer. They all pretty worked fine. I have Windows 7 Ultimate 64bit and Ultimate Edition 32bit on my computer now. My only problem is that I use the Windows Seven less as time goes by - and it's expensive. Happy computing. tammerlane.:popcorn:

---

### Post by thelugnut on 2010-07-07
First to quimkaos
Okay, thanks for your reply. I suppose the article I read on problems with Windows 7 and Ubuntu was, how shall I put it, a bit confusing.. So I'll go ahead and do it tonight.

Second to tammerlane:
No, I am not a noob as you put it. I have been using Ubuntu and other Linux distributions for a few years. :frown: Your answer did not make me smile.

---

### Post by Rubi1200 on 2010-07-07
The only thing I want to add is that it would be better to resize the Windows partition from **within** Windows using the built-in tools.

First, backup any important data then defragment the drive if needs be.

Then, resize and reboot running a chkdsk.

Reboot a couple more times just to make sure everything is in order and **then** install Ubuntu.

Good luck!

---

### Post by thelugnut on 2010-07-08
Roger that! Good advice. Thanks for the reply.

---

### Post by quimkaos on 2010-07-09
hope it all went fine!

---

### Post by drrkaplan on 2010-07-09
i'm having similar problem.  recently bought hp dv7-3165 laptop with windows7-64 preinstalled.  ubuntu was able to resize the c drive, but the resulting free space was 'unusable'.  aparently, sata drives can aonl have 4 primary partitions, & hp used all 4 in the windows install.  sda1=200mb listed in fdisk as 'system', sda2=c-drive, sda3=d-drive(recovery), sd4=e-drive(FAT32 'hp tools').  if i delete sda1, system wont boot to windows.  deleting sda4 doesn't provide enough partitions for both root and swap,& it also would prevent me from using hp's recovery tools(no recovery discs provided).  so far, i've been stuck, unless i install a second hd or buy a copy of win7 & install it from a clean reformatted hd,then install ubuntu the usual way.

---

### Post by thelugnut on 2010-07-09
I'm struggling with this problem, but there will be an icy day in Hades before I purchase a MS O.S. I still have my Windows XP disk and by golly that is what I am going to use.

---

### Post by wookieshaver on 2010-07-09
This reply is for drrkaplan.
 
What would be a good plan is to creat recovery media using windows. Most manufacturers provide a way for you make recovery discs even though you have a recovery partition. Once you have this, you are safe to re-use the space the recovery partition is using for your Ubunutu install.

---

