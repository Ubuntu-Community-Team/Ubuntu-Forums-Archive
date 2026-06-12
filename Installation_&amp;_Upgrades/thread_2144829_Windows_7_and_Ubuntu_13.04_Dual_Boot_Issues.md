---
title: "Windows 7 and Ubuntu 13.04 Dual Boot Issues"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by skibum3027 on 2013-05-13
I recently reformatted a computer and installed Windows 7 and Ubuntu 13.04 on two different hard drives (sdd and sdc, respectively). Following the install, I noticed that another hard drive, sde, had gone from having 2.2 TB used (my TV collection) and around 600gb free space left to having 8 gb left of free space. The size of the files hasn't changed, there's no extra partitions listed by either Windows Disk Management or gparted. In addition to the free space issues, Windows is only showing a few of the folders in the homegroup at all, and those only show up for the first few minutes after a reboot, after which they are no longer accessible from all the rest of the computers in my house.

I started t/s with the usual method of googling my problem worded a few different ways and even tried to search the forums, but all that turned up was people with no idea how to partition their disk drives. I don't have an extra 2 TB of space, only about 800 gb oustide of sde, so I can't move the files to another disk for temporary storage and reformat the drive.

Does anyone know what happened? How can a fresh OS install affect a hard disk drive it didn't change? Can I get my disk space back and homegroup working again?

Thanks for any help!!!

---

### Post by oldfred on 2013-05-13
Is Ubuntu working ok. If so mount various partitions you may be concerned about and run this:

df -h

What format is the partition you are concerned about?
sudo parted -l

---

### Post by skibum3027 on 2013-05-13
Ubuntu and Windows both boot normally, and the disk mounts. It shows one partition with 2.6TB used. I moved some shows around and freed up 163GB so the drive isn't completely full, but there should be an additional 571 GB of the space that is unaccounted for. That space shows up in windirstat as "unknown."  I know Windows System Protection can show up as unknown space, but it's not enabled for that drive. The partition is NFTS. Let me know if there's any other commands you'd like the output of and thanks for helping!!!

michael@michael-PC:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
/dev/sdc5               132G  4.1G  121G   4% /
none                    4.0K     0  4.0K   0% /sys/fs/cgroup
udev                    3.9G  4.0K  3.9G   1% /dev
tmpfs                   799M  888K  798M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    3.9G  228K  3.9G   1% /run/shm
none                    100M   16K  100M   1% /run/user
/dev/sdc1               226M   46M  169M  22% /boot
/home/michael/.Private  132G  4.1G  121G   4% /home/michael
/dev/sde2               2.8T  2.6T  163G  95% /media/michael/TV Shows

---

### Post by oldfred on 2013-05-13
Linux is seeing the entire 2.8GB but saying it is 2.6GB used. In Linux you have to empty trash before the space is freed up. Did you delete from Linux or from Windows. Not sure how Windows does it anymore. But automounts in Linux may leave trash?

Huge partition, but sometimes NTFS needs chkdsk, it will take a long time on that large of a partition.

---

### Post by skibum3027 on 2013-05-13
I haven't deleted anything of significant size. chkdsk is almost an hour in, and so far it's about 10% done. I'll post the results when it finishes.

---

### Post by skibum3027 on 2013-05-14
chkdsk just finished, and it worked!!!
Thanks for your help!!

---

### Post by oldfred on 2013-05-14
Glad that worked. :)

---

