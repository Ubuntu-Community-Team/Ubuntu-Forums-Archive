---
title: "Resizing Partitions on Dual Boot After Fully Installed"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by kirkio on 2006-10-13
I have been running Windows/Linux dual boot and installed Wine so that I can play CounterStrike on linux. When I went to install CounterStrike from Steam, I discovered that I hadn't made my linux partitions large enough, so I need to resize my partitions.

When I go to gparted and select my Windows (NTFS) partition, I get the Warning error: 
Unable to read the contents of this filesystem! Because of this some operations may be unavailible. Did you install the correct plugin for this filesystem?

It will not allow me to resize the partition. I suspect that it has to do with, ntfs-3g, which I used to mount and get read-write access to my windows partition (more on this here: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009))

How can I work around this so that I can make my linux partition bigger from space taken from my Windows partition?

Thanks,
Kirk

---

### Post by wieman01 on 2006-10-13
Safest bet is to resize in Windows. Free up space using PartitionMagic or the Windows disk manager (I remember there is something like that available). Don't use GParted/Linux for NTFS, that's not really safe.

In order for us to help you with the remaining bit (moving partitions, etc.) please post a screenshot of GParted after the resizing exercise. Will help a lot.

---

### Post by kirkio on 2006-10-13
Okay. Well I have freed up space from my Windows Partition and put in my extended partition that I use for linux (I have a dell that has stuff pre-installed on the other two partitions that I did not want to mess with) but I can not resize the logical partition that is in the extended partition. When I booted the live CD to make the partition modifications, it said that my swap partition was activated, so I had to deactivate it in order to make changes to my extended partition, so I did that. So now my extended partition says that I have 1.95 gigs of unallocated space but the resize tool will not allow me to resize my main ext3 partition. I have attached a screenshot of Gparted

Thanks,
Kirk

---

### Post by wieman01 on 2006-10-13
Ok, first of all you need to boot from the Live CD. Otherwise you won't be able to repartition because of the mentioned issue.

Your case is a bit more complicated because SDA5 is bigger than the unallocated space (1.95 GB). A slightly easier option is to move SDA5 to the unallocated space following SDA3. Would that be an option for you?

In that case we convert the unallocated space on the extended partition into a data partition for personal files, etc. Let me know your decision.

---

### Post by wieman01 on 2006-10-13
BTW: The reason why you cannot resize SDA5 just like that is because the unallocated bit starts _before_ SDA5. That's why your case is a bit complicated, but - of course - manageable.

---

### Post by kirkio on 2006-10-13
The unallocated space after SDA3 is only 7.84 MB, so that wouldn't work. Are you considering resizing SDA5 and making another logical partition for my files (run off of two partitions) or will that not work well?
Is there a way I can just move SDA5 up in the unallocated space in the extended partition and then resize it? If so, how would I do that?

---

### Post by gn2 on 2006-10-13
Would it be possible to create a partition in the un-allocated space, and then merge the two into one large partition with gparted?

This is a trick I've used before in windows with partition magic.

---

### Post by kirkio on 2006-10-13
I don't have a copy of partition magic to use, and if I'm not mistaken, it's a commercial app. I tried seeing if there was a way to do this in Gparted, but I couldn't find one. Is there any way I can do this in Gparted?

---

### Post by gn2 on 2006-10-13
> **kirkio said:**
> I don't have a copy of partition magic to use, and if I'm not mistaken, it's a commercial app. I tried seeing if there was a way to do this in Gparted, but I couldn't find one. Is there any way I can do this in Gparted?

I don't know if gparted can do it, I've got another partitioning tool. 
Ah... Partition Magic, worth every penny.

---

### Post by Peepsalot on 2006-10-13
I have had some troubles with gparted on the Ubuntu CDs(in Dapper and Edgy).  

However, I found that the gparted LiveCD(0.3.1-1) worked flawlessly.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
And it's only 30mb.

---

### Post by wieman01 on 2006-10-13
Kirkio:

My apologies... The unallocated following "SDA3" is 7.84 MB in size rather than 7.84 GB. Sorry, had not paid attention.

Let me think for a while & get back to you. Seems we need to get our hands a bit "dirty" now. :-)

---

### Post by wieman01 on 2006-10-13
Ok, as from what I can see here there easiest way to gain more space & move "SDA5" is to resize "SDA2" first of all, thus freeing up 2.93 GB for "SDA5". Later on we merge that with the unallocated space on the extended partition.

Let me know if that's an option. Then we continue from there.

---

### Post by kirkio on 2006-10-17
> **Peepsalot said:**
> I have had some troubles with gparted on the Ubuntu CDs(in Dapper and Edgy).  

However, I found that the gparted LiveCD(0.3.1-1) worked flawlessly.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
And it's only 30mb.

The gparted live CD worked great!

---

### Post by Peepsalot on 2006-10-17
Glad I could help.  Cheers :D

---

