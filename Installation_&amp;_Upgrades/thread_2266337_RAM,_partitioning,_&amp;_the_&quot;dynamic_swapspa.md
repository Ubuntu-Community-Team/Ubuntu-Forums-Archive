---
title: "RAM, partitioning, &amp; the &quot;dynamic swapspace manager&quot; program"
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2015-02-22
I've seen lately that the old rule of needing a swap partition that's double the amount of your RAM is today a more-or-less obsolete rule -- that it was true mainly in the days when folks had far less RAM than they do today.  

I wonder how true people here would say this is?

I've also been told that you really only need one swap partition (or swap file, if that's how you roll) for all of your Ubuntu systems, whereas I -- not knowing a whole lot about these things -- had assumed that each drive you had an OS on would necessarily need its own swap partition.

So I have a question or two about all this, based mainly on seeing a post by forum member oldfred (which post I can't seem to find now) wherein he discussed the benefits of having one large ext4 partition on a drive, holding everything, and a small swap partition at the end of the drive.  Also mentioned in that post was a program called "swapspace" -- a "dynamic swapspace manager" -- and that supposedly if you used this program, all you needed was either a very small swap partition or no swap partition at all.

So, for example, my personal setup is that I have a desktop unit with **8GB of ram**.  I never use the hibernate feature, and I have[COLOR=#0000ff] **three**[/COLOR] ***one-terabye*** SATA II drives: 

[COLOR=#0000ff]***Drive A ***[/COLOR]has **Ubuntu-MATE 14.04.1** (Trusty Tahr) installed on one big **912GB ext4 partition **(with the boot flag active on this partition only), and **a 21GB swapspace partition** at the end of the drive.
[I][B]
[COLOR=#0000ff]Drive B[/COLOR][/B][/I] has **Ubuntu 12.04.5** (Precise Pangolin) installed on a similarly large **912GB ext4 partition** with a **20GB swapspace partition** at the end of this drive as well.

[COLOR=#0000ff]***Drive C ***[/COLOR]has no OS on it and will be used for storage of music, pictures and other data.  It consists of a single 932GB ext4 partition, no swapspace partition.

I am also running the ***Swapspace*** "dynamic swap space manager" program,* version 1.10-4ubuntu3 *on both Trusty and Precise.

My main question is: _***What would be the optimal swapspace configuration for this particular setup?***_  

Would it be prudent to get rid of one of the swap partitions and reduce the remaining one? By how much?  

If one were to have only one swap partition with 3 drives, would it matter which drive it's on, in terms of affecting speed and performance?

What about the occasional situation where you've got Google Earth and 2  or 3 other super-hog programs open? Though it might not happen often, my entire 8GB of ram ***could*** get filled up on that  rare occasion, could it not?  In which case I'd be glad I have, say, 9 or 10GB of ram, no?   

Or maybe that's overkill. 

Is it true that one can safely and beneficially do away with all swap partitioning by installing the swapspace program?   Is it wise to have both a small swap partition _***and***_ use the swapspace program? How do the two interact with each other? Does one make the other irrelevant?

My understanding is that swapping is to be avoided whenever possible. But for those times when it's necessary, and taking into account that everyone has different needs and may handle these issues differently, what might be a good, realistic ram and ram-partitioning configuration for the above drive setup?  

Thankyou to anyone who chooses to answer.

---

### Post by MAFoElffen on 2015-02-22
My out- I have never used a dynamic swap space program, so know nothing about them. What I say will be from my experience and my opinion...

Swap is appropriate for laptops, notebooks and tablets. These are devices were you will hibernate or go to sleep. In those states, it wll write what was in memory to disk in that partition. If you close the lid on a laptop or notebook, it puts it into one of those states... So swap is not otpional on one of those.

Swap is optional in a Desktop system where you might have many app's open. You *may* never go into a hibernate or sleep state, as that would be just by user choice. So if you do not go into those states, most modern desktop have enough memory for it to be debatable to have much virtual disk (swap).

Most server admins do not put much value on swap. How do I know? I've asked simular questions about swap here. (anyone of you can agree or disagree, but that's what their posts were.) If you have the RAM that app's are not going to go to swap paging... then why dedicate 2 times waht RAM you have to swap.You don't put a server into a sleep nor hibernation state. My main server is 96 GB of RAM. 2 times that RAM for swap would be inappropriate distributoion of it's resources. And if you dedicate too much swap on a server, it sometimes has paging problems keeping track of an oversized paging space. (<-- Performance wise, noted by some users) 

For servers, I now tend to initially under-allocate my swap as 1.5 to 2GB's. I run scripts as jobs to track my paging, so I can have an indication if I need to worry or adjust what I do have set to something higher.

---

### Post by kerry_s on 2015-02-22
8gb ram = you don't need swap

the only thing i would do is cut the terabyte drives in half(2x500gb), or more smaller partitions(4x250gb).

---

### Post by tokyobadger on 2015-02-22
the "1.5 - 2.0x your RAM" comes from a time when PCs used to have much less than today - 48M RAM in a Sharp Mebius laptop, 128M in a Gateway PII-400 desktop, etc

Linux on laptops today does seem to need a large swap partition (or swap file) in order to support suspend/hibernate functionality and I don't currently run linux on a laptop so I cannot comment with accuracy; linux on desktops I can comment on - after passing 2G of RAM (many years ago) I tried switching off swap (swapoff) with no negative results. Consequently newer desktop builds with higher amounts of RAM were installed without swap.

As for shared swap, you can indeed run *bsd, solaris, linux on one PC sharing the same swap partition - did it for several years, no issues; not been doing it for about 7 years though so if recent requirements have changed then I'm out of date

---

### Post by oldfred on 2015-02-22
As above the old rule was because RAM was expensive and system had very little RAM. And you do not want to use swap as it is orders of magnitude slower than RAM. 

I normally suggest some swap like 2GB, just to have some. And I normally put a swap partition on every rotating drive but not on SSDs. But new installs find all the swaps and add them, so I go back in and remove all but one

If you hibernate which is not really suggested, then you cannot share swap. As it has the other systems hibernation in it. But if not hibernating nor have encryption you can share one swap partition.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)

---

### Post by watchpocket on 2015-02-22
> **oldfred said:**
>  . . . And I normally put a swap partition on every rotating drive but not on SSDs. 

Speaking of every rotating drive, I just noticed that my [COLOR=#0000ff]**sda1**[/COLOR] drive/partition _***has the same ID #***_ as my [COLOR=#0000ff]**sdc1**[/COLOR] drive. (Scroll to the bottom in the code box below.)

***Should this raise any red flags?***  Or no?

```

--> sudo fdisk -l 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3aec6e77

   Device Boot      Start         End      Blocks   Id  System
[COLOR=#0000ff]**/dev/sda1   *        2048  1911582719   955790336**[/COLOR]   [COLOR=#ff0000]**83**[/COLOR]  [COLOR=#0000ff]**Linux**[/COLOR]
/dev/sda2      1911582720  1953523711    20970496   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b03b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1911377919   955687936   83  Linux
/dev/sdb2      1911377920  1953523711    21072896   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41031e20

   Device Boot      Start         End      Blocks   Id  System
[B][COLOR=#0000ff]/dev/sdc1            2048  1953523711   976760832[/COLOR]   [COLOR=#ff0000]83[/COLOR]  [COLOR=#0000ff]Linux
[/COLOR][/B]
```[COLOR=#0000ff]
[/COLOR][COLOR=#000000]Thanks.[/COLOR][COLOR=#0000ff]
[/COLOR]

---

### Post by deadflowr on 2015-02-22
> ***Should this raise any red flags?***  Or no?
No, the id means what kind of partition you have, 83 means native linux partition.
Totally normal.
Here's a quick list of IDs
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

---

### Post by watchpocket on 2015-02-22
That's a great relief, and thanks for the link.  I'll now go educate myself about IDs.

---

### Post by grahammechanical on 2015-02-22
Suspend = suspend to RAM. Hibernate = suspend to disk. Guess which on uses swap. 

When we have multiple installs of Ubuntu and use use the Something Else option to put Ubuntu into a partition, then the installer will automatically use the existing swap partition. So, even with multiple installations we only need one swap partition.  I have never tried directing the installer to use the swap partition on another disk but it should work.

And then there is zRAM

[http://en.wikipedia.org/wiki/Zram](http://en.wikipedia.org/wiki/Zram)

I have this installed on my system but I cannot tell if it is improving things.

---

### Post by watchpocket on 2015-02-22
> **grahammechanical said:**
>  So, even with multiple installations we only need one swap partition.  I have never tried directing the installer to use the swap partition on another disk but it should work.

Quoting oldfred, above: *"And I normally put a swap partition on every rotating drive but not on SSDs."*

I'm guessing he has his reasons for that -- in fact I'd be curious to know what they are.

> And then there is zRAM
[http://en.wikipedia.org/wiki/Zram](http://en.wikipedia.org/wiki/Zram) 

Looks like it's more for laptops and embeded systems than desktops, though I guess it could still be useful on a desktop workstation that might have a bit more RAM.  I'd be interested to know if and when you're able to tell if it's helping.

---

### Post by tgalati4 on 2015-02-22
Multiple OS's can share one swap partition, but you can get into use cases where this will fail:  You suspend-to-disk in MATE 14.04, but then decide you want to boot into 12.04.  Your swap will get overwritten and then resume to MATE will fail--losing work-in-progress.  You normally can't share swap between 32-bit and 64-bit, nor between Fedora/SUSE and Ubuntu (Big Endien vs Small Endian), nor encrypted vs non-encrypted.  So it makes sense to keep swap separate between OS's.  You only really need swap just larger than RAM size to allow for hibernate (RAM-snapshot-to-disk).  Otherwise, make swap whatever size you feel comfortable above RAM size.

---

### Post by watchpocket on 2015-02-22
Earilier today I re-sized the swap partitions on both my drives from 20GB to 10GB.  I may not even need that much.  But although I don't generally use hibernate, with 8GB of ram and 10GB of swap partition per disk, if I ever need or want to hibernate (or even if I do it accidentally), I can. 

 I also changed swappiness from 60 to 20 (couldn't bring myself to go to 10, at least just not yet) and vfs cache pressure from 100 to 50, and I'm already seeing a very noticeable speedup in the system.

---

### Post by efflandt on 2015-02-24
I have never had any swap on my 8 GB desktop. The only time you would need that is if you use tmpfs for /tmp (primarily if using SSD) and trying to rip DVD's or BluRay (which uses lots of /tmp). Even after running Steam games I do not really use it all:```
efflandt@XPS-8100-1404:~$ free
             total       used       free     shared    buffers     cached
Mem:       8102108    6056172    2045936      36716      71380    4759144
-/+ buffers/cache:    1225648    6876460
Swap:            0          0          0
```But one reason I do not use swap is because originally some Win7 programs stepped on grub2 to save some status in what they "thought" was an unused part of the MBR occupied by grub2. And at least 1 Win7 service pack which had to reboot itself would not properly install when grub was in the MBR. So I wanted to put grub on a partition instead of MBR, Windows was using 3 partitions and I was not sure if grub would boot from an extended partition, so I put grub on primary partition sda4. Although, that is just for emergency if I need it, I normally boot from grub on sdb (SSD with little backup Ubuntu 12.04 updated from 11.10).

I also have an 8 GB laptop and over a year ago installed 13.10 on its sda4 that was originally Win7 D:. I could not get grub to boot from its sda4 because something peculiar in BIOS or MBR kept resetting the boot flag on sda2. So I had to install grub on USB memory stick to boot Linux (which was totally hidden without that). So it has no swap either. But since I recently installed 64-bit 14.04.1 and grub to 512 GB mSATA SSD (sdb) which boots fine on its own, I may convert sda4 to data and/or swap.

---

### Post by oldfred on 2015-02-24
In BIOS mode grub does not use boot flag. 
Windows has to have boot flag on a primary NTFS partition to know which partition has all Windows install's boot files. And only one boot flag per hard drive. Only if using Lilo boot loader would you have a boot flag on a Linux partition. But some BIOS will not let you boot unless you have a boot flag on a primary partition even if you do not have Windows. So we still suggest a boot flag, even if not normally required.

With UEFI, the boot flag must only be on the efi (ESP) partition which should be near beginning of drive, formatted FAT32. Again only one per drive. 

The only reason I have a swap on every drive is that I have an install on every drive, often more than one. But I want every drive to be able to boot without any other drive. Although my data partitions are not on every drive and would give errors on booting if they are on a drive that then has failed. And then, hopefully I have followed the advice on good backups. :)

---

### Post by mattharris4 on 2015-02-25
> **watchpocket said:**
> Quoting oldfred, above: *"And I normally put a swap partition on every rotating drive but not on SSDs."*

I'm guessing he has his reasons for that -- in fact I'd be curious to know what they are.

My understanding is that the constant saving and erasing that takes place with a swap partition causes an SSD to wear out quickly which is not evidently true for a traditional hard drive.  That is also why you never defragment an SSD when you run Windows and Mac based computers.  I am sure someone with much more experience than I will chime in here shortly with a more detailed explanation.

---

### Post by oldfred on 2015-02-25
Most users that have an SSD, also have enough RAM or over 4GB that they may never use swap. Then in most cases it really does not matter as swap is never used. 
I just started not putting swap on SSD and still do that.

Also newer SSDs now have live comparable to hard drives.
 SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)

---

