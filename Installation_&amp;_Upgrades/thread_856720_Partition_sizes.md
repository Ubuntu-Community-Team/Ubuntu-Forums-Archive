---
title: "Partition sizes?"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by jamh.unm on 2008-07-11
Specs:
780i SLI evga mobo
2GB ram
Q6600 running @ 2.66
nvidia 8800 GTX
500GB hard drive.

I have windows XP SP3 taking up 100gb, I need a partition that both windows and linux can share, I believe it needs to be fat32...?  My questions is how big and what other partitions do I need to create?

PS I'm installing Ubuntu Hardy Heron

---

### Post by ibutho on 2008-07-11
You can use ntfs or fat32 to share files between Linux and Windows. If you choose to use ntfs, you will need to install ntfs-3g which enables read and write support for ntfs partitions from Linux. The partition sizes really depends on what you intend to do with the system. For Linux, at a minimum, you need a root parittion (symbol /) which will contain your system files, a /home partition for your personal files and swap which is virtual memory.

---

### Post by Bakon Jarser on 2008-07-11
Don't use fat32.  Ubuntu should have ntfs read/write access enabled by default.  Also there are programs that allow windows to recognize ext3 partitions.  Ubuntu may not automount your ntfs drives be default though.  An easy way to make that happen is to install ntfs configuration tool.

---

### Post by Sef on 2008-07-11
> For Linux, at a minimum, you need a root parittion (symbol /) which will contain your system files, a /home partition for your personal files and swap which is virtual memory.

For Ubuntu, you should make root about 8-10 GB.  Home is not required, but it is good to have in case of reinstall or problems with root.  Swap size:  512 MB ram or more, then 1 GB of swap.  Less than than 512 MB, then 1 1/2 - 2 times ram.

---

### Post by jamh.unm on 2008-07-11
Ok I was thinking:

4GB for swap
20GB for /

and thats where I get lost, do I need a /home partition if I'm going to keep most of my files for music, photos, video, etc. in the NTFS partition so that XP can access them as well?

Reminder I have 400GB available for linux, the only real reasons I still have XP is for gaming and my Ipod...

---

### Post by Bakon Jarser on 2008-07-11
Your home folder will mostly be for storing your configuration files.  It is useful to have it on a seperate partition if you have to reinstall Ubuntu because you won't lose your settings for all of your programs.  If you don't have a seperate partition for /home then your homefolder will be on the same partition as your root (/) folder.  There's nothing wrong with either approach, but since you have lots of hard drive space you might want a seperate home partition.  I have a 500gb hard drive myself and have it set up like this.

swap 2gb
windows 25gb
/ 10gb (for Ubuntu)
/home 20gb
/ 10gb (for Linux Mint)
and the rest is storage space

I probably could have gone with a smaller /home partition but I'm using it for two different linux distros and soon I'll be adding a third (I just like trying different distros out)

---

### Post by ibutho on 2008-07-11
> **jamh.unm said:**
> Ok I was thinking:

4GB for swap
20GB for /

and thats where I get lost, do I need a /home partition if I'm going to keep most of my files for music, photos, video, etc. in the NTFS partition so that XP can access them as well?

Reminder I have 400GB available for linux, the only real reasons I still have XP is for gaming and my Ipod...

4GB is too much for SWAP. You can get by with 512MB or 1GB. I personally think you should have a separate /home partition. If you ever need to do a reinstall or a clean install of a newer version, its usually best if /home is on a separate partition because you personal files and settings will remain untouched.

---

