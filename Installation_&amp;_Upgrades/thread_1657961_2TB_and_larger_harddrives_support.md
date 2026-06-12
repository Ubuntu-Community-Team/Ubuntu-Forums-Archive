---
title: "2TB and larger harddrives support?"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by xerces8 on 2011-01-01
Hi!

With 2TB and 3TB drives available, how is the support from the Ubuntu side?

Anyone tried?
Developers?

Regards,
David

---

### Post by akand074 on 2011-01-01
Ubuntu uses EXT4 file system. EXT4 supports up to 1 Exabyte, with the max size for a single file of 16 Terabytes. I've used a 1TB and 2TB driver personally.

---

### Post by xerces8 on 2011-01-01
The problem is with partitioning, not file systems.

I will try it with a virtual machine, when I have time...

---

### Post by akand074 on 2011-01-02
> **xerces8 said:**
> The problem is with partitioning, not file systems.

I will try it with a virtual machine, when I have time...

What about partitioning? You're allowed up to 4 primary partitions, and as many logical partitions as you want, just like any other hard drive. You can do it with Ubuntu fine with any working hard drive including 2TB and 3TB drives.

---

### Post by xerces8 on 2011-01-02
What if we wait for someone who is aware that the MS-DOS partition format (also known as MBR) can only handle partitions of 2 TB maximum size, shall we?

---

### Post by cascade9 on 2011-01-02
> **xerces8 said:**
> What if we wait for someone who is aware that the MS-DOS partition format (also known as MBR) can only handle partitions of 2 TB maximum size, shall we?

What if somebody said 'GPT'? (GUID Partition Table). 

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

2TB sounds big, but the ladies, genetlemen and small furry creatures from Alpha Centauri who have been using RAID found the 2TB limit quite some time ago.....

---

### Post by ronparent on 2011-01-02
That reference was quite informative.
> 2TB sounds big, but the ladies, genetlemen and small furry creatures from Alpha Centauri who have been using RAID found the 2TB limit quite some time ago.....
... and I love your sense of humor.

---

### Post by srs5694 on 2011-01-02
First, the limit on MBR is 2 TiB (2 x 2^40 bytes), not 2 TB (2 x 10^12 bytes). Modern 2 TB drives are enough under the 2 TiB limit that they have no problems with MBR.

Second, the 2 TiB limit applies when the disk uses 512-byte sectors, since disk addressing on this level is normally done using sector pointers; the MBR limit derives from the fact that is uses 32-bit sector pointers, so it's really a limit of 2^32 sectors. Multiply that by 512 (2^9) and you get 2^41 -- or 2 x 2^40, as stated earlier. If the sector size is increased to 4096, as some drives now use, then the limit goes up to 2^32 x 2^12 = 2^44 bytes, or 16 TiB. Note that this applies to *logical* sector size. Some drives today use 4096-byte physical sector sizes but use 512-byte physical sector sizes, so the 32-bit sector limit works out to 2 TiB for them.

As to the heart of the question, one need only use GPT to bypass this limit; GPT uses 64-bit sector pointers, so the limit becomes 2^64 x 2^9 bytes = 2^73 bytes, or 8 ZiB, when using 512-byte sectors (or 64 ZiB when using 4096-byte sectors). Ubuntu's support for GPT is good, although there are some caveats. Mostly these relate to buggy BIOSes, as described [on this page of mine.](http://www.rodsbooks.com/gdisk/bios.html) You should also be aware of some of GPT's capabilities and requirements, as well as the needs of your boot loader when using GPT. In particular, GRUB 2 works best with a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) when used with GPT on a BIOS-based computer. If your computer uses EFI rather than BIOS, Ubuntu's support becomes rather weak, but that's a firmware issue, not a partition table issue per se.

Filesystem limits can become an issue. According to [Wikipedia,](http://en.wikipedia.org/wiki/Ext3fs) the maximum filesystem size for ext3fs is 16 TB, but I believe it's actually 16 TiB. Ext4fs has a much higher limit (1 EiB), but the current partition creation tools impose a lower 16 TiB limit. If you want to use a really big disk (as in a RAID array or a drive that's fallen through a wormhole from the future), you're better off using XFS (8 EiB maximum filesystem size) or JFS (32 PiB maximum filesystem size) for the moment. Note that filesystem sizes are independent of the disk's sector size, but they do sometimes depend on the allocation block size used in the filesystem itself.

---

### Post by srs5694 on 2011-01-02
a

---

### Post by srs5694 on 2011-01-02
a

---

### Post by xerces8 on 2011-01-02
I did a test with virtual box 4.0.0 and a 5 TB (5000000 megabytes, according to VirtualBox) hard drive.

ubuntu-10.10-desktop-i386.iso installs (uses GPT), but then fails at boot.
Grub is started, but gives
error: file not found

---

### Post by dino99 on 2011-01-02
[http://www.wensley.org.uk/gpt](http://www.wensley.org.uk/gpt)

scroll down to #3

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by xerces8 on 2011-01-02
That bug is about booting OS from second hard drive.
The reporter says the OS on the same drive as GRUB boots OK.
In my case there is only a single drive.

---

### Post by cascade9 on 2011-01-03
> **srs5694 said:**
> First, the limit on MBR is 2 TiB (2 x 2^40 bytes), not 2 TB (2 x 10^12 bytes). Modern 2 TB drives are enough under the 2 TiB limit that they have no problems with MBR.

I thought that was the case, but I didnt want to bring MiB/MB into things (and IMO the whole idea of KiB, MiB and TiB should have been knocked on the head, the only people it serves is the HDD manufacturers)

> **ronparent said:**
> That reference was quite informative.

... and I love your sense of humor.

Pity I stole the humour, but thanks ;)

---

### Post by srs5694 on 2011-01-03
> **dino99 said:**
> [http://www.wensley.org.uk/gpt](http://www.wensley.org.uk/gpt)

scroll down to #3

I'm not sure what you mean by "#3", but if it's anything to do with the advice to create a hybrid MBR, I can only say:

[SIZE=6]Aaaaarrrrrgggghhhh!!!!!! NONONONONONONONO!!!!!![/SIZE]

OK, perhaps I'm overreacting; creating a hybrid MBR won't make your computer explode or turn chocolate into moldy lemons, but hybrid MBRs are ugly and *dangerous*. See [this page of mine](http://www.rodsbooks.com/gdisk/hybrid.html) for details.

The recommendation on that page to use a hybrid MBR seems to be based on the assumption of using an unpatched version of GRUB Legacy, which doesn't understand GPT; but recent versions of Ubuntu use GRUB 2 by default, and GRUB 2 *does* understand GPT. I've got at least two systems booting from GPT disks using GRUB 2 *without* using the ugly and dangerous hybrid MBR.

Sorry for screaming about this; I just see a lot of problem reports in certain forums (like the Apple subforum here) where hybrid MBRs are commonly used, and I've written the [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) partitioning software, so I know how flaky and dangerous hybrid MBRs are. They currently aren't that common in the Linux world, but there's a trend underway to increase their use, and I see a *lot* of grief coming from that. I'd like to head that off, as much as possible. IMO, that page should not be linked to, except to say how *bad* its advice is.

> [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

That's a known problem with GRUB 2 on computers that have both MBR and GPT drives and when you want to boot Windows from the MBR drive. It's easily overcome by adding the following line to /etc/default/grub:

```

GRUB_PRELOAD_MODULES="part_msdos"

```

AFAIK, this is *not* necessary on GPT-only or Linux-only systems. (I've got a Linux-only computer with one GPT and one MBR disk, and this workaround isn't necessary on that system.)

---

### Post by dino99 on 2011-01-03
> **srs5694 said:**
> I'm not sure what you mean by "#3", but if it's anything to do with the advice to create a hybrid MBR, I can only say:

[SIZE=6]Aaaaarrrrrgggghhhh!!!!!! NONONONONONONONO!!!!!![/SIZE]

OK, perhaps I'm overreacting; creating a hybrid MBR won't make your computer explode or turn chocolate into moldy lemons, but hybrid MBRs are ugly and *dangerous*. See [this page of mine](http://www.rodsbooks.com/gdisk/hybrid.html) for details.

The recommendation on that page to use a hybrid MBR seems to be based on the assumption of using an unpatched version of GRUB Legacy, which doesn't understand GPT; but recent versions of Ubuntu use GRUB 2 by default, and GRUB 2 *does* understand GPT. I've got at least two systems booting from GPT disks using GRUB 2 *without* using the ugly and dangerous hybrid MBR.

Sorry for screaming about this; I just see a lot of problem reports in certain forums (like the Apple subforum here) where hybrid MBRs are commonly used, and I've written the [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) partitioning software, so I know how flaky and dangerous hybrid MBRs are. They currently aren't that common in the Linux world, but there's a trend underway to increase their use, and I see a *lot* of grief coming from that. I'd like to head that off, as much as possible. IMO, that page should not be linked to, except to say how *bad* its advice is.



That's a known problem with GRUB 2 on computers that have both MBR and GPT drives and when you want to boot Windows from the MBR drive. It's easily overcome by adding the following line to /etc/default/grub:

```

GRUB_PRELOAD_MODULES="part_msdos"

```

AFAIK, this is *not* necessary on GPT-only or Linux-only systems. (I've got a Linux-only computer with one GPT and one MBR disk, and this workaround isn't necessary on that system.)

Good to know your opinion as tutorials are not so numerous about that, specially on this forum:

[http://ubuntuforums.org/search.php?searchid=78509359](http://ubuntuforums.org/search.php?searchid=78509359)

and thanks for gdisk of course :)

---

### Post by xerces8 on 2011-01-10
> **dino99 said:**
> 
[http://ubuntuforums.org/search.php?searchid=78509359](http://ubuntuforums.org/search.php?searchid=78509359)

This returns:
Sorry - no matches. Please try some different terms.

---

### Post by serge_o on 2011-02-19
as of now official ubuntu 9 and higher cannot install onto 2*2TB software raid 1. Not able to install GRUB bootloader.

It worked fine for me on a single drive, though, everything ok.
tested with 9.10, 10.04, 10.10.

I do not know whether there is an official bug ticket on launchpad about this.

I needed a 2TB raid 1 storage and had no time to work on the issue, so I tested that and then returned to the good old 8.04 LTS, which works with 2TB (because they do not need GTP, could do with simple MBR).

But next week I will get 2*3TB drives and would need to install a storage with these drives... it is a problem then... lets see. maybe latest debian would work?
or centos?

---

### Post by Obi-Wan-YJ on 2011-02-28
If I'm reading correctly, most of the discussion thus far pertains to booting off a 3TB drive when that's the only disk on your system.  I'm running 32-bit U10.10 and booting off a nice, safe, small drive.  My mobo is roughly 3 yrs old (forget the model -- I'm at work now).

I'd like to get a 3TB drive to use in an existing, 2-yr-old Rosewill USB enclosure for backing up all my current drives to a single partition (the 1.5TB drive currently in use for this is 94% full).  This will never be my boot drive.  However, I do want to keep the same USB enclosures if at all possible.  Since the whole point of having a USB drive as my off-site backup is that I can access the data if my current machine disappears, I'd like to have as portable a solution as possible.

Can I buy a 3TB drive and slap it in my current USB enclosure for use as a single partition backup drive?  Will I have to do anything special to make it work?  Does my BIOS have anything to do with it in this scenario?

---

### Post by srs5694 on 2011-02-28
Obi-Wan-YJ,

In theory, what you suggest should work fine. In practice, a lot will depend on your USB enclosure -- or more precisely, its electronics and firmware. If it uses 32-bit sector pointers in its firmware, it won't work with a 3TB drive (unless maybe the drive uses 4KiB logical sectors and the enclosure properly handles that).

You might try contacting the manufacturer to ask about this issue; however, they may be unresponsive or clueless.

As a practical matter, I suggest just buying the drive, and if it doesn't work, either return it or buy a new USB enclosure for it. Alternatively, you could buy an external 3TB drive and then either use your current enclosure for something else or sell it on eBay.

---

### Post by Obi-Wan-YJ on 2011-03-01
> **srs5694 said:**
> You might try contacting the manufacturer to ask about this issue; however, they may be unresponsive or clueless.

Fortunately, Rosewill is neither unresponsive nor clueless.  They answered my email queries in just a couple hours.  Unfortunately, my old RX35-AT-SC enclosures (I have two) are not compatible with 3TB drives.  Rosewill suggests that their RX358 RX-358-U3S enclosures will work much better with 3TB drives ($40 each at newegg).

> As a practical matter, I suggest just buying the drive, and if it doesn't work, either return it or buy a new USB enclosure for it. Alternatively, you could buy an external 3TB drive and then either use your current enclosure for something else or sell it on eBay.

These two external drives provide my off-site backup solution.  I keep them both at my office, and alternate which one I bring home every night to sync up my home system.  Even if my home burns down while I'm syncing one drive, I still have the other one at work with a 2-day old copy of my data.  I chose to get two identical enclosures so that I could leave one power supply at each location and would only have to carry the drive itself back and forth every day.  Buying a new external 3TB drive with its own enclosure to replace the smaller of my two backup drives would still require me to carry the power supply back & forth every day, unless I can get lucky enough to find one that requires the same power supply specs and connector size that I already have.  It's not the end of the world, but it makes the process just that much more cumbersome.

Thanks for your help and the great info.

---

### Post by srs5694 on 2011-03-01
> **Obi-Wan-YJ said:**
> Fortunately, Rosewill is neither unresponsive nor clueless.  They answered my email queries in just a couple hours.  Unfortunately, my old RX35-AT-SC enclosures (I have two) are not compatible with 3TB drives.  Rosewill suggests that their RX358 RX-358-U3S enclosures will work much better with 3TB drives ($40 each at newegg).

There's a possibility that Rosewill's tech support, although prompt, was still clueless. This could happen if they never bothered to test the older enclosure you've got with >2TiB drives. In such a case, it's conceivable that it would still work, but Rosewill doesn't know that it will work, and so they conservatively claim that it won't. I certainly wouldn't gamble a lot of money on that possibility, but depending on the costs, plusses, and minuses of your various options, you might consider trying it out. It might make sense to try it if your next-best option is to buy a new drive and a new enclosure; in that case, buying the drive first and (if it doesn't work) the enclosure later will cost you a bit of time and perhaps extra shipping costs if it doesn't work. That might be an acceptable cost to pay, vs. even a slim possibility of it working and therefore saving the cost of the extra enclosure.

---

