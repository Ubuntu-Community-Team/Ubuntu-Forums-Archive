---
title: "Ubuntu installation (LVM+LUKS-encrypted) on SSD and HDD"
date: 2019-08-05
forum: Installation &amp; Upgrades
---

### Post by tellapu on 2019-08-05
I will be doing a new installation of 19.04 on brand new disks. I have an SSD (128GB) and HDD. Both should be fully **encrypted** (LVM/LUKS) and accessible after entering a single passphrase on bootup. 


The **SSD** will hold these partitions:
/boot (probably unencrypted)
/ (root) (Ubuntu 60GB)
- and all the usual directories in the Linux file system
/home (47GB)
Free Space (20GB) - is this needed to keep the SSD healthy?


The **HDD** will have
/var
/swap
Part of Home: pictures, audio, video, .deb files, zipped files, backups, etc.

How is this best accomplished?
Some instructions help but don't fully cover all wishes (e.g. var & swap and only part of home on HDD) and not sure whether there is a better way to configure it:
[http://nyeggen.com/post/2014-04-05-full-disk-encryption-with-btrfs-and-multiple-drives-in-ubuntu/](http://nyeggen.com/post/2014-04-05-full-disk-encryption-with-btrfs-and-multiple-drives-in-ubuntu/)
[https://askubuntu.com/a/1035703/30631](https://askubuntu.com/a/1035703/30631)
Thanks in advance

---

### Post by TheFu on 2019-08-06
If you are going through all this effort, it would be wiser to use an LTS release, not one that has only 4 months of support remaining, like 19.04 does. That will increase the chance of multiple years of hassle-free use.

I'd use symbolic links from $HOME to the other storage. Don't directly mount it under the HOME directory.

Probably make the / partition 25G, which is extremely generous for what is needed, more than 10G higher than I've ever needed with a separate /home storage allocation.

I run an encrypted laptop, but only with 1 storage device.  On prior laptops, I wanted a small area of normal storage that wasn't encrypted. Unrolling the different storage to be able to shrink the partition was a huge hassle and full of non-exact guess work on the sizes of the partition, encrypted area, LVM PV, VG, LVs ... Took me a few attempts to get the numbers correct enough. LVM doesn't know about LUKS boundaries and LUKS doesn't have a clue about LVM.

Definitely use LVM so you only have to deal with 1 encrypted partition per physical disk.

---

### Post by tellapu on 2019-08-07
@TheFu Thank you very much for your helpful comments!
If anybody else would like to comment, too, I am grateful for all tips before I endeavour into this new territory.

Do you think it is a reasonable way to do the "basic" steps:
[https://askubuntu.com/a/1035703/30631](https://askubuntu.com/a/1035703/30631)

I found another approach which looks more complicated to me, though:
[https://lucaswerkmeister.de/posts/2018/05/12/luks-on-lvm/](https://lucaswerkmeister.de/posts/2018/05/12/luks-on-lvm/)

**Adapted** **configuration: SSD** (128GB) will hold these partitions:
/boot (probably unencrypted)
/ (root) (Ubuntu 25GB)
Symlink to some parts of /home (up to 78GB)
Free Space (25GB) - is this needed to keep the SSD healthy?

The **HDD** will have
/var
swap
/Home

How could I "move" /var and swap to the HDD after the installation to the SSD?

---

### Post by tellapu on 2019-08-10
Is there anybody to help?
Especially for moving/installing swap on the LVM + encrypted HDD while / (root) is still on the SSD.
Thanks!

---

### Post by tellapu on 2019-08-11
I hope to do a new installation of Ubuntu 19.04 on new disks. I have an SSD (128GB) and HDD. Both should be fully **encrypted** (LVM/LUKS) and accessible after entering a single passphrase on bootup.
Probably I will install the system with the usual installation CD (as there seems to be no alternate CD for Ubuntu 19.04 except for Lubuntu) on the SSD. But I would like to move the swap partition to the HDD which should then also be LVM/LUKS-encrypted (to save writing to the SSD).
I tried to find instructions in the forum and wider internet but could not find enough information so I dare to do it. I would really appreciate any guidance (best if it is step-by-step as I am not familiar with this at all).
Thanks in advance!

---

### Post by oldfred on 2019-08-11
Do not know LVM.

A lot of users see old info on SSDs. They now are just as reliable (unreliable?) as HDDs.
So writes are not really an issue. But I do change SSD partitions to use noatime parameter.

But if you have 4GB or more of RAM, are you even using swap? And if you are, you may want to change swap setting swapiness, to reduce use of it. 
Only if editing movies or very large photos may you need more RAM and then probably should buy more RAM as even swap on SSD is slow compared to RAM.

```
fred@bionic-z97:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           7.7G        1.3G        1.9G         76M        4.5G        6.1G
Swap:          2.0G          0B        2.0G

```

---

### Post by oldfred on 2019-08-11
Merged threads. Please do not create duplicate threads on same topic.

---

### Post by tellapu on 2019-08-11
@oldfred Thanks a lot for chipping in and merging the threads! Sorry, about the extra trouble I caused, I was desperate to get an answer and the second thread was focusing just on one question of the more general wider configuration query of this first thread. But I am fine that you merged this.

> **oldfred said:**
> Do not know LVM.

A lot of users see old info on SSDs. [B]They now are just as reliable (unreliable?) as HDDs.
So writes are not really an issue.[/B] But I do change SSD partitions to use noatime parameter.



This would be really good news and would save me a lot of headache (e.g. not move swap and var to the HDD.)
Thanks for the tip regarding **noatime**. I have to see how this works with LVM/LUKS. 
I read that **relatime** might be as good. And some say backup might be difficult with noatime. **What do you think?**

> **oldfred said:**
> 

But if you have 4GB or more of RAM, are you even using swap? And if you are, you may want to change swap setting swapiness, to reduce use of it. 
Only if editing movies or very large photos may you need more RAM and then probably should buy more RAM as even swap on SSD is slow compared to RAM.

```
fred@bionic-z97:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:           7.7G        1.3G        1.9G         76M        4.5G        6.1G
Swap:          2.0G          0B        2.0G

```

I am open to have **no swap partition **especially as it might increase the wear on the SSD. As far as I know a swap partition is installed with the usual Ubuntu installation process (LVM/LUKS) and it may be more trouble to delete this partition than just to leave it. With 128 GB I have plenty of space on the SSD. And some still recommend to have swap (even with 8GB RAM): [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

**Thanks again and I am looking forward to your further comments!**

---

### Post by oldfred on 2019-08-12
Again, I do not really know LVM nor use it.
But have seen that it still creates a swap partition inside the LVM.
Standard installs now all use a swap file, but will use a swap partition if found.

My main working install 18.04 had swap partition as my SSD has 14.04 (now obsolete & will become 20.04), 16.04 and 18.04 on it with all my data on sdb HDD. I was able to manually convert to swap file, but a lot of commands. My test installs of 19.10, I was able to just choose not to use swap partition during install and it defaulted to swap file. I do not think you can do that with LVM.

If never using swap, then there is no issue of wear on swap. Even if only occasionally using it, then its use would be less than rest of drive. My old laptop with 1.5GB of RAM and lightweight desktop would use swap if I loaded more than one larger app and several smaller apps. Never opened more than a very few tabs in Firefox. But occasionally did something & screen would go gray for a second or two and I knew it was swapping. Old system had slow 5400 rpm drive also, so swap use was very obvious. If you are one to open 100s of tabs in browser or edit video then you may need the swap.

       [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

---

### Post by TheFu on 2019-08-12
All Linux desktops need some swap.  There are issues when memory becomes constrained where bad things happen. Having some swap provides the end-user with feedback that things are getting slower before the system locks up or the GUI locks up.  

Servers are different, assuming the amount of RAM is tuned to the workload. Most of my servers don't have any swap. A few have some to handle more transactions for a few hours a month than they normally experience.

For desktops, my answer for how much swap is really simple.  Regardless of the amount of RAM, 4.1g of swap.  I don't care if the desktop/laptop has 1G, 2G, 4G, 6G, 8G, 16G, 32G or more of RAM.  It is more important on 16G and smaller RAM systems.  Humans need that slowdown to as a way to know that RAM is becoming constrained.  Swap provides that feedback.  The Linux kernel guys have been discussing issues about not having any swap the last year or so and all the issues it can cause.  Their recommendation, as I read it is, always have some swap.

As for LVM or swap file or swap partition.  I'd prefer an LVM LV for swap, then a swapfile, and lastly a swap partition.  Modifying the size of a swap file or a swap LV is pretty trivial and can be performed on a running system. Modifying a swap partition requires a reboot, using external boot media. It is ugly.  LVM provides the separation of partitioning, but the convenience of file management among many other capabilities that only admins would likely use. Like being able to move a PV to another disk might be handy.

---

### Post by tellapu on 2019-09-10
@oldfred and @TheFu Sorry for the late response, I hoped to be quicker and give more feedback. I eventually found a solution and will post it for reference. Thank you both very much for your valuable responses!

---

