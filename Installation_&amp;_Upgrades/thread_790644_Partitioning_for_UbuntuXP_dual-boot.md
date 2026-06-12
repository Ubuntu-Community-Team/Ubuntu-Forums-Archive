---
title: "Partitioning for Ubuntu/XP dual-boot"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by sackbj on 2008-05-11
Hi all,

I've built a machine with a 320GB hard drive and I would like to configure it to dual boot with Windows XP.  I am thinking about how to partition the machine so I can access media from each operating system.  I'm using an Abit RN-M2HD motherboard, AMD X2 5000+, 2GB of ram.

I am thinking something along these lines.

| NTFS 40GB | ex3 30GB for / | the rest FAT32 for /home and Windows | 1GB Swap |

I can set up those partitions using a LiveCD.  Then install XP on the NTFS partition.  Then install Ubuntu on the / partition and mounting the big one as /home.  I'm thinking this will install Grub so I can choose between the two at boot time.

Will XP be able to access and modify data on the big partition (FAT32 mounted as /home in Ubuntu) as its own hard disk?  Also, do I need a Swap partition with 2GB of ram?  I'm looking for any input or suggestions about partitioning or things like 32bit vs 64bit.  Thank you!

---

### Post by UnWarierMage224 on 2008-05-11
I would create 1NTFS partition for windows
1 NTFS partition for your documents
1 EXT3 partition for linux home
1 EXT 3 partition for linux root
1 swapfile partition

You'll need a logical partition to hold the four non-win-OS partitions. 

this is how I have my setup. 

Hope this helps.

Oh BTW, when I did this I installed windows first then installed linux. Linux partitions were created lateron as this used to be an exclusively-windows system... I'm pretty sure order doesn't matter but to be safe that's what I did. 

-'Mage

---

### Post by Fjatle on 2008-05-11
Back in those days, when I still wanted my XP around ( :) ) I also wanted FAT32 as my /home partition. But from what I remember, this was not possible to do. I believe I had to make it an ext3. 
But you will find this out the second you enter the partition editor. 
But, if I am wrong about this one (and you will find this out yourself the moment you mark the partition as /home), then yes, both Windows and
Ubuntu can use it.

Remember to install Windows first. That is the best way to prevent Windows from messing up your Grub.

From what I once learned, the swap partition is recommended to be a bit bigger than your RAM. This is because of hibernating. When you hibernate your system, it stores whatever you have in RAM to the swap. 
So my guess is if you (in an hypothetical situation) have your RAM filled to the edge before hibernating, things will be messed up.

Grub should automagicaly work after you have installed Ubuntu (remember Windows first). And yes, it should find Both Windows and Ubuntu

---

### Post by louieb on 2008-05-11
> **sackbj said:**
> Will XP be able to access and modify data on the big partition (FAT32 mounted as /home in Ubuntu) as its own hard disk?  Also, do I need a Swap partition with 2GB of ram? 

fat doesn't support Linux permissions so even if you could mount /home on a fat partition (not sure haven't tried) it would not be my idea of a good choice.  I 2nd Mage's layout.  

A 1/2GB swap partition isn't going to hurt anything.  I'd go ahead a create one.

---

### Post by Pumalite on 2008-05-11
/swap=RAM for hibernation. Make /home ext3. You can use it from Windows with this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
Remember the 4 primaries per drive limit.

---

### Post by omglol741 on 2008-05-11
huh I just got a new computer and am thinking about this too..

I got a 500GB hard drive, and I'm going to use 64 bit Vista and 64 version of the newest Ubuntu if that matters

So Windows and Ubuntu can't read files from each other because they are protected correct? Would it be good if I installed Vista first with 100GB or so for games, then installed Ubuntu with most of the rest, then a 20GB or so communal NTFS partition for sharing files between them?

I don't really know how this partition stuff works. Can Vista see other partitions and just copy files into them?

---

### Post by sackbj on 2008-05-11
Thank you for all the replies.

Mage recommended having 2NTFS partitions - one for Windows and the other for documents.  Then also an ext3 partition for /home.  I guess what I was originally asking was: Is there a way to have one partition that can serve as a place for both Windows AND Linx documents?  I am hoping to be able to read/write to it from both OS's.  I guess maybe I'm not understanding your recommendation?


I'm certainly not tied to FAT32 for my /home partition - I was just thinking that might be something that would be compatible with both systems.  However, if Linux doesn't like FAT for /home then I will probably go with ext3.  The Ext2 IFS software looks like a good option.  Have anyone tried this with success?

---

### Post by sackbj on 2008-05-11
In response to omglol741:

One other concern I have about making a partition for multiple operating systems is the potential for Windows malware to infect/destroy the data on that partition.  I'm not sure, but if some kind of malware infects windows and begins destroying data you might lose what you have on your shared partiton.  Like I said, it's just a concern - I don't konw if it happens like that or not.

---

### Post by louieb on 2008-05-11
> **sackbj said:**
>   The Ext2 IFS software looks like a good option.  Have anyone tried this with success?

I've used  [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") occasionally without any apparent   problems.  And Ubuntu comes with fuse and ntfs-3g  for  r/w access to NTFS. 

If you think you'll use window more then make the data partition NTFS. Or if you use Linux more make it ext3. (Mine is ext3 :))    

> **sackbj said:**
> ...One other concern... Windows malware...

With_ ext2 IFS_ an ext3 data partition will look like any other windows formated partition.  So if you become malware infested it could destroy data on that partition too. The good news is windows malware  won't run in Linux. I've seen post about tring to run types of malware in** wine ** it didn't work.

---

### Post by sackbj on 2008-05-11
louieb,

Thanks for your input.  This is a computer for my aunt.  Most of the time it will be running XP, but I wan Ubuntu on there for when I use it (maybe someday I can ween her onto Ubuntu because most of the stuff she does is just e-mail and internet).  I think I will have the shared partition as NTFS since Ubuntu can natively read/write to it with fust and ntfs-3g.

As far as the malware - if I can ween her off of MS and on to Linux, it won't be a problem anyway!

---

