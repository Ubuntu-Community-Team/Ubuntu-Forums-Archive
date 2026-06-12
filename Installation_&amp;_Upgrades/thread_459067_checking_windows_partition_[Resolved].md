---
title: "checking windows partition [Resolved]"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by cequiel on 2007-05-30
hello.

I have installed a dual-boot Windows XP and Ubuntu. when I start Ubuntu it spend a lot of time of checking the windows partition.

that is good, because I can recover some files in the Windows partition, but I would like to know how to disable this option and enable it later (if it is needed).

(sorry for my English)

---

### Post by aysiu on 2007-05-30
What do you mean by "checking"?

---

### Post by cequiel on 2007-05-30
:D by checking I mean Ubuntu is examining the whole structure of the windows partition each time it is mounted.

In any case I have solved this problem. Just edit the file /etc/fstab and comment the line that tells Ubuntu to mount the partition.

Here is the source with the solution:
[How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

Now, Ubuntu start up faster.

---

