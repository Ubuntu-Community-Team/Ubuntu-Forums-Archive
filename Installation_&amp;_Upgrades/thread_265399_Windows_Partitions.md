---
title: "Windows Partitions"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by Dimtar on 2006-09-25
Hi Guys. I have tried to install Ubuntu. I stopped because i could not understand the way Linux does partitions. I understand the whole root and home and swap partitions. On my main pc i have 3 partitions one for Windows and one for Vista and one for all my actual files.

What i want to do on the pc i am installing Ubuntu on is similar. I want to have two partitions. One say 100 gig for my XP partition and one say 20 gig for my Ubuntu (hope to expand later) Is this just a stupid idea? Can it be done with the installer? (I have partition magic should it be needed)

Before anyone says remove the xp partition and use it all for Linux , i can't. I don't have the space to move my laptop files firstly. Secondly i want to get Ubuntu setup and i want to feel comfortable with it before i pack in XP for good.

Any help would be great. Thanks guys and sorry if this has been asked recently. I did have a look first to see if i could find it.

---

### Post by catlett on 2006-09-25
The installer has a selection for 'resizing' your partition. This will let you 'shrink' the windows partition and then install ubuntu on it. The instaler will do all the partitioning for you. It will allow you to choose the size of ubuntu's partition. Then it will shrink xp and make a root and swap partition. Then it will install the OS.
Aysiu's guide has screen shots of the selection [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) That will show you the screens that will appear and then the disk preperation page. The resize option is the first choice.

---

### Post by Mr Frosti on 2006-09-25
I think that the best approach is to ease into Linux, so your request is not unreasonable. You must first know some "gotchas" about your file system layout.

First, Windows partitions (NTFS) can not currently be written to from Linux. This is experimental and will hopefully change in the near future. You can however, read your documents on an NTFS partition from Linux.

Second, Windows does not understand any file system that isn't itself. (Great interoperability, I know). There are third party tools available to read from the popular Linux filesystem types such as Ext2 and Ext3. 

My suggestion, if you just need an occasional file from your Windows drive, is to read and copy the file from inside Linux. Install the Windows plugins that will allow you to read from your Linux partition if need be.

If you have a large collection of files that need to be constantly accessable from both, you might want to create a neutral, extra FAT32 partition for all of your documents. This file system can be both read / written to from Windows and Linux.

You can do this from inside the Ubuntu installation CD. Boot from the CD, and under the partition section, choose the advanced section. You can resize existing partitions, create new partitions, and choose their mount points. It sounds intimidating, but it is graphical, so I think that you will find it not to be that bad. Especially if you are familiar with the concepts of filesystems, and Partition Magic which you seem to be.

---

