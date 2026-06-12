---
title: "Install Ubuntu to trial then delete Windows?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Recked on 2008-02-23
Hello,

I would like to install Hardy and when it becomes final remove all my Windows XP partitions etc.

Is there a way to do this and then recoup the disk space formerly used by Windows for the Hardy installation?

Thank you

---

### Post by oldos2er on 2008-02-24
Yes. You'll want to choose the "Guided--Use entire disk" option during installation.

---

### Post by Recked on 2008-02-24
Hi,

Thanks for the quick reply, but how exactly do I remove the Windows partitions which include a scratch, "root" and "home" partition on a single 500 gig sata hard drive after Hardy goes final?

Thanks

---

### Post by Herman on 2008-02-24
First, avoid installing Ubuntu in separate partitions such as /boot /home and / (root) and so on. I don't know why anyone need to do that and it only makes things complicated for you. Just a simple install is best, with everything in  / (root), plus a swap area.

If you leave Windows at the start of the hard disk like most people do, you will have Ubuntu in the inside half of the hard disk, which is shown by most graphical disc partitioning programs as being 'to the right' of the Windows partition.

It's no problem for  a hard disk partitioning program to delete partitions. I'm not sure what you mean about your Windows partitions including a scratch, "root" and "home" partition. I didn't know Windows could be installed in separate partitions, I thought only Linux was like that. Anyhow, it only takes a second or so to delete any partition, I don't see any problem there.

Most hard disk partitioning programs have no problems resizing a partition containing a Linux file system to the right, but the blocks at the start, (or left-hand end) of the Linux file system seem to be not so simple to move.

Gnome Partition Editor can 'move' the root of a Linux file system these days but it's a very slow process. 

It is possible for most hard disk partitioning programs to copy and paste the entire partition from one location on the hard disk to another if there's room.
It's a lot quicker and easier if most of the files that are removable are copied to some other media and deleted first. (Your personal files).
So you could delete your Windows partition with [Gnome Partition Editor]("http://gparted.sourceforge.net/"), (GParted LiveCD), and copy your entire Ubuntu operating system to the beginning of your hard disk.
You would run into a minor problems caused by the fact that the copy of the operating system will have a new partition number and file system UUID number, but after editing a few configuration files your new copy of your Ubuntu operating system would be fine.
You would need to edit /etc/fstab and /boot/grub/menu.lst. If you want to boot that operating system from the MBR you would need to install that system's GRUB to MBR.
Then you'd have two identical Ubuntu Hardy Heron's, and it would be up to if you want to delete the original one or just leave it there.

Personally, I am pretty lazy and I would just leave it there. It might come in handy to have a spare operating system from time to time for various reasons and  if it's not taking up too much disc space why bother deleting it? 
I usually just leave mine there and use it for experiments and testing. Then when the next Ubuntu comes out I install  that over the top of it and  wait until I'm ready before I transfer my files into it. 

Regards, Herman :)

---

### Post by zvacet on 2008-02-24
If you want to dual boot until Hardy becomes stable install in on unallocated space and once it become stable download  [Gparted live CD](http://gparted.sourceforge.net/) and with it you can delete win partition and add free space to Ubuntu.If I didn´t understand you correctly and you want to install Ubuntu on entire disc now you have  option **use entire disc**.

---

### Post by toa on 2008-02-24
> **Recked said:**
> Hello,

I would like to install Hardy and when it becomes final remove all my Windows XP partitions etc.

Is there a way to do this and then recoup the disk space formerly used by Windows for the Hardy installation?

Thank you

My journey was, 

- installing ubuntu on an existing genuin Vista (C Drive) and (D Drive) for other, 

- partitioned the drive, took out 10GB of the vista -> ext3 to ubuntu installation
- After time i needed additional, i took another 30 GB NTFS of D drive to ->ext2 ubuntu 
- After time (finishing the Trial period) i took over the Whole (D Drive) to ubuntu
- (3 months testing)
- After Vista (C Drive) will remain for apps & games, and Vista will be virtualized within Ubuntu (as still testing)

- I wanted to show you the options you might do on your machine.

My advice, dont take the whole drive since its a new ubuntu installation, keep windows

---

### Post by zvacet on 2008-02-24
@** Herman**



> I don't know why anyone need to do that and it only makes things complicated for you. Just a simple install is best, with everything in / (root), plus a swap area.

Because that way you are saving your settings on separate home (and not settings only) and you can do upgrades and reinstall as you wish.

---

### Post by Herman on 2008-02-24
When we install a new operating system beside the old one we have a chance to try it out first to make sure it's okay. 
The new system will automatically mount the old one and we can transfer all the contents we want out of the old /home directory in minutes when we're ready.
Two operating systems are better than one.

Regards, Herman :)

---

### Post by zvacet on 2008-02-25
It is (from my point of view)unusual way of doing things,but if you like it keep doing it.

---

