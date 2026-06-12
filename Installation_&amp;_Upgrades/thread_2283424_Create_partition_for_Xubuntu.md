---
title: "Create partition for Xubuntu?"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by Digitalscribbler on 2015-06-21
Hi-
I currently have a dual boot setup on my netbook (Ubuntu 14.04 LTS & Windows 7). I'd like to install Xubuntu and after doing some research, it looks like I can put install Xubuntu by using Gparted and then using some of the unallocated space for Xubuntu. Is this correct? And if that's correct do I just select create a New partition from the drop-down menu in Gparted (i.e., Partition>New) and then allocate the space for it/Xubuntu? I think the Xubuntu installation screen recommends allocating at least 5-6 GB of space. (Apologies if this is too basic of a question. I wasn't sure if I should post this here or the New to Ubuntu forum). Thanks!

Ediit: Here's a screenshot of my current gparted setup [http://postimg.org/image/u0zjaaqsd/](http://postimg.org/image/u0zjaaqsd/)

Other specs:
Memory 3.6GiB
OS type 64-bit
Disk 214.1 GB

---

### Post by Bashing-om on 2015-06-21
Digitalscribblerl Wellll ..

There are as many solutions as there are system operaters .
All depends on what your future plans might be.
Consider : as the present partitioning is the legacy MBR there is a 4 primary partition limit ( the extended partition is one of those 4 primaries - and in the extended are the logical partitions sda4,5,6 ) such that only windows can utilize the  present 190.33 unallocated space.

Now consider that you want to install xubuntu: This install must also be installed within the extended partition. The easier thing to do is to shrink the sda5 partition. The suggested minimum disk space for a usable install is 30 Gigs. So shrink sda5 by X amount giving you the unallocated space. In the installer point the installation to this new unallocated space and allow the installer to do it's thing.

Partitioning is always risky business, strongly urged to backup any and all important info before proceeding.

Just a thought of what I would do
[INDENT][INDENT][INDENT]'till I do know what to do better
[/INDENT][/INDENT][/INDENT]

---

### Post by Digitalscribbler on 2015-06-21
Thanks for the feedback. Basically what I'm looking to do is just play/experiment with Xubuntu and see what it's like. I guess I could try it via the Live version (without installing it), but I'm also kind of interested in learning more about partitioning. 

At any rate, I'll try doing it via the "extended partition" option. I'll also be sure to back up my files before attempting this and will report back on how it goes. Thanks for your help!

---

### Post by oldfred on 2015-06-22
You can also expand your extended partition into the unallocated and then you can add partitions in the extended.
You may have made Windows NTFS partition too small. NTFS really likes 30% free. At 10% you may have difficulty running a defrag as it has no working room and system will be slow.

If having multiple installs, I prefer smaller system partitions and larger data partitions that I can use in every install, so I have same data no matter what I boot. You may want to make Windows a bit larger, but then create a NTFS shared data partition in the unallocated. But you have to expand extended left and in effect move unallocated into extended to add more partitions, first.

---

