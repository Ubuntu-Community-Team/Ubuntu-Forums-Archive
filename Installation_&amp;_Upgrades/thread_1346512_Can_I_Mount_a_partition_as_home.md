---
title: "Can I Mount a partition as /home"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by llawwehttam on 2009-12-05
Up till now I've taken the easy option and put everything in one big partition but I'm going to be installing 9.10 on my new laptop and I've been advised to make separate partitions for my home folder and music etc.

 As /home already exists can i mount a separate partition as /home or will I have to put it in /mnt and call it something else? Also If I can mount it as /home,  if I then create a new user account will it create it on the mounted partition or on the same partition as / .

Also can I get another partition to mount where my current music folder is?

I'm not new to Linux but I've never really bothered with partitions so I don't really know how mounting works. I know I have to put entries in /etc/fstab and I know how to do that but I don't know what I can and can't do. I'm a bit reluctant to experiment as I don't want to lose everything!

---

### Post by darkod on 2009-12-05
You can set up separate partition and mount it as /home. That way all users will be created there. From inside ubuntu, it will look the same because even now you have folder home in /. But the benefit is that you can do clean install in future and format only / (to destroy previous version) but since /home is separate partition on the disk you just specify during the new install to mount it and all data is there (be careful not to format it too).
For music not sure how it goes, but if you keep it in the home folder the above will apply.
You have to use manual partitioning when installing to make /home. This is what I have, sort of the basic system with partitions
/
swap
/home

You do not need to know anything special about the mounting if you are doing this on new install. You just specify mount points when creating the partitions. Ubuntu will take care of the rest. Entries are made automatically in /etc/fstab.If you want to make some adjustments to a current system, I am not experienced enough to give you the procedure what to do.

---

### Post by weedwacker on 2009-12-05
Read this as a start: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

What you want is near the bottom.

Also, try Psychocats: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
On the left column is "Beyond the Basics" and a link to "make a /home partition.

---

### Post by llawwehttam on 2009-12-05
Well thanks a lot guys. As usual you answered my questions quickly and in language I can understand.

This is exactly why I use Linux. There is always someone to help!!!

---

