---
title: "Question about partitioning"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by Dawar on 2006-10-18
I wanna install Ubuntu 6.06 and when i get to step about partitioning i select my new created partition with 9gigs
After that he tells me to set up main partition and that. I select for that partition to be main (/) but i dont know what to put on my other 2 partitions because i dont wanna to erase that (my files and XP is on it) 
And do i need special partition for swap?

Tnx a lot :D

---

### Post by Kateikyoushi on 2006-10-18
Yes, you need a swap partition especially if you are low on ram, make it 512MB. Here is an installation guide which also explaines partitioning. [LINK]("http://www.psychocats.net/ubuntu/installing").

---

### Post by Dawar on 2006-10-18
Ok that means that i must put /windows on my windows partition and on other where's files put /documents
But i dont wanna to convert that partitions from NTFS to linux file system

---

### Post by Kateikyoushi on 2006-10-18
To install linx you need a new filesystem where linux can be installed.
You can keep your windows filesystem just resize it to make space for linux, then following the guide make a / partition ext3 filesystem is recommended and a 512MB swap partition.

9GB is enough for linux, then make a 8.5 GB / partition and a 512MB swap.

I also recommend to backup your important data every time before you make filesystem changes.

Read that guide it is very helpful for beginners.

---

### Post by Dawar on 2006-10-18
Ok i read it and i understand all but please tell me what to put for windows and file partition on this [http://img206.imageshack.us/img206/8928/w2u31a6qs.png](http://img206.imageshack.us/img206/8928/w2u31a6qs.png) i dont wanna to put file partition with linux.:D

---

### Post by Kateikyoushi on 2006-10-18
The first partition is your windows do not set mount point for it, leave it as it is, you can also leave your documents partition without a mount point. It will be automatically mounted anyway.

---

### Post by Dawar on 2006-10-19
I have 1 more question if i set a mount point to my documents partition (NTFS) do u know if that will erase my files or keep it. And if it keeps it can i see them through windows :)

---

### Post by bulldog on 2006-10-19
Don't make any more mountpoints then needed.

Just make / [root partition] and a swap and if you have space left you can make a /home so when you need to do a reinstal,your personal data is save.

But don't go mounting windows partitions you could be badly sorry when things go wrong.

Your windows partitions are auto mounted so you can read and copy from them,you can't write to a NTFS file system by default.

But there are possibillity's but that's done later if necessary.

---

### Post by Dawar on 2006-10-19
Ok on my old partitions it tells me that he wants some /media6/ or something in the mount partitions windows should i leave it like there.
I know i am boring but i dont wanna to lose some important data or install it again :)

---

### Post by bulldog on 2006-10-19
I presume you have made space for your Ubuntu.

A save way is to make a / of about 10GB a swap about 512MB - 1GB.

The rest of your space you can make your /home.

Your windows partitions have to be unticked so they won't be formatted,be sure to look for this.

You don't have to do more.

Your windows partitions will be mounted in your /media folder of Ubuntu.

Just make sure your windows partitions will not be formatted.

---

### Post by Dawar on 2006-10-19
Are u sure if i select my NTFS file partition /home that it will be    intouched

---

### Post by bulldog on 2006-10-19
Nope that's not the way to do it.

You need to make space for your Ubuntu install and let it unallocated.

**That** space you gonna use for Ubuntu,no NTFS partitions!!!

And that space you can use to make a / a swap and a /home.

All your NTFS partitions are auto mounted but are **not** in anyway mixed up with your Ubuntu.

Example:

HDD = 80GB

split up 50 GB windows and 30GB Ubuntu

The 30 GB you can use to make,
10GB /
1GB swap
19GB /home

Your windows partitions will be visible in your Ubuntu [auto mount]

---

### Post by Dawar on 2006-10-19
Ok guys very very Thanks i made it and on my suprise it has installed in 4 minutes :)

---

### Post by bulldog on 2006-10-19
> **Dawar said:**
> Ok guys very very Thanks i made it and on my suprise it has installed in 4 minutes :)

Think you'll come back,Ubuntu is quick.........but that quick....](*,)

---

### Post by Dawar on 2006-10-19
It works perfect just i need to find some good mp3 player.
BTW do i need Antivirus and firewall for ubuntu ?

---

### Post by bulldog on 2006-10-19
If you plan to run a server yes you could use a antivirus program,otherwise not really.

Firestarter is a firewall for Ubuntu.

I use xmms and it's in the repositories,just enable universe and multiverse.

But there are much more.

Take a look at this site,it can provide you with a lot of programs codes java and much more.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

