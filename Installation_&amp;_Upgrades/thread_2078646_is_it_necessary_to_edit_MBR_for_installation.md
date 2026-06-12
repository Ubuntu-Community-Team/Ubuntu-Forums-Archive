---
title: "is it necessary to edit MBR for installation"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by JayIyer on 2012-10-31
I am a bit of a newbie when it comes to the installation/setup piece, so I am trying to insure against any problems. 
1) I have a partition(D:) with nothing else on it, which I am planning to install Ubuntu 12.04, from liveCD, the 64 bit version. on a windows 7 machine, so that I can dual boot.
 I have come across articles that you should use EasyBCD to edit and make the MBR point to ubuntu instead of having the ubuntu installation process do it because people have talked about horror stories (about not being able to bbot windowa, corupted boot etc).
Could someone advice me on this ?
 
Thanks a lot.

---

### Post by darkod on 2012-10-31
First, you will have to delete that D partition because ubuntu can't install on ntfs. Just use windows Disk Management and delete it, leaving the space as unallocated (unpartitioned).

Personally I prefer the grub2 bootloader, instead of going the EasyBCD route. But the choice is yours. Horror stories are all around and forums exist for people to complain and ask for help, not to post when they are happy. :) So, don't pay too much attention to it.

Of course, you need to have at least a little bit of knowledge what are you doing, otherwise any OS can turn into horror, not only linux.

The bottom line is:
Option 1. If you have one hdd, it's very simple. Delete the D partition as mentioned, and if you don't want to do any custom partitioning just use the "along side win7" option and the installer will use the unallocated space you left, install grub2 to the MBR of the disk, and in 98% of cases, it simply works.
If you happen to be in those 2%, it's not the end of the world (yet). We can probably help you to get your computer up and running fast, just keep the ubuntu cd at hand since it allows you to boot in live mode (Try Ubuntu) even if the hdd doesn't boot.

Option 2. To leave windows bootloader on the MBR and use EasyBCD, you will have to delete the D partition also, but during the installation you have to use the manual method creating the partitions manually into that unallocated space. And select the bootloader grub2 to go to the ubuntu root partition. After that in windows use EasyBCD to add ubuntu entry to the windows bootloader.

So, for option 2 you have to do manual partitioning which sometimes has the risk to really mess up the hdd, if you are not used to it. Also, even if it works OK, later during grub2 updates it can break grub2 and you will have to reinstall grub2 to the partition boot sector. This can happen because grub2 doesn't fit on the partition boot sector so it leaves part of it's code on the root partition. During an update this code can move and the grub2 part on the partition boot sector will not be able to find it until you reinstall it.

I think option 1 is much better, and easier. And you? As always, the choice is all yours.

---

### Post by JayIyer on 2012-10-31
Thank your for your response. Armed with that knowledge, I will go forth and try option 1.
One more question:(after I delete and have all that in unallocated)  lets say I want to keep a portion, say 300GB, of the 700GB on my former D: for soemthing else (another OS for e.g), would ubuntu installer allow me to to do that ?
Thanks again,

---

### Post by oldfred on 2012-10-31
With MBR you have the 4 primary partition limit. Windows only boots from a primary partition, but Linux works just fine from logical partitions in an extended partition. So convert one primary to the extended and include all the free space in that. Then you can create many logical partitions.

I often suggest a separate shared NTFS data partition so you can have the same data in both Windows & Ubuntu. Worked great for me but I do not hibernate which can cause major issues. I have in my shared NTFS data partition my Thunderbird & Firefox profiles & all photos and use Windows version of Picasa from both XP & Ubuntu. I then have many extra 25GB / (root) partitions with other installs of Ubuntu either older now or for testing something.

---

### Post by darkod on 2012-10-31
With the auto method, no. It will use the biggest unallocated space it can find, and it will use all of it.
With the manual method, because you are creating the partitions yourself, you can create the partitions with the size you want, leaving as much of the unallocated space unused as you want.

---

### Post by funicorn on 2012-10-31
For a hard drive of very large capcity ( say 1TB or larger), I always suggest installing ubuntu on lvm instead of naive msdos partition. The reason is twofold, you may need many partitions, you may need to resize them.

---

