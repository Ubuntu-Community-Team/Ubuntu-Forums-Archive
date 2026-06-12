---
title: "Swap necessary?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by kufford on 2006-06-01
I forgot to include a swap partition. But... I have 2 gigs of ram? Am I alright? I really don't want to reinstall?

---

### Post by equal on 2006-06-01
It's not 100% mandatory, but it would be a good idea to just repartition the drive with at least a 256Mb swap partition at the end of your HDD. It can save you some hassles later on.

---

### Post by philipgm on 2006-06-01
Ubuntu only needs the swap space if it runs out of physical memory. Its a bit like running a Mac with virtual memory turned off. If you run out of memory it may fall down.

In the install Ubuntu defaults to a swap space around three times the size of physical memory, although I think it's unlikely you would need 6GB of swap space! You should be able to repartition with gparted from the repos.

HTH 

Phil

---

### Post by az on 2006-06-01
I think the default swap size varies and is calculated using your total disk size, your total system memory and some funky equasion.  I think you would only end up with three times your ram if you only had a small amount of ram (like 128 megs) and an 160 Gig hard drive...

You need a swap space of 125 per cent of your system ram if you want to use hibernation - and you can hibernate a dekstop - it is useful.

It shouldn't be too hard to boot the live cd and shrink your linux partition down by a gig and make a swap space.  After that, just add a line in your fstab for it:

/dev/hda5       none            swap    sw              0       0

---

### Post by Slim Odds on 2006-06-01
[quote=equal]It's not 100% mandatory, but it would be a good idea to just repartition the drive with at least a 256Mb swap partition at the end of your HDD. It can save you some hassles later on.[/quote]
 
With 2Gig of RAM, a 256Meg swap partition would be pretty pointless. Most folks recommend at least 1.5 times your RAM size for the swap space. But 12.5% is not worth it.

---

### Post by arsolto on 2006-06-02
As general rule, the partition of swap must more or less be the double of the size of the memory of the system (RAM). For example, if a machine possesss 128 megabytes of memory, the archive of swap would have to be of 256 megabytes. Systems with little memory can get better performance with swap more. Less than 256 megabytes of memory it is not recommended and an expansion must be considered. The algorithms of paging of the virtual memory (VM) are syntonized to get performance better when the partition of swap is at least two times the size of the memory. To configure one swap very small can lead to the inefficiency in the code of search of page of the virtual memory and can create problems if more memory will be added.

In systems bigger with multiplos records SCSI (or multiplos records IDE operating in different controllers), swap either configured in each record is recommended that (it stops up to four records). The partitions of swap must approximately be of the same so great. Kernel can manipulate arbitrary sizes but internal structures of data scale to the one up to 4 times for the biggest partition. To keep the partitions of swap with approximately the same so great will allow kernel to optimize the distribution of the space of swap for the partitions. It does not have problems in having great partitions of swap, exactly that swap is not very used. This can facilitate the recovery of data of a program before being forced to restart the machine.

Fonte: [http://www.openit.com.br/freebsd-hb/configtuning-initial.html](http://www.openit.com.br/freebsd-hb/configtuning-initial.html)

---

### Post by cleentrax on 2006-06-02
Linux loves extra RAM. I have 1.2gigs, and a 512mb swap. I typically use 300 mb of RAM for applications, but I frequently hit the swap, especially if I am uploading or downloading a large file through Bittorrent. Ubuntu likes to load it all into RAM so that it doesn't have to keep hitting the hard drive.

---

### Post by flip314 on 2006-06-03
Does anyone have a REFERENCE for the 1.5x-2x values for swap size?  Those numbers get thrown around a lot, but I've never seen a rationale for them.  If you have 32MB of RAM, a 64MB swap seems reasonable, but I'm sure the servers I do my work on for my job don't have a 32GB swap partition for their 16GB of RAM :rolleyes: 

I can understand if the system hibernates to swap why you need at least 100% space*, but otherwise I see absolutely no reason to have a 4GB swap file with 2GB of ram.  I have 1GB of ram, and rarely go above 30-40MB swap usage.  Linux does like to have some swap no matter how much RAM you have, but you don't need that much.

That said, many people run swapless systems without trouble, so if you really want to go without, there's no real reason not to if you've got enough RAM.

*[Incidentally, that may be why my hibernation doesn't work.  I only have a 512MB swap partition ](*,) ]

---

### Post by Master Chief on 2008-05-15
People always wonder how much swap they should put on install, or after installing without a clue think "oh my god", have I put enough swap? Maybe I should just reinstall with more swap...

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

