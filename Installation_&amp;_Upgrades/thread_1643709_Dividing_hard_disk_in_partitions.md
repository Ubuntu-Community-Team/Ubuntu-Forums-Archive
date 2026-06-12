---
title: "Dividing hard disk in partitions"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by DDaanV on 2010-12-12
Hi people, 

I have had Kubuntu and Ubuntu installed before in Wubi, but now I want to start (or try at least) using Ubuntu as primary OS. But I still want to keep Windows on my laptop since I may need it for work/school. My Hard Disk is 320GB big, this is what I had in mind: 

- 10 GB **Samsung Restore **- Has always been on my laptop to restore Windows Vista.
- 60 GB **Windows 7 **- 60 GB might seem much, but I use Visual Studio (and Netbeans :P), that takes a lot of space.
- 40 GB **Ubuntu**
- 2    GB  **Swap Space**
- 208 GB **Shared memory **- Store documents used on Windows and Ubuntu.

Does this seem to be good? 
I have 3GB RAM, could the 2GB Swap be overkill? 
Might it be smarter to slice my shared memory into two partitions to speed up reading? 

Thanks in advance

---

### Post by sikander3786 on 2010-12-12
Welcome to the forums :-)

Remember, you can only have a maximum of 4 primary partitions. And an extended partition is a primary partition itself. So the setup would look like,

1. Primary System Restore Partition
2. Primary Windows Partition
[Extended]
3. Logical Ubuntu System Partition '/'
4. Logical Separate /home Partition
5. Logical Swap Partition
6. Logical Shared Partition.
[/Extended]

Size can be what you mentioned or you can extend that. Separate /home saves you the hassle when you decide to re-install as it will preserve all your personal docs and settings. Just mount it as /home during installation and choose *_not_* to format it.

If you decide to go for a separate /home, 20 GB would be enough for Ubuntu System Partition in my opinion. However, choice is yours.

Regarding swap, 3 GB of physical RAM is enough in most cases. Swap only comes to play when you decide to hibernate/suspend. Anyways, as you've got plenty of disk space, 2 GB swap won't hurt much.

I am not sure if splitting your data partition into 2 would be much helpful. That needs some benchmarks ;-)

And regarding Wubi, if you want to transfer that to a separate partition, it can be done.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
courtesy of forum member bcbc

---

### Post by srs5694 on 2010-12-12
I agree with sikander3786's comments, but have some additional ones:


[list]
[*]For optimum performance, place the shared data partition between the Windows and Ubuntu partitions. That is, it should be the first logical partition in the extended partition, given sikander3786's layout. Placing a shared data partition between two sets of OS installation partitions minimizes the head seek times when accessing data on that partition, which improves performance. Putting it at the end of the disk, by contrast, means that performance from Windows will suffer, since the head will have to seek over the entire Linux partition space, which takes extra time. I don't know how significant this effect will be, but as there's no cost whatsoever to placing the partitions as I suggest, you might as well do it that way, even if the benefit ends up being very small.
[*]AFAIK, there's no advantage to creating two small NTFS partitions for shared data rather than one big one. If you were using FAT, you'd get some benefits from a smaller allocation block size. This would affect the total amount of data you could store, not performance per se.
[*]When using a laptop, I strongly recommend having a swap partition that's *at least* as large as your RAM. This is because suspend-to-disk (aka hibernate) operation stores the contents of RAM in the swap space, so you won't be able to suspend to disk if your swap space is smaller than your RAM size. For safety, I'd round up -- say, to 4 GB. Even if you don't think you'll use suspend to disk, you might change your mind later, and the extra GB or two of disk space is a minor price to pay for the possibility of using this feature.
[/list]

---

### Post by DDaanV on 2010-12-12
Thanks for the replies! 

@sikander3786 I might just throw the Restore partition away, since it is only junk. That would make it possible to put everything in 4 partitions. ;)
But I also wonder why you've put /home on a separate partition. Isn't it possible to put it on the Shared or just on the same as the Ubuntu System? 

@srs5694 I hardly ever use hibernate, but 4GB it is. =A

---

### Post by sikander3786 on 2010-12-12
Even if you plan to get rid of the restore partition, I would recommend not to go for 4 primary partitions. If sometime later, you need to add a new partition for whatever reason (can be a new OS or a backup partition), you'll need to delete one of the primary partitions and then you'll be able to add extended ;-)

And extended/logical partitions are not slower than primary ones. No real benefit in having 4 primary partitions. But it might prove worthy to have an extended partition later.

And regarding /home, you can definitely put it on your '/' Ubuntu System Partition (if you don't create a separate /home during installation, it will automatically get created on the System Partition) but never on the shared data partition. It needs to be on an ext3/ext4 partition and not FAT or NTFS as they don't support Linux permission system.

> The /home directory is where all user personal files and settings live, so by having a separate /home partition, you can reinstall all the system files and still preserve your music, bookmarks, and photos. Ubuntu will see /home as just another folder living underneath /, but the home folder will really be its own disk partition that lives apart from the rest of the folders. 

Source: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

> Setting up /home on a separate partition is beneficial because your settings, files, and desktop will be maintained if you upgrade, (re)install Ubuntu or another distro. This works because /home has a sub-folder for each user's settings and files which contain all the data & settings of that user. Also, fresh installs for linux typically like to wipe whatever partition they are being installed to so either the data & settings need to be backed-up elsewhere or else avoid the fuss each time by having /home on a different partition. 

Source: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by DDaanV on 2010-12-12
Thanks for the quick reply and help again. 

I will not create a separate partition for the /home, I don't really need it since I probably just throw all my junk on the shared.

---

