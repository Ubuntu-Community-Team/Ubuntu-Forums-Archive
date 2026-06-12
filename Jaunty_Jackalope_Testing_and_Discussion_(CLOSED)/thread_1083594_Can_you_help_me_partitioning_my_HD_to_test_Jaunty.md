---
title: "Can you help me partitioning my HD to test Jaunty?"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2009-03-01
Hello guys.
I am about to install Jaunty for testing. My system works gorgeously with my current installation and I don't want to loose it, so, I would like to post here my current HD partitions and make sure that I'm not breaking anything :)

Actually I have a dual boot, Windows / Intrepid managed by grub. and another NTFS partition 

Windows partition NTFS / 80 GB NTFS Partition / Ext3 Filesystem / Swap 

So, in order to create another partition I have to resize my 80GB ntfs partition. Then use the freed space to create the Ext4 partition for Jaunty.
So, during the installation there is any specific step I have to follow in order to be able to boot all OS (Win, Intrepid, Jaunty?) 
The mount point for the new Ext4 would be / ? 

I am attaching the current partition table in my HD
Thaks!

---

### Post by Kosimo on 2009-03-01
[IMG]http://kosimo.googlepages.com/partitions.jpg[/IMG]

---

### Post by Timon&amp;Pumba on 2009-03-01
No offense, but if you do not know how to do the partioning part, you probably do not have enough experience to fix any problems you may run in to while using a development release.

If you are curious about the status of Jaunty, use the livecd or run jaunty in a virtual machine.

Just some advice...
Timon

---

### Post by ronacc on 2009-03-01
If you do not want to risk your existing system I would not install any alpha or beta on the same drive regardless of the partitioning . Developement software can do strange things at any time and the results can be severe .If you do decide to procede , backup everything first . I also would not allow the test install write its own grub (same reason ) you can edit your existing grub to boot the new partition .

---

### Post by Kosimo on 2009-03-02
Wow guys that was helpful 	#-o

---

### Post by Timon&amp;Pumba on 2009-03-02
> **Kosimo said:**
> Wow guys that was helpful 	#-o
> **Kosimo said:**
> Hello guys.
So, in order to create another partition I have to resize my 80GB ntfs partition. Then use the freed space to create the Ext4 partition for Jaunty.
So, during the installation there is any specific step I have to follow in order to be able to boot all OS (Win, Intrepid, Jaunty?) 
The mount point for the new Ext4 would be / ? 


Well, to begin with you are not very clear, except that you want to squeeze another system on you harddisk. You are talking about a 80 GB NTFS partion you do not have according to the screenshot.

Now assume it is the 118 GB partition you want to resize:
[LIST=1]
[*]rightclick that partion, then resize to free up some space (at least 10-20 GB)
[*]Boot to the Jaunty installation cd
[*]Use the build-in partitioner to format the "unallocated space" (be careful here) according to your wishes to contain the system
[/LIST]

You may want to share the linux-swap partition between your linux systems.
I think grub will load its configuration from either your old ext3 partition or your new ext4 paritions. It does not matter which, as long as that configuration contains all operating systems. You probably have to edit that yourself.

---

### Post by Nullack on 2009-03-02
Mount point will be /. though I prefer to do / and home

These sorts of operations are risky and the wise will take a disk image before doing so of any important data

Yes, resize the partition and create some new extended partitions and primary partition numbers are limited

---

### Post by nyarnon on 2009-03-02
Considering your knowledge I would not advise you to use Jaunty, but as that probably will not stop you I would like you to consider setting Jaunty on a USB stick or drive. Problem solved. No risk of mocking up your stable system.

---

### Post by Kosimo on 2009-03-02
> **nyarnon said:**
> Considering your knowledge I would not advise you to use Jaunty, but as that probably will not stop you I would like you to consider setting Jaunty on a USB stick or drive. Problem solved. No risk of mocking up your stable system.

This is the best advice I could ever have. I didn't think about it

Tanks dude ! ;)

---

### Post by nyarnon on 2009-03-02
De nada, your welcome.

---

### Post by tghe-retford on 2009-03-02
> **ronacc said:**
> If you do not want to risk your existing system I would not install any alpha or beta on the same drive regardless of the partitioning . Developement software can do strange things at any time and the results can be severe .If you do decide to procede , backup everything first . I also would not allow the test install write its own grub (same reason ) you can edit your existing grub to boot the new partition .
I would have to echo this, I have known data to be deleted across multiple partitions early on in Jaunty's development. Considering my experience of testing, I would be uneasy to install a development system on the same hard disk as a stable one. The safest way to test Jaunty is to use a separate computer from your stable install.

---

