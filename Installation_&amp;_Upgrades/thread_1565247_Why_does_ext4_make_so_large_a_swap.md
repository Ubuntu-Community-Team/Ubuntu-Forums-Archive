---
title: "Why does ext4 make so large a swap"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by mrreality13 on 2010-08-31
Hey gang,
Just wanted to see if any one had this experience?
I just did a fresh install of the recent LTS and saw it made a whopping 8 1/2 gig swap on a new pc I have 3 gigs of ram in?
Im a try to resize as I have already done my customizing to it.
:popcorn:

---

### Post by tgalati4 on 2010-08-31
You can modify swap to any value you want.  You want at least 3.5 GB if you care about hibernation (writing RAM to disk before going to sleep).  Although waking from hibernation takes as long as a cold boot so I don't use it.  

I believe the swap creator script simply takes a percentage of your install partition--so if you have a really big hard disk, then you end up with a really big swap disk.

Swap is normally helpful at 1.5X to 2X your RAM.  You can also use a tiny swap partition (say 256 MB) and that will help loading and running Live CD's--when you want to test new distros for instance.

You can also put multiple swap partitions on a drive, or spread them out over several drives.  The current linux OS will grab them all.  32-bit and 64-bit should be kept separate because they can't be read by the other.  But you can write a boot-up script in /etc/rc.local that remakes swap so you can reuse the same swap space and share it between 32-bit and 64-bit.

---

### Post by srs5694 on 2010-08-31
> **tgalati4 said:**
> You can modify swap to any value you want.  You want at least 3.5 GB if you care about hibernation (writing RAM to disk before going to sleep).  Although waking from hibernation takes as long as a cold boot so I don't use it.

The size of swap required to support hibernation depends on the RAM installed in the computer. Specifically, the swap space must be equal to or greater than the RAM size. (There may be a bit of overhead, too; I'm not sure of that.) Whether resume from disk takes as long as a cold boot probably depends on the system. On my laptop, resume from disk is a bit faster -- and much faster if one counts the time required to start various programs that I normally run.

> You can also put multiple swap partitions on a drive, or spread them out over several drives.  The current linux OS will grab them all.

It may detect them on installation, but AFAIK, swap space must be listed in /etc/fstab for it to be used by Ubuntu once installed. There's little point in putting multiple swap partitions on one drive, and this configuration can actually degrade performance, compared to using one big swap partition. Spreading swap across multiple drives can theoretically improve performance, depending on drive speed, filesystem locations, and other factors.

> 32-bit and 64-bit should be kept separate because they can't be read by the other.  But you can write a boot-up script in /etc/rc.local that remakes swap so you can reuse the same swap space and share it between 32-bit and 64-bit.

I'm pretty sure that 32- vs. 64-bit format makes no difference for swap space. There's no need to "remake" it between boots of 32- vs. 64-bit Linux versions, and in fact doing so could cause serious problems. (Suppose you repartition and forget your script. If it does insufficient testing, the script could easily turn the system root partition or a partition with valuable data into swap space!)

---

### Post by mrreality13 on 2010-09-01
with 3 gigs ram however(hd is 320 gig btw) -IN _theory_ I shouldn't even need a swap or only a real small one say round at most 1 gig or less?
But if the installer automatically uses a % for swap that makes sence.

---

### Post by tgalati4 on 2010-09-01
If you hibernate in 32-bit mode--pull the plug--then cold boot in 64-bit mode, the 64-bit OS can't read the 32-bit swap partition.  If you mkswap under a 32-bit OS, then the 64-bit OS can't read it.  You would need a script to mkswap to be able to use it for 64-bit use.

I doubt you would see a performance hit with multiple swap partitions.  Once you have started to use swap, your performance slows way down anyway.

---

### Post by srs5694 on 2010-09-02
> **tgalati4 said:**
> If you hibernate in 32-bit mode--pull the plug--then cold boot in 64-bit mode, the 64-bit OS can't read the 32-bit swap partition.

If by "can't read," you mean that it won't be accessed as swap after a normal cold boot, then I'm 99% sure you're wrong, although I've not tested this specific situation. If by "can't read" you mean you can't resume from the swap space, then you're probably right -- but booting Installation A and attempting to use the hibernation area created by Installation B is a Bad Idea, no matter what bit-ness they use. Two installations are likely to have different programs running, use different filesystems, etc. At best, when booting Installation A to resume from Installation B's swap would result in a system correctly running Installation B but using Installation A's kernel. I've never tested to see how well this would work, but I suspect it wouldn't work well even when the two use the same kernel architecture, unless maybe they use the exact same kernel.

> If you mkswap under a 32-bit OS, then the 64-bit OS can't read it.  You would need a script to mkswap to be able to use it for 64-bit use.

I just tested to be 100% sure, and you're wrong. I created swap space on a USB flash drive using a 32-bit Fedora install. I was able to use "swapon" to access the space in a 64-bit Gentoo installation with no problems. In the past I've had computers that multi-boot between 32- and 64-bit Linux installations and they've shared swap space just fine.

> I doubt you would see a performance hit with multiple swap partitions.  Once you have started to use swap, your performance slows way down anyway.

I've not measured it; the effect may be minor. It will also vary depending on the locations of the swap spaces. Theoretically, it would be greatest if the swap partitions are widely separated, since that will increase head seek times.

---

