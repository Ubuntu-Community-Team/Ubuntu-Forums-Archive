---
title: "Possible to install Ubuntu without removing windows?"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Xamindar on 2008-01-18
Is there any way to modify the partition without removing windows?  I have a new computer here that didn't come with a Vista DVD to reinstall so I just want to modify the partition (split the drive in half) to add Linux to it.  I'm interested any any programs even if I need to buy them.  Will partition magic do what I need?  Or is it impossible?

Thanks.

---

### Post by Partyboi2 on 2008-01-18
Hi, There is a disk management program in Vista that will allow you to shrink Vista to make room for ubuntu. Once you have shrink Vista by the disk management, defrag and install ubuntu:)

---

### Post by Pandemic187 on 2008-01-18
You don't need any added programs. You just have to choose the option to manually partition the drive during the install process. See the attached thumbnail which shows the correct option there.

Then, you have to decide for yourself how much space you want to allocate for Ubuntu. I'm not sure what you'll be using it for, so that's really up to you. If you'll be using Windows a lot more, then you should allocate most of you hard drive to Windows. Either way, you'll have to resize the drive, which the installer makes fairly simple.

Then, you should make a swap partition, which I usually allocate 1 GB toward. You also want an ext3 partition which will be your main file system for Linux. For your ext3 partition, you should make "/" the mount point, minus the quotation marks. I usually select "dontuse" as the type for Windows partitions, but if you plan to access your Windows documents, you can leave them enabled. I just don't like that because it makes your Windows partitions show up on the desktop on each startup...this can be changed after the install, but it's easier to disable during the install process.

Hope this helps.

---

### Post by aysiu on 2008-01-18
There is if you know what you're doing.

If you don't know what you're doing, you may accidentally delete the Windows partition during installation.

These dual-boot guides might help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by Pandemic187 on 2008-01-18
> **Partyboi2 said:**
> Hi, There is a disk management program in Vista that will allow you to shrink Vista to make room for ubuntu. Once you have shrink Vista by the disk management, defrag and install ubuntu:)
Or you can do it during the Ubuntu install...

---

### Post by Partyboi2 on 2008-01-18
> **Pandemic187 said:**
> Or you can do it during the Ubuntu install...
Yes you can, but alot of people have run into problems as the partition editor on the live cd does not always like Vista. In saying that I have heard of a few people that did not run into problems. I guess you could try either way and if one way does not work then try the other. :)

---

### Post by Pandemic187 on 2008-01-18
> **Partyboi2 said:**
> Yes you can, but alot of people have run into problems as the partition editor on the live cd does not always like Vista. In saying that I have heard of a few people that did not run into problems. I guess you could try either way and if one way does not work then try the other. :)
Oh. Fortunately I haven't used Vista...well except for RC2.

---

### Post by Xamindar on 2008-01-18
> **Pandemic187 said:**
> Or you can do it during the Ubuntu install...

Hmm, I was always worried that while resizing it I would corrupt the Windows partition because it might erase any files that were stored at the end of the disk on the part I took away.


Thanks for all the replies.  I didn't know vista had a resize tool, I'll look into that.  If it does it would be exactly what I need.  I'm sure I'll be able to install Ubuntu just fine after I get the partition resized.

---

### Post by Xamindar on 2008-01-18
> **Pandemic187 said:**
> You don't need any added programs. You just have to choose the option to manually partition the drive during the install process. 

wait, so this will resize the windows ntfs partition for me while keeping windows in tact?

---

### Post by forestpixie on 2008-01-18
it should but as partbois has said there have been problems for some - better to use the vista tool to make some space

---

### Post by erfahren on 2008-01-18
Xamindar - just a side note here....

you mentioned that you didn't get a Vista disk - most brand-name PCs these days don't come with the disks but provide a way to burn it off instead.

the manual should mention that and give instructions how. it'll probably be in a folder off of Vista 's "All Programs" menu. -- you'll want to burn one off.

---

### Post by Pandemic187 on 2008-01-18
> **Xamindar said:**
> wait, so this will resize the windows ntfs partition for me while keeping windows in tact?

> **Partyboi2 said:**
> Yes..., but alot of people have run into problems as the partition editor on the live cd does not always like Vista. In saying that I have heard of a few people that did not run into problems. I guess you could try either way and if one way does not work then try the other. :)

> **Pandemic187 said:**
> Oh. Fortunately I haven't used Vista...well except for RC2.

Does seeing these three together help at all? Like I said, I haven't used Vista and Ubuntu in dual-boot. I've only used Ubuntu + XP. Thus, I would take Partyboi's advice and use the Vista partition editor. Either way, I would suggest that if you have important files on your Vista partition that you back them up since it sounds like you haven't done this before.

---

### Post by Xamindar on 2008-01-24
Hey thanks for all the help.  I finally used the vista partitioner and resized my vista partition.  Was able to get 35gigs available for linux.  It`s very nice of vista to have something like that. :)

---

