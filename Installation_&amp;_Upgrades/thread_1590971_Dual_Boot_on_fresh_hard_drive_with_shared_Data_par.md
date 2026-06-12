---
title: "Dual Boot on fresh hard drive with shared Data partition"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Adrastus on 2010-10-08
[FONT="Arial"]Hi all,

I just finished building my shiny new desktop and I need some advice on partitioning before installing.

I'd like the final layout to have a Windows partition (will start out as XP and will become Win7 when I can afford yet another copy), a partition for Ubuntu, and a shared Data partition that I can use for all my files between both OSs.  I think this should be fairly straight forward with Linux on a Primary partition with / and swap.  Only thing is, from what I've read (and yes I know this is a bit old school) it might be a good idea to put in a /Home partition so that I can reinstall new upgrades and maintain settings.  But I don't want to max out my 4 primary partitions so I can use a 4th partition as a kind of sandbox for OS testing without using VirtualBox all the time.

This leaves me in need of some advice, I've never used Fdisk and I was planning on just using the Ubuntu installer to do all of this, but I don't know if I can create /Home as a logical partition in the main Ubuntu partition and still have the benefit of being able to reformat /root without losing /Home.  I might have just confused myself, because no matter how many guides and How Tos I read I still don't really get extended partitions, I understand logical vs. primary but extended is...confusing.  I need the Ubuntu partition to be bootable, so it needs to be a primary partition...I think.  Unless I can have: /boot, /, swap, and /Home...yeah, I'm confused.

Help?

Also, if Ubuntu can read NTFS, and Win7 can read Ext3, what should a do with /Data? Or should I just go with FAT32 and be done with it.  (It's a big HDD btw, 640 GB, so /Data will be fairly large)

Thanks,

Adrastus
[/FONT]

---

### Post by Adrastus on 2010-10-08
Just realized that /Data can't be FAT32 b/c video files are bigger than 4GB.  I suppose I could just leave them on external :/

---

### Post by sikander3786 on 2010-10-08
You can install Ubuntu with 3 partitions i.e, '/', Swap and /home, all being logical partitions. I myself am doing that. I have Windows 7 on my 1st primary partition, Ubuntu Meerkat on the 2nd one and after that, Ubuntu Lucid, Swap, Home and Data Partition, every thing on the extended/logical partitions.

Support for ext3 in Windows is quite poor. I'll go for NTFS. NTFS-3G driver has grown over the time and now you can say that "NTFS is natively supported under Linux". Really.

---

### Post by Adrastus on 2010-10-09
And having a setup with /home, "/", and swap as logical partitions will still let me to fresh upgrades without losing /home?

---

### Post by sikander3786 on 2010-10-09
> **Adrastus said:**
> And having a setup with /home, "/", and swap as logical partitions will still let me to fresh upgrades without losing /home?
Absolutely yes. That is the real benefit of having /home on a separate partition. Still, it is always a safer approach to backup important data before upgrading.

---

### Post by Elfy on 2010-10-09
> I understand logical vs. primary but extended is...confusing. Treat extended as a special type of primary.

> so it needs to be a primary partition...I thinkNo - ubuntu will boot from a logical

> And having a setup with /home, "/", and swap as logical partitions will still let me to fresh upgrades without losing /home?You can in fact do a clean install without a seperate /home and without losing data in your home - pick manual at the partition option, pick the existing / set the mountpoint to / but do NOT mark it for formatting and the /home will stay as it is.
> 
I'll go for NTFSI would do the same if I needed to share data.

---

### Post by Adrastus on 2010-11-08
[FONT=Arial][SIZE=2]Thank you for your replies, it ended up working out great.  Final partition map:

[/SIZE][/FONT]  
[LIST=1]
[*][FONT=Arial][SIZE=2]Win7[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Data[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Linux[/SIZE][/FONT]
[LIST=a]
[*][FONT=Arial][SIZE=2]/boot[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]GRUB[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]/[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]/home[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Swap[/SIZE][/FONT]
[/LIST]
 
[/LIST]
[FONT=Arial][SIZE=2]
Turned out great, now i just have to migrate my files.

--Adrastus

Anyone else interested in a similar set up might take a look at:
[/SIZE][/FONT][http://maketecheasier.com/quick-guide-to-linux-partition-schemes/2009/12/17](http://maketecheasier.com/quick-guide-to-linux-partition-schemes/2009/12/17)
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

---

