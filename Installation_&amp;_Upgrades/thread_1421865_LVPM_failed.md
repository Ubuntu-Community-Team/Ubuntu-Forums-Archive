---
title: "LVPM failed"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by superarthur on 2010-03-04
I've been using wubi for about a week, and I am already running out of space. (I allocated 5 GB for wubi, and only 1.5 GB was left after installation =P)
Therefore, I decided to use LVPM to upgrade wubi to a standard Ubuntu system.
My laptop has 2 hard disks. My D drive is empty, and I used Partition Manager to completely delete it. There is suppose to be 60GB in my D drive. I then set up a new ext3 partition with 51.27 GB, and a linux-swap partition with 3.86 GB.

What I can see from partition manager is as follow:
/dev/sda/1 nfts WinRE 1GB
/dev/sda/2 nfts       55.68GB
/dev/sda/3 ext3       51.27GB
/dev/sda/4 linux-swap 3.86GB

So, I then booted onto wubi, and used LVPM. I selected transfer to /dev/sda/3.
After the transferring is done, I reboot and see the following:
Ubuntu-on-/dev/sda3
Other operating systems:
Unknown OS
Window Vista (loader)
Window Vista (loader)

When I clicked enter while highlighting Ubuntu-on-/dev/sda3, nothing happened.
When I clicked enter while highlighting Unknown OS, I get back to my old boot up screen where I can choose between vista and ubuntu. After booting to ubuntu, I just got back to my old wubi installation.
The Window Vista (loader) options bring me to Window vista recovery mode.

Can anyone provide help, please?

---

### Post by superarthur on 2010-03-05
can somebody help me please? sorry for pushing the post, but you will get worried if your computer is messed up.

---

### Post by shakenama on 2010-03-29
[FONT=Arial][SIZE=2]superarthur -
 Did you ever resolve the issue with Grub and the UnknownOS tag? 
 Just asking because I have the exact same issue. I'm wanting to edit Grub, or Menu.lst in Ubuntu, but not sure on how to go about it. If you fixed the problem, please let me know how you did it. I'd appreciate it ;)[/SIZE][/FONT]

---

### Post by superarthur on 2010-03-29
actually, I solved the problem by burning a CD and install a fresh Ubuntu. LOL
I haven't marked this thread as solved because:
a) I've forgotten to :P
b) the real problem hasn't been solved, just avoided

---

