---
title: "Need partitioning advice"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by Claire on 2006-08-14
I used Ubuntu Linux as the sole operating system on an old laptop for a few months, but I recently got a new laptop and I'm trying to set up a dual boot with Windows and Linux.  I installed [fs-drive]("http://www.fs-driver.org/index.html") so that I'll be able to have a /home ext3 partition that can be accessed from Linux and Windows for all my files, so my current plan is to partition my 100 gb (actual space: 93 gb) harddrive with a bootable Windows partition, a 10 gb bootable Linux partition, a 3 gb swap, and then a /home partition as big as I can make it.

My current issue, however, is that I made the mistake of putting my rather large music collection onto this computer already (17.4 gb of files currently), and I want to make the Windows partition as small as possible (so that the /home partition can be as big as possible), but I'm not sure if it's worth the hassle of deleting all the music files and then reloading them onto the /home partition after I've done all the partitioning.  I'm pretty sure this isn't possible but . . . is there any way for me to create the partitions and then after moving files from the Windows partition to the /home partition to resize those partitions?  Or is there some other possible solution I'm missing?

---

### Post by wieman01 on 2006-08-14
You can resize, move, delete, and copy partition under Ubuntu using **GParted** or under Windows using a tool called **PartitionMagic**. This is fairly simple and even allows your to create partition images.

I am taking advantage of both tools quite regularly.

---

### Post by Claire on 2006-08-14
Sweet!  Thanks for the info!

---

### Post by omgporye on 2006-08-15
Hi 

well im new to linux, i havent ever installed on a single computer. i usually boot form teh apc cover discs, have a look around, and then close it. My secondary system is runnin freedom linux that i never installed os i dont know how it was done.

My main question is what is the 2 partitions for. The swap partition and other one.

Im planning on havin xp pro and 6.06 run dual boot and was wonderin if anyone could kinda walk me through it.

---

### Post by wieman01 on 2006-08-15
The "swap" partition is usually twice the size of your RAM and is what Windows calls a "paging file" or "virtual memory". The "home" partition holds user data and is pretty much the same as "Documents and Settings" under Windows.

The "root" partition holds the kernel, programs, modules, etc.

---

### Post by omgporye on 2006-08-15
so you need 3 partitions for it? can the documents and settings one be held on a usb key? that way if i have 2 systems with it i can carry aroudn my usb key and stuff

---

### Post by wieman01 on 2006-08-15
> **omgporye said:**
> so you need 3 partitions for it? can the documents and settings one be held on a usb key? that way if i have 2 systems with it i can carry aroudn my usb key and stuff

You actually need 2 partitions only... "swap" as well as another one hosting "root, "home", and the rest.

As for the USB stick, I am sure you **can** do that, however, I have not tried it yet so I can't advise.

---

### Post by az on 2006-08-15
> **omgporye said:**
> so you need 3 partitions for it? can the documents and settings one be held on a usb key? that way if i have 2 systems with it i can carry aroudn my usb key and stuff

No, you don't need three partitions.  And you don't have to worry about partitioning.  The installer does all that for you.

You can back up your home files to a usb key as you describe, but I think it would be a much bigger hassle to have a home partition mounted on an external usb drive.  Just do it the old fashion way.

You can make a third home partition, but you don't need to.  Do it only if you have very specific reason to do so.

---

### Post by omgporye on 2006-08-15
ok 2 partitions for linux and 1 for xp any recomendations on sizes for linux? i have 200gb hdd (184) and im gonna use 15 for xp and whatever's left for other stuff. What order should i install os? linux forst or xp or doesnt it matter? 

Azz u been since 2004. are u like one of the main ubuntu guys?

---

### Post by az on 2006-08-15
> **omgporye said:**
> ok 2 partitions for linux and 1 for xp any recomendations on sizes for linux? i have 200gb hdd (184) and im gonna use 15 for xp and whatever's left for other stuff. What order should i install os? linux forst or xp or doesnt it matter? 

Windows first, then Linux.  Linux plays well with the other kids, windows doesn't.  Instlling linux will install a bootloader that will allow you to boot any detected OS on your computer.  Windows doesn't do that.

> **omgporye said:**
> 
Azz u been since 2004. are u like one of the main ubuntu guys?

No.

Actually, I have been since 1971.  And I'm just this guy, you know.

---

### Post by omgporye on 2006-08-15
ok awesome.  another thing whats with all the diff type partitions. Logical extended primary that all ican think of righ tnow whats the difference between them?

so i first make 15 gb partition for windows-install, then start chuck in ubuntu and use it's partition maker to do rest?

---

### Post by az on 2006-08-17
> **omgporye said:**
> ok awesome.  another thing whats with all the diff type partitions. Logical extended primary that all ican think of righ tnow whats the difference between them?

There can only by four primary or logical partitions.  In logical partitions, you can have more extended partitions.  But who cares?  You shouldn't have to fiddle with partitioning that much.

> **omgporye said:**
> 
so i first make 15 gb partition for windows-install, then start chuck in ubuntu and use it's partition maker to do rest?


Install windows on your whole drive and then use the ubuntu installer - it will ask you how small to shrink the windows partition.  That's as much partitioning as you need to fiddle with.

---

