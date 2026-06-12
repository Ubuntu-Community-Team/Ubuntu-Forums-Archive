---
title: "Formatting, and starting over?"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by Mantrasong on 2006-04-05
I currently have my computer set up to dual boot WinXP and Ubuntu on two hard drives, one with windows and one with linux. I recently decided (for a class I'm taking) to add Gentoo to the mix. However, when I went to to create another partition on my second "linux" drive, I discovered that gparted wouldn't recognize my main partition - it sees it, but it calls it unknown, and it won't allow me to resize it, and it says that the partition that should be my swap is formatted as ext3. I haven't been working with linux all that long, but I'm pretty sure thats not correct. 

I've pretty much decided at this point that I don't have the time to mess with it that much to figure out what's going on, and it would probably be easier to reformat and repartition the disk to hold Ubuntu and Gentoo. My main concern at this point is that I don't want to mess up my Windows install in the process (since its on a different disk), so is there anything I need to do to ensure that it doesn't mess that up? Also, any advice as to what might have happened, so I don't do it again a second time, or on how to partition for two linux installs, would be appreciated.

---

### Post by tszanon on 2006-04-05
Well...in order to keep everything that is on the "Windows" HD safe, I would just unplug the HD power cable. No power, no problem. :) 

In case you don't want (or just can't) do that, you shall have no problems as long as you don't commit a mistake during partitioning.

Another point to be careful is during grub install. I had a HD with Windows and Ubuntu. I bought 2 HDs to build a RAID array and, during installation, I installed grub on the "first hd". It made both HDs unbootable and I had to use the Live CD to bring them back. I don't know if anything might go wrong with you, so be careful.

And to be extra careful, you should mount your windows partition as Read Only, or even not mount it.

And, for your other question: I don't know why gparted didn't recognize the partitions.

---

