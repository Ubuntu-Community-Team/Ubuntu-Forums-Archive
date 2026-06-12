---
title: "Installation error: Not enough space (Dual boot with Windows 7/UEFI)"
date: 2015-12-28
forum: Installation &amp; Upgrades
---

### Post by cij on 2015-12-28
Hello.

I was trying to install Ubuntu 14.04.3, to dual boot with Windows 7 on UEFI mode, but couldn't because it stopped in the middle of the process, saying there was not enough space.

I have a SSD with 100GB allocated for Windows, and left the rest of the space (11.79 GB) unallocated, so that I could install Ubuntu on it.

In the beginning of the installation, it says I needed at least 6.6 GB of free space to install it, so I don't know what happened.


Could someone help me here, please?

By the way, not sure if it helps, but I managed to choose my location, keyboard, login/password details, the problem happened after this, when it was showing some features while I had to wait for the installation, and then it stopped in the middle of it. I booted into Windows to check the space, and through the disk management, I could verify that Ubuntu had installed 2 partitions, one with 3.91 GB (probably the "/" root?), and another with 7.88 GB (swap?), which ended up using all the 11.79 GB of unallocated space I had left for it.

I've heard that swap partition depends on my RAM size (which is 8 GB), so maybe it has something to do with it?

---

### Post by yancek on 2015-12-28
12GB isn't much for a curretn Ubuntu system and if you have a 3.91GB partition for Ubuntu, that will never work.  You might just try it from the DVD or flash drive first to see if you like it.  The amount of swap you need varies, 2-4GB is usually enough for an average user but it depends upon what you will be using the computer to do.

---

### Post by cij on 2015-12-28
I researched a little about dual booting, and some people said 10 GB would be enough for Ubuntu 14.04, and the installation itself said it would be only 6.6 GB or so, that's why I thought something was wrong, as it was trying to install much more stuff than that.

Then, what is the minimum space required for Ubuntu 14.04.3? I'll try to shrink Windows partition as there's some space left there.

Now that I think about it, if I use the manual partitioning, can I actually choose a smaller partition size for Ubuntu? I'm planning to do only web surfing with Ubuntu, at least for now, and nothing else, so I wanted it to be as small as possible.

Edit: By the way, I also forgot to mention that my drive is GPT, and not MBR, not sure if that makes any difference.

---

### Post by oldfred on 2015-12-28
The default install makes swap large enough to hibernate. So you must have 8GB of RAM.
But hibernation not really recommended with dual booting and with an SSD hibernation will not save much if anything in boot time. So just to have some swap about 2GB is all you need. But then you need to manually partition and use Something Else.

I normally suggest 25GB for / (root) and use about 11 to 13GB with all my data in other data partitions. You can use 10GB, but would have to regularly houseclean and not download much of anything into Ubuntu's /home folders.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]15-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

More details on UEFI install in link in my signature.

---

### Post by cij on 2015-12-28
Thanks a lot, oldfred, those links were all very helpful.

I managed to squeeze Ubuntu 14.04.3 into the 11 GB partition on the SSD, through manual partitioning during installation, with 4GB for swap and the rest (8GB) for root partition.
Looking very nice, I used a little for a couple hours now and am already loving it!

Once again, thanks oldfred, and yancek too, for taking your time to help me!

Regards,
cij.

---

