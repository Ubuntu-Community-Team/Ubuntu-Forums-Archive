---
title: "Best partition scheme for multiple linux distros?"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by NobleSavage on 2006-12-23
I posted this in the General forum and didn't get any takers - I think it would have been more appropriate in this forum.

My experience with Linux and Ubuntu in the past has either been dual boot Win/Linux or just Linux. I have never run more than one Linux distro on the same box. 

Anyhow I have a new box that I'm going to use for just screwing around and learning.  I plan to try out different Linux distros and maybe some of the Ubuntu testing stuff. This computer will not have Windows on it.  Before I just dive in and start installing I thought I'd ask some of the more experienced users here for advice, tips, things to look out for, etc 

1) Any suggestions as to best partition scheme?


2) This may be a dumb question, but Is it possible to have a /home partition that can be shared by all the different distros?

Thanks!

---

### Post by djgrandmarquis on 2006-12-23
I'll be doing something similar within the week. Here are a couple of thoughts:

1) I'm planning on putting the /root partitions (one partition for each distro) on my new Raptor drive. Then other data will go on my other two drives. If you have multiple drives, spread your swap across them; the kernel can optimize the usage.

2) Yes, definitely! It's a good idea, because it will preserve your settings, etc. for multiple distros. I'm also making a separate partition for multimedia. That way, a fresh install won't wipe out my music.

Best of luck!

---

### Post by NobleSavage on 2006-12-23
> **djgrandmarquis said:**
> I'll be doing something similar within the week. Here are a couple of thoughts:

1) I'm planning on putting the /root partitions (one partition for each distro) on my new Raptor drive. Then other data will go on my other two drives. 

That sounds like a good idea.

> If you have multiple drives, 
Yes, I do...

> 
spread your swap across them; the kernel can optimize the usage.


How do I do this? Just create a swap partition on each drive? 

Thanks!

---

### Post by bernied on 2006-12-23
Some things to think about:
- when ubuntu upgrades its kernel it runs a debian script on the grub menu.lst file, which will change your boot options. This is something you want, but it might be difficult to have several distros behaving the same way on the same file. My solution to this has been to have a boot partition with just grub on it, that boots all other OSs.  All other OSs are chainloaded, like this:
```
title Any linux distro
root (hd0,2)
chainloader +1
```The advantage of this is that you let the distro set up its own boot method, but **only on its own partition**. So when the ubuntu install asks you where to install grub, you tell it do it only on its partition, not the MBR. Then you don't have to fix up every other OSs boot.

- as for a /home partition, be very careful with this - when user:group information is stored in a filesystem it is stored as numbers, not names. The names of users and groups are translated using the /etc/passwd and /etc/group files - that's where you'll find the numbers. So, if you are going to share users, make sure they have the same UID and GIDs. Or, don't do it. Also having shared configuration directories (in /home) is likely to lead to grief, especially if you're running different versions of desktops or desktop apps. 

- much easier than sharing /home partition is to have a partition in a filesystem that doesn't have permissions, like VFAT, that you can share among all OSs.

have fun!

---

### Post by bernied on 2006-12-23
And, as for swaps, the kernel (as far as I know) will only use the second when the first is full, so make your first swap partition on a disk that is not used for very much else. So if your /usr and your /home is on disk one, use a swap on disk two. Just put the swaps in your /etc/fstab.

---

### Post by djgrandmarquis on 2006-12-23
Good thoughts on GRUB, bernied. I forgot to mention my /boot partition.

I recently read an article about swap & the Linux kernel. I was pretty impressed that it can use swap like a striped RAID array:
[http://tldp.org/HOWTO/Partition/setting_up_swap.html#multiple_swap_areas](http://tldp.org/HOWTO/Partition/setting_up_swap.html#multiple_swap_areas)

---

### Post by bernied on 2006-12-23
OK - thanks for the education, I didn't know about that.

---

### Post by NobleSavage on 2006-12-25
Merry Christmas!

Ok guys,  I'm gotten myself completely confused on the boot process.  My original understanding went something like this:

I install Grub on the MBR.   I install each distro on a separate partition.  I tell Grub the location of the various distros in the menu.lst file in the MBR.  Each distro has it's own /boot partition with kernel(s).

Do you install Grub in each /boot partition as well?  Or do you set up one boot partition for all distros?

I realized something may be wrong in my logic when Gparted would only allow me to make flag one partition "bootable".   I've spent the last 24 hrs reading various documentation and the Grub documentation and now I'm really mixed up.  ](*,) Most of the stuff I found seems dated. If anyone can explain this to me and or link me to a good resource I'd be very grateful.  

Thanks.

---

### Post by bernied on 2006-12-26
The last thing first, as far as I know Windows/DOS are the only OSs that need the bootable flag set on a partition, so leave the flag set on the Windows partition and don't worry about it for linux. The only time you have to think about it is if you are booting more than one Windows/MS-DOS OS (nasty! surely one is too many).

About the grub stuff, fisrtly you don't have to really know about any of this stuff, Ubuntu generally looks after it all for you. I suggest you start with one linux distro and make it work for you. You don't need a separate /boot partition.

All you need is one partition for each different OS (even this is not strictly true, but it is advisable). Let Ubuntu install grub onto the ubuntu partition, then start from there.

But maybe leave plenty of spare space for new partitions, so you can mess about with other installs later (and maybe think about how to set up a booting system that won't be bothered if one day you decide to totally wipe that original ubuntu partition - that's where I was going).

---

