---
title: "Delete swap partition?"
date: 2020-08-24
forum: Installation &amp; Upgrades
---

### Post by nought2 on 2020-08-24
My system has Ubuntu installed in a dual boot arrangement with Win10.
Partitions and booting are managed by BootIt UEFI, a commercial tool that permits multiple boot items.
Boot drive is 500GB NVMe.

Ubuntu 18.04 was installed with a / (root) partition and a swap partition.
Grub is installed to / (root). Everything else is in root too. I have not used a multi-partition install plan.
So far things have worked out well with this simple install plan.
Ubuntu partition is 60GB. Swap is 20GB.
16 GB of memory.

I have seen it mentioned that contemporary Ubuntu releases do not necessarily require a swap partition. The OS can use a swap file within root instead.

Would my current installation of Ubuntu 18.04 still work if I delete the swap partition?
If I do this can a swap file be created within root of the installed OS to take the place of the deleted swap partition?

I have read that swap is required for hibernation of the system. This system is a desktop workstation. It is never hibernated, only ever on or off. 

I intend to install Ubuntu 20.04 LTS alongside Ubuntu 18.04 to give it a try. If 20.04 can get along happily without a swap file I'd like to do that to see how it goes. 

I can't recall the Ubuntu installation routine well enough to be sure that I can direct the install process to use a swap file in root. Can I make it do that, or will the installer use the existing swap partition it detects if I am unable to delete it?

---

### Post by tea for one on 2020-08-24
> **nought2 said:**
> 

I have seen it mentioned that contemporary Ubuntu releases do not necessarily require a swap partition. The OS can use a swap file within root instead.

Would my current installation of Ubuntu 18.04 still work if I delete the swap partition?
If I do this can a swap file be created within root of the installed OS to take the place of the deleted swap partition?

Yes, in Ubuntu 18.04, you can delete the swap partition and create a swap file. 
Your existing 20GB swap partition is very large.
A 4GB swapfile should be plenty and it is easier to enlarge a swapfile rather than a swap partition.

Here are a couple of helpful webpages:-

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://bogdancornianu.com/change-swap-size-in-ubuntu/](https://bogdancornianu.com/change-swap-size-in-ubuntu/)

You will also have to edit your **/etc/fstab** to remove the old swap partition and add the new swapfile.

Please ensure that you have adequate backups before removing partitions.

The Ubuntu 20.04 installer will automatically create a swapfile during the install process.

---

### Post by oldfred on 2020-08-24
I have old swap partitions on some of my drives.
During install using Something Else I have to select the swap on each drive and change from swap to "Do not use". Then a swap file is created. Default swap file is 2GB.

Some with servers still suggest a 4GB swap partition.

I have not deleted swap partitions, yet as I still have some older installs and they boot with the swap partition. 
I did change one install from swap partition to swap file, but multiple commands required.

---

### Post by Impavidus on 2020-08-24
One advantage of a swap partition is that it can easily be shared between two (or more) Linux systems dual booting, as long as you don't hibernate.

---

### Post by ashoknaidu007 on 2020-08-24
Why dont you try swap memory inplace delete option 

Refer [https://tequality.tech/swap-memory-in-windows-and-linux](https://tequality.tech/swap-memory-in-windows-and-linux)

---

### Post by nought2 on 2020-08-24
> **tea for one said:**
> Your existing 20GB swap partition is very large.
A 4GB swapfile should be plenty and it is easier to enlarge a swapfile rather than a swap partition.

Here are a couple of helpful webpages:-

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://bogdancornianu.com/change-swap-size-in-ubuntu/](https://bogdancornianu.com/change-swap-size-in-ubuntu/)

Thank you for these links. Their detail in commands provided was precisely what I needed.

Wish I had seen the table of swap file sizes before installation.
When making the new swap file I made it 6GB in case I add more physical memory.
> **oldfred said:**
> During install using Something Else I have to select the swap on each drive and change from swap to "Do not use". Then a swap file is created. Default swap file is 2GB.
Thank you. I'll look out for this in the install routine for 20.04 Focal.

> **Impavidus said:**
> One advantage of a swap partition is that it can easily be shared between two (or more) Linux systems dual booting, as long as you don't hibernate.Yes, I considered that. But now that I know swap file/partition needed for machine with 16GB RAM is only 4GB if not hibernating it makes managing my boot partitions easier to use swap file rather than partition.

Notwithstanding all the preparatory reading I had done I made a small omission when creating the new swap file.
Before starting I did not do:
$ sudo swapoff -a

This meant for a time I had two swap listings: the existing swap partition and the new swap file.

As far as I can tell this only caused a small wrinkle in the results.

Here are outputs of verification commands:
```


$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/mnt/6GiB.swap                          file		6291452	0	-2

$ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        1.6G         12G        253M        1.3G         13G
Swap:          6.0G          0B        6.0G

$ grep SwapTotal /proc/meminfo
SwapTotal:       6291452 kB

New line in /etc/fstab:
/mnt/6GiB.swap   swap   swap   defaults     0   0
# line for old swap partition commented out 
```The wrinkle is that cat /proc/swaps shows priority is -2. 
I ironed it out like this:
```
$ sudo swapoff /mnt/6GiB.swap; sudo swapon -p 0 /mnt/6GiB.swap
$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/mnt/6GiB.swap                          file		6291452	0	0
```
In boot manager I changed settings of boot item for 18.04 to hide the now hopefully obsolete swap file. OS booted normally.

I presume it is safe to delete swap partition now?

---

### Post by tea for one on 2020-08-25
> **nought2 said:**
> I presume it is safe to delete swap partition now?

Yes, it all looks OK to me.

After you have deleted the swap partition, I would leave the free space unallocated for a few days, just in case something unexpected occurs and you need to retrace your steps.

If everything is OK, can you mark the thread as solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by nought2 on 2020-08-25
Thank you for your help, tea for one. 
Much appreciated.

---

