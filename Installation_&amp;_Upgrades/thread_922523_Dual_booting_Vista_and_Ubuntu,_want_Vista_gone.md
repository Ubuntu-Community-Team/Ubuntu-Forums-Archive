---
title: "Dual booting Vista and Ubuntu, want Vista gone"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by revchris on 2008-09-17
I'm dual booting Vista and Ubuntu at work and want to install Vista in VirtualBox instead.  How can I remove the partition that has Vista installed on it and add that partition to Ubuntu?

Thanks.

---

### Post by Herman on 2008-09-17
Of course you would obtain the owner's permission first if you aren't the owner of the computer.

I would begin by making a complete backup of all my information in both operating systems.
Then I would double check and triple check that I have definitely copied all that data successfully to the backup(s) before doing anything.

You could simply delete Vista with a partition editor like Gnome Partition Editor, or GParted LiveCD. Thehn you would have a large area of free space in the beginning of your hard disk that you will probably want to use for something.

The problem is, it is not fast or easy to move or resize a Linux partition from it's start point. It's easy to resize it from the other end, but not from the start, so you can't just add that partition to Ubuntu easily.
Actually, you can move the start point of your Ubuntu partition with Gnome Partition Editor or GParted, but it's a slow process and takes a long time. If you decide to try that it's best to let it run overnight or do it on a day off or something, and go do something else while it's running.
It would actually be faster to re-install Ubuntu to the beginning of your hard disk. If you are good at backing up and re-installing you can probably do that in an hour or so.

Another way would be to make a whole partition backup of your Ubuntu partition with Partimage, and restore it to the first partition in your hard disk.
You would need to edit GRUB's /boot/grub/menu.lst with the new partition number and maybe re-install GRUB to get it to boot okay. For the first time you would need to boot it with Super Grub Disk or some other GRUB, like GRUB from a floppy disk or your own GRUB CD.

What I normally do myself is install a newer version of Ubuntu in one half of a hard disk instead, so if I had Gutsy Gibbon, I would install Hardy Heron in the other partition.  
Then when I feel like it, after moving my files from Gutsy into Hardy, I would delete Gutsy Gibbon and install the next version of Ubuntu, Intredpid Ibex, in the Gutsy partition. I wouldn't move any files into it yet or use it for my main operating system until it is officially released and then I'd wait a bit longer still.
Two Ubuntus are better than one.

If you decided to do things that way, you'll already have Intrepid Ibex before it is officially released, and later if you only want one Ubuntu, you could just delete Hardy Heron and resize Intrepid to fill the free space. Linux partitions are easy to resize from that end. Or, wait and install the next version of Ubuntu there, whatever that will be called.
The main problems with trying out new versions of Ubuntu before they are released is they can be expected to be a little buggy, and so they get a lot of updates and use some extra bandwidth from your internet account. It helps the developers to get the bugs out of the new version before it is released if we test it in our hardware while they're working on it. Most ordinary users are still better off sticking with Hardy Heron though, at this point in time.

Regards, Herman

---

### Post by ee19921 on 2008-09-17
> **Herman said:**
> 
You could simply delete Vista with a partition editor like Gnome Partition Editor, or GParted LiveCD. Thehn you would have a large area of free space in the beginning of your hard disk that you will probably want to use for something.

The problem is, it is not fast or easy to move or resize a Linux partition from it's start point. It's easy to resize it from the other end, but not from the start, so you can't just add that partition to Ubuntu easily.
Actually, you can move the start point of your Ubuntu partition with Gnome Partition Editor or GParted, but it's a slow process and takes a long time. If you decide to try that it's best to let it run overnight or do it on a day off or something, and go do something else while it's running.
It would actually be faster to re-install Ubuntu to the beginning of your hard disk. If you are good at backing up and re-installing you can probably do that in an hour or so.

Another way would be to make a whole partition backup of your Ubuntu partition with Partimage, and restore it to the first partition in your hard disk.
You would need to edit GRUB's /boot/grub/menu.lst with the new partition number and maybe re-install GRUB to get it to boot okay. For the first time you would need to boot it with Super Grub Disk or some other GRUB, like GRUB from a floppy disk or your own GRUB CD.



Herman, I have a similar question. What would you suggest for [this]("http://ubuntuforums.org/showthread.php?t=922480")?

---

