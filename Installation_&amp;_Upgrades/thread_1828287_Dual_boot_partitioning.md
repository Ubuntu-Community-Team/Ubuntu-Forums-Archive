---
title: "Dual boot partitioning"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by halozander on 2011-08-18
Hey whats up everyone,  I am about to get a new laptop here soon and I was planning a dual boot like I have on my current laptop (Win7 and Ubuntu), but I have something special in mind. I looked around the forum to see if there was anything like what I had or if it was even possible but I didn't see anything quite like this.
[IMG]http://i268.photobucket.com/albums/jj29/halozander/My%20artwork/PartitionStrategy.jpg[/IMG]

I was wondering if this was even possible, and if so, would anyone be able to tell me what filesystem I should use for my windows swap partition?

Thanks for your help ahead of time!

Alex

---

### Post by Basher101 on 2011-08-18
windows and swap partition? windows does not have a swap partition, nor does it use swap functionalities. But otherwise it is possible. But why make the shared so small? it does not make sense. It would be alot more beneficial if you made the OS partitions smaller (50GB or so should be enough), some space for your home, a big shared partition and the linux swap at the end of the disk. For filesystems use NTFS for windows and the shared partition and ext4 for ubuntu and swap for well...swap^^ This way your OS wont get cramped much, espacially windows. Install your programs onto the shared partition if possible. This way, when you make whole system backups of windows you will save alot of space and time restoring it.

---

### Post by YesWeCan on 2011-08-18
Hi Alex. Welcome to the Ubuntu forums. :)

That's a very nice diagram. I like the symmetry of it. I haven't seen any partitioning scheme like that. It looks interesting.

One thing I have never seen is a Windows swap partition. Windows normally uses what is called a "page file" or virtual memory file for this purpose and it normally exists inside the C: partition, although it doesn't have to. Linux still uses the old-fashioned swap partition by default. So you are thinking "outside the box" here. Have a look at this article for more information: [http://technet.microsoft.com/en-us/magazine/ff382717.aspx](http://technet.microsoft.com/en-us/magazine/ff382717.aspx)

---

### Post by halozander on 2011-08-18
Thanks for the advice guys! However, windows does use a swap file like you said, and I have read that if you create a partition solely for that file it optimizes memory usage because if it is on its own partition there are several advantages: windows knows exactly where it is if it needs it, it doesn't get fragmented, and it is not constantly changing size like it would be otherwise. What I couldn't figure out however was what type of filesystem should be used. I am assuming that it should be NTFS, but I'm unsure.


Oh and basher, I like the idea of using NTFS for the shared partition and installing programs on it, I kinda forgot that Linux could read/write to NTFS, thanks!

---

### Post by oldfred on 2011-08-19
I also agree that you should use NTFS for the shared data partition with windows and Linux. If you do want to read data from your C: drive, set it to read only so you do not accidentally damage it.

Your / (root) only needs to be 10-20GB. I use 25GB since I have room and have several / partitions. If you are storing most of your data into the NTFS shared partition, you may not need a separate /home, otherwise I make /home larger than / since you data may grow a lot. The acutal user settings are small, mine are about 1GB and most of that is .wine for Picasa. I have moved all my other data folders (some hidden) into my shared or another ext3 data partition. I like having Firefox & Thunderbird profiles in the NTFS partition so I can have the same email & bootmarks in both systems.

---

### Post by _nedR on 2011-08-19
1. I don't think having a separate partition for pagefile in Windows has  any real benefits. Can you  provide a link? I also do not understand  your rationale for using a separate partition for swap on windows:

- You can tell Windows to keep the page file size fixed at 8gb (instead of system managed)
- Doing the above prevents the page file from getting fragmented
- At any time you can change the size of the page file. This is not easy with a swap partition.
-  Having swap/page on a separate partition has no performance advantages  that I know of (unless you put the partition on a second hard-disk)

One  disadvantage regarding page-files that i can think of is that most  defragmenters on Windows can't/won't move it during defragmenting.


2.  I agree with the above comments that it might be a better idea to  increase the size of your Shared and Home partitions and decrease the  size of your Windows and Ubuntu partitions for the following reasons :

-You'll generally have more data than programs so it is more logical to allocate more space for data
- Keeping your data on a separate partition increases the probability that** if something goes wrong with your windows (this has happened to me) or linux partition ****you won't lose all your precious data.**

3.  A 300G root partition? I am a linux noob myself but I was under the  impression that the root partition was primarily for operating system  and installed applications. Are you going to install that many  applications?

An alternate configuration like Basher101 suggested could be :

| 50-100GB Windows| 200+ GB Media |25-50GB Shared(ntfs) |200GB /home | 50-75GB Ubuntu |8GB Swap linux|

4.  I am quite wary of Ubuntu's ntfs write support actually, since i have  had a  few weird errors creep up, although none of them were serious or fatal.  (This could be my imagination though and maybe there is nothing wrong  with Ubuntu's NTFS support.) That's why i included the Shared partition  above( which can still be NTFS but  seperate from the Media partition so as to not corrupt it accidentally.)  I use an NTFS partition as my media partition without much trouble. 

5.  As suggested by oldfred, you could keep your Windows and Media  partitions as read-only on Ubuntu for additional isolation and security.  
 
Of course, The above is based on my needs. Your needs will probably be different.

---

### Post by Mark Phelps on 2011-08-21
Unless you are planning on keeping a LOT of data inside Win7, I would recommend that you keep the OS partition to 50GB -- and add the remaining amount to your shared NTFS partition.  Ans while that 50GB is more than you will need, it gives you some slack space so you don't have to worry about Win7 growing over time and running out of space.

---

