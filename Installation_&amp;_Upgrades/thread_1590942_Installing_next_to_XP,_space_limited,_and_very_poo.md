---
title: "Installing next to XP, space limited, and very poor hardware"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by lepusfelix on 2010-10-08
Hi. I'm looking to dual-boot Ubuntu with the currently-running XP. The HD is tiny by today's standards, and was already partitioned into:

C: (Windows partition) 14.3GB, 6.75GB free
D: 10.4GB, 4.15GB free
E: 3.90GB, 2.73GB free

The majority of what's taking up the space on D and E is extremely useful to keep XP secure, so I'm a bit hesitant to delete anything, but would try to cut back a little if possible.

I'm a complete beginner where it comes to partitioning, so without a very simple step-by-step, I am not confident I'd be able to do much to re-arrange the current partitions, although I do have Norton PartitionMagic installed.

I have attempted booting a LiveCD, but it hung at the familiar Ubuntu splash screen, with the row of red dots, for around 10 minutes before I decided it had frozen there. I also have used wubi, but it was virtually impossible to use, as the mouse trailed like crazy and the whole thing was about as sluggish as a sedated snail (which I know Ubuntu never is). That likely has something to do with running inside Windows on only 512Mb RAM.

I'm reluctant to wipe Windows (at least not yet) because I have experienced issues before with LiveCD's not actually booting properly on some systems, and don't want to take the chance that it could happen on this one, so I'd be looking to get it working before I remove Windows, if I decide to.

---

### Post by Dustin2128 on 2010-10-08
> **lepusfelix said:**
> Hi. I'm looking to dual-boot Ubuntu with the currently-running XP. The HD is tiny by today's standards, and was already partitioned into:

C: (Windows partition) 14.3GB, 6.75GB free
D: 10.4GB, 4.15GB free
E: 3.90GB, 2.73GB free

The majority of what's taking up the space on D and E is extremely useful to keep XP secure, so I'm a bit hesitant to delete anything, but would try to cut back a little if possible.

I'm a complete beginner where it comes to partitioning, so without a very simple step-by-step, I am not confident I'd be able to do much to re-arrange the current partitions, although I do have Norton PartitionMagic installed.

I have attempted booting a LiveCD, but it hung at the familiar Ubuntu splash screen, with the row of red dots, for around 10 minutes before I decided it had frozen there. I also have used wubi, but it was virtually impossible to use, as the mouse trailed like crazy and the whole thing was about as sluggish as a sedated snail (which I know Ubuntu never is). That likely has something to do with running inside Windows on only 512Mb RAM.

I'm reluctant to wipe Windows (at least not yet) because I have experienced issues before with LiveCD's not actually booting properly on some systems, and don't want to take the chance that it could happen on this one, so I'd be looking to get it working before I remove Windows, if I decide to.
I'd not recommend less than 8GB of space for your ubuntu partition, so you should probably just do some disk cleaning, then shrink your C drive xp partition. You might not want to hear this, but the simplest solution would be to simply [buy]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148231") a [bigger]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152244") [drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148397").

---

### Post by phredbull on 2010-10-08
I'm dual booting XP and Lucid on a relatively lo-spec machine w/30g drive; here's my partitioning scheme...
sda1-15g(FAT32)-XP
sda2-1g(Linux swap)-swap
sda3-4g(ext4)-Home
sda4-10g(ext4)-Lucid
Actual formatted sizes are smaller. I'm told the swap partition isn't crucial, and more space on Home would be nice, but I use an external drive for the bulk of my storage needs. I uninstalled as much as I could to minimize XP's size. BTW, I also used WUBI for a few months and it worked pretty well, but full install seems more stable.

I used GParted partition editor on a Karmic live USB. (Live USB takes like 20 minutes to load, but does work, kinda sluggish). I'm no expert, but it was pretty easy, just make sure you do a little research, (primary vs. logical partitions, etc.) Good luck!

---

### Post by snowpine on 2010-10-08
Check out Puppy Linux. It is designed specifically for older hardware, takes up about 100mb, and you can do a "frugal install" that does not require any partitioning. :)

---

### Post by Dustin2128 on 2010-10-08
if we're talking about distros light on resources, I'd recommend [SliTaz]("http://www.slitaz.org/en/").

---

