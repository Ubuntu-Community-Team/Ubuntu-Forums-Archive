---
title: "Remove Windows XP Completely"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by frankydt on 2008-06-19
Hi, I hope this is the right place to post this thread. If no, please accept my apologies.

I have a two disks machine (80g each) and I have installed Windows XP first, then Ubuntu. I have never went back to using Windows. I feel great, pleased, and grateful to be using such a good OS. I had some short-comings but everything has a solution and a configuration. 

I have my Ubuntu Drive (80g) almost full (of crap basically but anyways). So I want to reclaim my other sata drive now in the awful hands of windows and into the hands of my Ubuntu.

Two questions:

1- What is the best way of formatting my window drive, removing it from grub, etc?
(do I just right-click format and edit the /boot/grub/menu.list)

2- I have seen that my windows drive (2 partitions) have to be mounted and do not stay mounted once I restart (probably logout too). So can I have my formatted windows xp used to be drive easily mounted once I go trough with step 1?

Thanks in advance,
f(t)

---

### Post by logos34 on 2008-06-20
> **frankydt said:**
> 1- What is the best way of formatting my window drive, removing it from grub, etc?
(do I just right-click format and edit the /boot/grub/menu.list)

yep. Use Gparted to unmount them, then delete both ntfs partitions. Remove windows from menu.lst and Don't forget the lines in /etc/fstab.
> 
2- I have seen that my windows drive (2 partitions) have to be mounted and do not stay mounted once I restart (probably logout too). So can I have my formatted windows xp used to be drive easily mounted once I go trough with step 1?

I'd make one or more ext3 partitions, rather than continue to use reformatted ntfs.

It's all covered here

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by frankydt on 2008-06-20
> **logos34 said:**
> yep. Use Gparted to unmount them, then delete both ntfs partitions. Remove windows from menu.lst and Don't forget the lines in /etc/fstab.


I'd make one or more ext3 partitions, rather than continue to use reformatted ntfs.

It's all covered here

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Thanks for the reply.
f(t)

---

