---
title: "[SOLVED] Ubuntu 8.04 LTS install problem"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by ubume2 on 2008-04-29
Resolved: I successfully installed 8.04LTS on my "wired" computer. It is dual booted with Windows XP. Doing nicely, except for this bug:  boxes opening up all over the place when I designated an unsupported printer.

I have been a previous user of Dapper. I have Windows XP installed.[I know,I know] Tried to install 8.04 after I deleted Dapper and merged that partition with Windows. When I got to partitioning, Ubuntu wanted to use all of the remaining drive space. 67GB on my 80GB drive.  There was no way to change partition size in 8.04. It did on 6.06  The CD rom checked out ok.  The install of 8.04 Squeezed XP so bad many of the apps were unusable. I then reinstalled 6.06 and tried to install 8.04 in the EXT3 partition. 8.04 again would not allow me to change partition size.  It would only allow 2% of the space for 6.06. I abandoned that install.

I reinstalled 6.06LTS along with windows. Ubuntu has 35GB in its partition. Works fine except can't connect to wireless. _Is there a problem [bug] with 8.04 in not allowing the adjustment of partition size?_

I've read about WUBI, and later about lubi. _Is that a viable alternative to having separate partitions for XP and Ubuntu? Any drawbacks?_ I am not ready, nor can I, to commit to Ubuntu on the whole HDD. I do not have a 2nd hd. I ve done a little with 8.04 on liveCD and I like what I see. Would like to install it now along with Windows

Please help
Thanks

---

### Post by Rallg on 2008-04-29
Before you do anything else, boot to XP in ordinary fashion, and run the disk check (it may run automatically if you recently did anything to change the Windows partition size). Then, look at how much disk space is taken up by your Windows-accessible partitions (many computers come with a Windows recovery partition, in addition to the Windows operating system partition). If the sum of partitions is much less than your hard drive size, then you still have a Linux partition lurking somewhere. Keep in mind that hard drive manufacturers specify size in a manner that is slightly different than the way that software measures size, so don't worry about a small difference.

If everything makes sense, defragment your XP.

You didn't mention how you dual-booted when you had Dapper. Was it using Grub, initiated by the MBR? If so, was Grub on the Dapper partition, or was it on the XP partition, or on external media?

Once you get to the point where your system is "like new" in XP, then others on this forum may be able to provide more detailed info. I would, but XP and Vista have different tricks that can be used in a multi-boot environment, and I don't have XP.

---

### Post by ubume2 on 2008-04-29
Thanks Rallg for your post.  The mbr was in the linux partition. Found out the hard way. Deleted the linux partition with PM and voila--a grub 22 error msg.  After reinstalling XP from scratch twice, I found out an easy fix using the OS install cd and repairing the mbr

After trying again to install 8.04 along with XP [that I had freshly installed], Windows would boot up but it did not function properly. the installation of 8.04 only allowed 10GB for XP. In Dapper, I could adjust the size of that partition [the XP partition] to allow for installation of Ubuntu. It would install without problems.

In 8.04 installation,even in guided installation, it would take up all of the unused space on the hard drive.  The size of the partition could not be adjusted as in Dapper.

At this point, I am leery of trying to install 8.04 again. Am reinstalling 6.06LTS. 

Input appreciated.
Thanks

---

