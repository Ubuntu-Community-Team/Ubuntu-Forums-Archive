---
title: "How to Ubuntu 14.04 /home folder to System partition - step by step please?"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by Onl on 2014-10-20
How to Ubuntu 14.04 /home folder to System partition - step by step please?

---

### Post by oldfred on 2014-10-20
Not sure what question is?

/home by default is inside / (root) which is the system partition. You cannot use Windows or any NTFS for /home.

If you want /home on a separate partition you can do that during install with Something Else or move it afterwards. 
This has details.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Onl on 2014-10-20
sda5 (/home folder) move the sda3 ( boot) partition
[IMG]https://scontent-a-fra.xx.fbcdn.net/hphotos-xap1/v/t1.0-9/s720x720/1620486_281559625388442_5442783428905969653_n.png?oh=e67108dde7408455deabb38052d4b259&oe=54B5951B[/IMG]

---

### Post by oldfred on 2014-10-20
Just do the reverse of the process to create a separate /home partition in link above.

You need to copy all your data into the /home/$USER folder inside you / (root) and edit fstab to remove the /home partition.

---

