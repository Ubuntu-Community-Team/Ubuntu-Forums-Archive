---
title: "ssd?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by northwestuntu on 2010-03-20
would a ssd be a optimized in 10.4? been thinking about getting one since the price is under 100 now.  would it be worth it for speed?

my idea was to buy the ssd for my os and then use my other sata drives for files.

---

### Post by Reiger on 2010-03-20
Depends on how much SSD you need; and &#8220;what files&#8221; you would keep on the SSD. Obviously your gigabytes of accumulated file-history isn't going to fit what will be left of a SSD after default installation.

However, the SSD's that are under $100 are apparently not ... that good (heavily biased towards reading not that much bang-for-buck-per-gigabyte compared to the more full featured likes of an X25M and not even reading is as good as X25M). This is somewhat of a concern if justifying spending that much money on hardware is: the one thing that drives processor usage through the roof in its brief spell of booting the OS is *writing* the log records. Small, random writes. Similarly I imagine that upgrading your OS through the package manager isn't going to be significantly quicker or anything than doing this on a more conventional harddisk -- simply because it's again a lot of small writes.

OTOH the proper &#8364;180,- Intel X25M is pure awesome. A lot of money for 80GB up front but it is seriously quick. Intel obviously thinks so too: the only non-OEM thing (didn't even supply screws) the kit included was a cheesy sticker reading &#8220;MY SSD ROCKS&#8221;. No kidding.

---

### Post by vishalrao on 2010-03-21
My personal recommendation - avoid Intel for Linux unless you want to manually run wiper scripts etc.

Get an IndiLinx Barefoot controller based driver with the "1916" version firmware like my Crucial M225 model SSD which has both TRIM and GC because Linux does not yet do TRIM well the GC is a lifesaver and it automatically keeps your drive running like new!

My motherboard BIOS probably has a problem where I have to set kernel option "libata.force.noncq" to prevent it from spewing out a lot of error messages but other than that everything is smooth as silk :D

See my blog here: [http://lahsiv.net/blog/?p=47](http://lahsiv.net/blog/?p=47)

---

### Post by IanW on 2010-03-21
I read elsewhere on this forum that booting the 2.6.33 kernel with option "discard" will give TRIM support.

Of course, you'll have to install that kernel manually, from the kernel team's [PPA](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

You'll need to download and install 3 deb files:-
linux-headers-***_all.deb
linux-headers-***_arch.deb
linux-image-***_arch.deb

Where "arch"="i386" or "amd64", depending on your needs

---

### Post by northwestuntu on 2010-03-21
so it doesnt sound like a must have option right now.  i was looking at a ozc at newegg.com.  it was only 30gb, but it would only be used for the os and programs.  my home folder would be on a tb sata drive.

---

### Post by Sockerdrickan on 2010-03-21
10.04 keeps bugging me about a broken hdd each time I log on. I have a SSD Vertex limited edition 100GB and it's not broken. Ubuntu isn't ready for SSD's yet.

---

### Post by vishalrao on 2010-03-21
Apparently it is "normal" for SSD to have "bad blocks" on their flash chips and their firmware "reroutes" storage around them so you can open the disk utility and select the drive and check the box that says "dont warn me about this drive".... note its just a "warning" not a fatal/concerning problem, unless of course it gets worse and your disk fails then for sure its a problem :D

---

### Post by andrewabc on 2010-03-21
ubuntu 10.04 won't have TRIM support by default. :(

I also don't think it will align SSD to optimal level either. You can fix this yourself before installing OS onto it. I dunno if gparted or the installer works to align properly. There might have been updates but last I heard it still didn't.

I'd also recommend an OCZ vertex or agility (don't buy based upon mail in rebates). With the garbage collection it will help maintain performance in RAID and non TRIM OS.
Wait for sales on SSD as that is when prices are only good. Got my 60gb vertex on sale for $200 free shipping last October, and finally regular prices have it close to that price now (in CAD).

SSD are worth it for speed. No more firefox hard drive thrashing when typing into address bar or using bookmarks (due to the firefox profile and 23mb sql database that has lots of small reads/write).

If you got $ get two 30gb and RAID them for some nice speed. :)
Or just buy one for now, and maybe in future when they go even cheaper get another. That's my plan.

I don't recommend ocz vertex limited edition. speed of it is nice, but only 5000 were made and one that was tested died. [here](http://www.anandtech.com/storage/showdoc.aspx?i=3747) is review. Anandtech has best SSD articles.

I'm really looking forward to 10.10 as it will have a lot newer technologies. For example they are using intel drivers from last summer instead of one that was released in December because of architectural changes that might negatively affect i8x6 (old P4 intel) users.

---

### Post by ShadowDragon on 2010-03-21
You can use your SSD in Ubuntu without having any problems. I'm running a OCZ Vertex 30GB since June '09, and the speed gains are outstanding. Best hardware upgrade ever.

But if you want to squeeze the maximum out of it, you will need to do a small amount of manual configuration, like alignment, I/O Scheduler, ext4-mount options noatime, tmp-files on a RAM-disk, TRIM with the mainline kernel and ext4-mount option discard, etc etc etc. But you can just pick out the tweaks you like, if you don't feed comfy with installing mainline kernels then you don't have to do that and you would still have a super-fast disk.

I have based my chose of SSD on the amount of support and information there was available. The OCZ-forums have a separated section for linux-users with there own tips, tweaks and tricks.

So I don't think you would regret buying a SSD, since they are out there for some time now and there is a lot of info available. Plus everything will go so much faster when you install it. :D

---

### Post by trystan.snyder on 2010-03-22
> **andrewabc said:**
> ubuntu 10.04 won't have TRIM support by default. :(



Is there any official source on that?

---

### Post by andrewabc on 2010-03-22
> **trystan.snyder said:**
> Is there any official source on that?
No official source, as they could implement it whenever.

It will only happen if they backport that feature into the kernel.

TRIM was officially supported in .33 kernel.
Ubuntu 10.04 is using .32 kernel

So either devs backport, or people will have to manually install .33 kernel.

Maybe they will backport it eventually (sometime in 2 years), but dunno about it getting done by release date.

I think they said lots of backporting will be possible/needed since using older kernel. But who knows exactly what will get backported.

I don't got my hopes up, I just assume it won't be in it until 10.10 release.

---

### Post by psusi on 2010-03-22
> **vishalrao said:**
> My personal recommendation - avoid Intel for Linux unless you want to manually run wiper scripts etc.

Get an IndiLinx Barefoot controller based driver with the "1916" version firmware like my Crucial M225 model SSD which has both TRIM and GC because Linux does not yet do TRIM well the GC is a lifesaver and it automatically keeps your drive running like new!


The wiper script just manually issues TRIM commands for all free blocks on the disk.  You seem to suggest that it is for disks that don't support TRIM.

Automatic TRIM support went in to 2.6.33 and Ubuntu 10.04 will be shipping with 2.6.32, so it will not be there.  It doesn't really matter though unless you fill up the drive.  If you leave a few gigs unpartitioned so you never use those blocks the GC will always have enough free space to work with.

I've been using the OCZ Vertex 64GB for over a week now and it is VERY nice, though I am still trying to figure out why disabling NCQ speeds it up, and had to manually align the partition/lvm pv for optimal performance.

---

### Post by IanW on 2010-04-03
It seems TRIM was backported into 2.6.32-9.13.

>  * ext4: make trim/discard optional (and off by default)


Full changelog [URL="https://launchpad.net/ubuntu/lucid/+source/linux
/+changelog"]here[/URL].

So I'll try booting with "discard" in my kernel line next time I reboot.

---

### Post by MadsRH on 2010-04-03
> **northwestuntu said:**
> ...my idea was to buy the ssd for my os and then use my other sata drives for files.

I've got that setup and it's very nice. A small SSD for the OS and a spinning disk for all my data. Lucid is awesome on SSD (*except I can't boot at the moment* ;-)).

---

### Post by vishalrao on 2010-04-03
> **IanW said:**
> It seems TRIM was backported into 2.6.32-9.13.

ah, nice, if it works well enough then i guess most SSDs are 'ready to rock' with lucid!

---

### Post by fjf on 2010-04-03
I will get an intel SSD when lucid comes out.  I found a nice how-to on how activate trim and other tweaks [http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/") but i havent found the partition alignment tutorial yet.  Anyone found the way with gparted?.

> **psusi said:**
> The wiper script just manually issues TRIM commands for all free blocks on the disk.  You seem to suggest that it is for disks that don't support TRIM.

Automatic TRIM support went in to 2.6.33 and Ubuntu 10.04 will be shipping with 2.6.32, so it will not be there.  It doesn't really matter though unless you fill up the drive.  If you leave a few gigs unpartitioned so you never use those blocks the GC will always have enough free space to work with.

I've been using the OCZ Vertex 64GB for over a week now and it is VERY nice, though I am still trying to figure out why disabling NCQ speeds it up, and had to manually align the partition/lvm pv for optimal performance.

---

### Post by andrewabc on 2010-04-03
ext4: make trim/discard optional (and off by default)

Is there a howto to enable it? It doesn't turn on if it detects SSD?

[fixed link for changelog](https://launchpad.net/ubuntu/lucid/+source/linux/+changelog)

---

### Post by ShadowDragon on 2010-04-03
> **IanW said:**
> It seems TRIM was backported into 2.6.32-9.13.

> * ext4: make trim/discard optional (and off by default)

Full changelog [URL="https://launchpad.net/ubuntu/lucid/+source/linux
/+changelog"]here[/URL].

So I'll try booting with "discard" in my kernel line next time I reboot.
No, that's making a false alarm mate... ;)

The line you see there is just a copy / paste from the 2.6.32.1 release notes, which is talking about [commit eac39ba7f50e851f4e20466e5d390f046932287](http://github.com/pfactum/pf-kernel/commit/feac39ba7f50e851f4e20466e5d390f046932287) which is about just about a setting, making trim off by default.

If you want native TRIM support you need [this commit](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=18f0f97850059303ed73b1f02084f55ca330a80c) which fixes libata so that ATA-devices get TRIM support. And for now, that commit it's only in 2.6.33 and higher ...

**Edit:** Although there seems to be something in [Snapshots /patch-2.6.32-git2.log](http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.32-git2.log). If you do a search for "18f0f97850059303ed73b1f02084f55ca330a80c", you have found the same commit as in the changelog of 2.6.33... I only don't know what Snapshots /patch-2.6.32-git2 means...

---

### Post by shimoda on 2010-04-10
It should be interesting if someone has more news about including **TRIM** **in kernel** 32 (aka 10.04)...

Another thing is the **Partition Alignment**... All info I read is really old, speaking of WinXP, speaking of first SSD drives...

Now with newer drives, with ext4 and trim, is really important to manually align a partition in an SSD? 
Is a gain in performance or in life time? (or both?)

---

### Post by powder on 2010-04-10
> **shimoda said:**
> Now with newer drives, with ext4 and trim, is really important to manually align a partition in an SSD? 
Is a gain in performance or in life time? (or both?)

AFAIK, the benefit of partition alignment hasn't been proven, but is generally considered to be a good idea.  Alignment would theoretically prevent erase block fragmentation that would cause write amplification and slow down the performance of the drive.

---

### Post by Reiger on 2010-04-10
The lifetime depends on how effective the wear leveling algorithm is; which in turn depends on the amount of data you store. For instance if you only use e.g. 50 out of 80 GB this leaves the controller free to use 30GB to buy you additional operating time; compared to say 79.5GB out of 80GB which leaves only 0.5GB to play wear leveling with.

Trim helps the wear leveling algorithm do its job because it marks blocks as &#8220;reclaim-able&#8221;. Essentially it is a bit of feedback from the (logical) file system layer to the hardware saying &#8220;hey I don't need this data anymore&#8221;. (E.g. you just issued rm -rf / meaning you don't need your OS on disk anymore).

Partition alignment helps to align partitions with the internal data layout, thereby minimising overhead. It is IMHO a bit overkill if you have a half-decent SSD. After all, SSD's are so much faster than ordinary SATA/USB mass storage hardware...

---

### Post by andrewabc on 2010-04-10
Proper alignment is very important.
[Linux - Tips, tweaks and alignment ](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

For ocz products 512kb alignment is the same size as erase block size.

Of course if you know you will be writing lots of large files all the time, then larger block size should get you higher write speeds for large files. Lower block size will get you better smaller file size read?/write.

I'm not sure what ubuntu defaults to.

---

### Post by KegHead on 2010-04-10
Hi!

I run 10.04 b2 on a Dell mini w/16gb ssd hd.

It flies.

Waiting for final release.

KegHead

---

### Post by Kokopelli on 2010-04-10
Block alignment was definitely of use in first generation SSDs.  For 2d generation SSDs such, as the current Intel X-25Ms, the benefit is more debatable however.  Aligning partitions to erase boundaries is a one time cost of time at set up however and at the very least will not hurt. 

Has anyone confirmed whether or not Lucid has TRIM support at the kernel level yet? Specifically backporting .33 TRIM support so it can be used with EXT4.

---

### Post by psusi on 2010-04-10
> **Reiger said:**
> The lifetime depends on how effective the wear leveling algorithm is; which in turn depends on the amount of data you store. For instance if you only use e.g. 50 out of 80 GB this leaves the controller free to use 30GB to buy you additional operating time; compared to say 79.5GB out of 80GB which leaves only 0.5GB to play wear leveling with.

Trim helps the wear leveling algorithm do its job because it marks blocks as “reclaim-able”. Essentially it is a bit of feedback from the (logical) file system layer to the hardware saying “hey I don't need this data anymore”. (E.g. you just issued rm -rf / meaning you don't need your OS on disk anymore).


That's actually not true.  Wear leveling does not REQUIRE free blocks, it just slows down a lot without them since it has to first erase a block or two then rewrite them just to satisfy one small write request from the OS.

As for partition alignment I have an OCZ Vertex 64 gb and it does make a difference, though not a very noticeable one outside of benchmarking.  You shouldn't have to worry about it in Karmic though since by default it aligns partitions to 1mb like windows 7.

> **Kokopelli said:**
> 
Has anyone confirmed whether or not Lucid has TRIM support at the kernel level yet? Specifically backporting .33 TRIM support so it can be used with EXT4.

No, it doesn't.  You can build yourself the latest hdparm from source though and use the wiper.sh script to trim the drive manually though.  Unless you are using LVM like I am.  So far I have not worried about it and have not seen any consequences, nor should you until after you have written to pretty much every block on the disk.  You can make sure you never do this by leaving some unpartitioned space.  A few mb should do.

---

### Post by shimoda on 2010-04-11
> **psusi said:**
> That's actually not true.  Wear leveling does not REQUIRE free blocks, it just slows down a lot without them since it has to first erase a block or two then rewrite them just to satisfy one small write request from the OS.

I read somewhere that a safe setting rounded 20% of free space for optimal use...
About this, I don't know one thing. When you and **Reiger** speak of free blocks... Are you referring to "unpartitioned space" in drive or to "unused space" in current partition? :confused:

---

### Post by ShadowDragon on 2010-04-11
Partition alignment: You should try to apply that if you can. There is not a single use-case where it can have negative consequences. So it's always a win. However the impact isn't as large in all use-cases that you would notice it as a user. But you can't loose with it and I even think it's even adviced to do so in the appendix of the ATA specs.

Free space: This should be interpreted as NAND-pages/blocks which are interpreted by the SSD-controler as free space. And since the only way to occupy that space is when the OS writes to a LBA and send that command to the drive the following situations are in play:
[LIST]
[*]If you wipe your drive clean and you apply an HPA (Host Protected Area) that space is free.
[*]If you wipe your drive clean and you under-partition your drive (a.k.a. over-provisioning) that space is free.
[*]If you wipe your drive clean and have native TRIM running on your file-system (and the trim-implemantation is to do everything), all your free space in your file-system is free space.
[*]If you wipe your drive clean and have native TRIM running on your file-system (and the trim-implemantation is only best effort), a large part of your free space in your file-system is free space, but not nessecarely all.
[*]If you wipe your drive clean and don't have TRIM running, not all free space in your file-system is free space. You're dependent on the LBA-reuse implementation of your OS and the min amount of free space in your filesystem you had since your last cleaned your drive.
[/LIST]

---

### Post by shimoda on 2010-04-11
thanks SD, very clear!!

---

### Post by fjf on 2010-04-12
Is there a guide on how to align partitions using the partitioner of the ubuntu live CD (or other open source partitioner)?.  I haven't found a clear How-to do it yet.

> **ShadowDragon said:**
> Partition alignment: You should try to apply that if you can. There is not a single use-case where it can have negative consequences. So it's always a win. However the impact isn't as large in all use-cases that you would notice it as a user. But you can't loose with it and I even think it's even adviced to do so in the appendix of the ATA specs.

Free space: This should be interpreted as NAND-pages/blocks which are interpreted by the SSD-controler as free space. And since the only way to occupy that space is when the OS writes to a LBA and send that command to the drive the following situations are in play:
[LIST]
[*]If you wipe your drive clean and you apply an HPA (Host Protected Area) that space is free.
[*]If you wipe your drive clean and you under-partition your drive (a.k.a. over-provisioning) that space is free.
[*]If you wipe your drive clean and have native TRIM running on your file-system (and the trim-implemantation is to do everything), all your free space in your file-system is free space.
[*]If you wipe your drive clean and have native TRIM running on your file-system (and the trim-implemantation is only best effort), a large part of your free space in your file-system is free space, but not nessecarely all.
[*]If you wipe your drive clean and don't have TRIM running, not all free space in your file-system is free space. You're dependent on the LBA-reuse implementation of your OS and the min amount of free space in your filesystem you had since your last cleaned your drive.
[/LIST]

---

### Post by shimoda on 2010-04-12
> **fjf said:**
> Is there a guide on how to align partitions using the partitioner of the ubuntu live CD (or other open source partitioner)?.  I haven't found a clear How-to do it yet.

psusi wrote:
> **psusi said:**
> You shouldn't have to worry about it in Karmic though since by default it aligns partitions to 1mb like windows 7.

I'd not tried it yet... But if the "auto" mode not works, after searching I found that the easiest method is use gparted, leaving 1Mb **before** the partition...

---

### Post by Taoye on 2010-04-12
I'm using a 128GB OCZ Agility SSD in my MacBook Pro 13" with Lucid beta 2 and I have no problems whatsoever with the SSD... everything runs snappy, boot speed is fast, overall a very nice improvement over a regular HDD, even without TRIM support.

---

### Post by ShadowDragon on 2010-04-12
> **fjf said:**
> Is there a guide on how to align partitions using the partitioner of the ubuntu live CD (or other open source partitioner)?.  I haven't found a clear How-to do it yet.
Have you tried ["Partition alignment for OCZ Vertex in Linux" by TortureTest @ OCZ-forum](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)? It's quite complete.

---

