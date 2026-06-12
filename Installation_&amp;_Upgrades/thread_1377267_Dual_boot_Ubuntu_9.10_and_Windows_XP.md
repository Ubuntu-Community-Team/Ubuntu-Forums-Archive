---
title: "Dual boot Ubuntu 9.10 and Windows XP"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by sunnypilott on 2010-01-10
I have a 160 GB hard disk with three partitions (All NTFS):

C: (30 GB) (WINDOWS XP system partition)
D: (60 GB)
E: (60 GB)

I want to install Ubuntu on another drive (D: in this case). I have backed up all my data on D: drive. What are the steps in doing so and does Ubuntu support NTFS? If it does then will I be able to read and move data between all the drives without any problem (while running either of operating systems)?

---

### Post by jocampo on 2010-01-10
> **sunnypilott said:**
> I have a 160 GB hard disk with three partitions (All NTFS):

C: (30 GB) (WINDOWS XP system partition)
D: (60 GB)
E: (60 GB)

I want to install Ubuntu on another drive (D: in this case). I have backed up all my data on D: drive. What are the steps in doing so and does Ubuntu support NTFS? If it does then will I be able to read and move data between all the drives without any problem (while running either of operating systems)?

Yes, you can see and write on your NTFS partitions from Ubuntu. 

Now, if you backed up D already I would suggest destroy D and E and create different layout. 

C - DO NOT touch
D - 10gb Ubuntu root partition
E - 50gb (suggested size) for /home
E - remaining on NTFS (or so, because you need to leave 1 for swap)

You should be able to see F from any Os, Window$ or Linux.

Just be sure of NOT TOUCHING C when running Ubuntu setup. Linux will create the dual boot for you. It could be a good idea "clone" or get an image of C drive, just in case things go wrong. When running Ubuntu live CD, create space or partitions for D, E and leave the space for E unformatted. Finish setup and then boot on Windows. From Windows go to disk manager and format the space you left using NTFS.

---

### Post by portable-linux.com on 2010-01-10
I would suggest you to install ubuntu within windows you can do that by using the wubi.exe file present in the ubuntu 9.10 cd. you just have to mention the partition you would like to install ubuntu. Select a partition other than the partition where the Windows XP is setup and thats it.Witin 20 minutes you will be running ubuntu. Its that simple:D

Yes Ubuntu does support NTFS.

---

### Post by jocampo on 2010-01-10
> **portable-linux.com said:**
> I would suggest you to install ubuntu within windows you can do that by using the wubi.exe file present in the ubuntu 9.10 cd. you just have to mention the partition you would like to install ubuntu. Select a partition other than the partition where the Windows XP is setup and thats it.Witin 20 minutes you will be running ubuntu. Its that simple:D

Yes Ubuntu does support NTFS.

Easy solution but will not get good performance. Ubuntu will be using the horrible NTFS file-system that comes with windows. Dual boot provides much better performance and still you can see the shared NTFS partition from both.

---

