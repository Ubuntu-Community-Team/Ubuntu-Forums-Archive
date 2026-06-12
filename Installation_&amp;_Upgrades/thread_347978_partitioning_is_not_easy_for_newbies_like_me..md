---
title: "partitioning is not easy for newbies like me."
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by ramster on 2007-01-28
Ubuntu Linux for Non-Geeks and The Official Ubuntu Book do not give me any idea on how to partition the drive (dual boot with Windows). I have tried other distros and was provided with a standard type partitioning system which worked fine. Yes the books tell one how but I don't understand. Undoubtedly my fault but without partitioning I can't get it running. Have problems further down the track with Mandriva, Suse and Fedora and hoped Ubuntu was the answer.
                                                                                             ramster

---

### Post by housam on 2007-01-28
Try this guide:
You have to defrag the windows partition at least two times before the resizing. and also back-up all your data and files.
Now you can use the Gparted partitioning tool to do the job. it is on the live CD . you boot through the live CD and click system >> admin. >> Gnome partition editor.
Resize the windows ( by clicking on the partition and shrinking it from the right end ) to create an unallocated space of about 11Gb ( or what ever you like )
Now devide the unallocated space to two new partitions:
10 Gb ext3 for the root ( / )
1 Gb swap for the ( swap )
You can add another ext3 partition as /home 
After that go for the installation and when it comes to the partition mater , choose the manual way .

Good luck.
__________________

---

### Post by Zander_Z on 2007-01-28
I try to use the Gnome Partitioning tool and set up the space for the partitions I need to create and it tells me that none of the operations could be performed. I'm trying to set up a dual boot part so the rest of the family can use Windows XP, and I can use Ubuntu. I read online that the newer versions of Ubuntu don't support a partitioning system that splits NTFS. Is there a way I can split the NTFS into partitions that I can use to set up Ubuntu?

---

### Post by meng on 2007-01-28
You should tell us what partitions are on your hard drive to start with. For example, if you already have 4 primary partitions, you can't create any others without deleting one of your primary partitions first.

---

### Post by Zander_Z on 2007-01-28
I have a /dev/sda1 (Which ntfs runs on) which is 289.28 GiB in size
and a /dev/sda2 (which my fat32 runs on) which is 8.80 GiB in size along with an unallocated 7.38 MiB in size.

---

### Post by meng on 2007-01-28
And have you defragmented these partitions with Windows Disk Defragmenter or similar tool? Could there be data towards the end of these partitions which is making it difficult for GParted to resize these?

What changes are you hoping to get the partitioning tool to institute? You may find that GParted Live CD has better support for moving/resizing NFTS and FAT than the version of GParted included with the Ubuntu install.

Above all, make sure you have your critical data backed up!

---

### Post by Zander_Z on 2007-01-28
I did try defragmenting a few times, but I'll attempt again. All crit data has been backed up ^_^

---

### Post by Zander_Z on 2007-01-28
I hope to split the NTFS into extra room for linux (Specifically so that I can dual boot windows and linux). I need to create a partition for the root, and the swap, and then a /home. I'd like about 100 gigs for Linux to run, leaving about 120 for my windows set up. I'm currently defragmenting my windows NTFS partition

---

### Post by breakaway on 2007-01-28
There is no need for any of this. All you have to do, is free up about 10GB of space anywhere on your drive. (For this, I use PowerQuest Partition Magic)

Providing that it's a modern compute, it won't have any trouble loading the kernel from the back of a large drive (Like Mine) -

```

[ [          10GB - Windows Partition NTFS          ][          40GB - Windows Storage NTFS          ][        Free Space - 10GB          ] ]

```

After installation of Kubuntu

```

[ [          10GB - Windows Partition NTFS          ][          40GB - Windows Storage NTFS          ][          Linux Main - 10GB          ][          Linux Swap - 512MB          ] ]

```

Slap the ubuntu disc in, and when it asks you during installation, select "Use Free Space". And it will automatically partition the space and you'll be away laughing.

---

### Post by rocknrolf77 on 2007-01-28
It's just better to have a seperate /home partition when you upgrade your system. Then you get to keep all your settings and files. And a fresh install on upgrade is also better.

Read this : [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) :)

---

