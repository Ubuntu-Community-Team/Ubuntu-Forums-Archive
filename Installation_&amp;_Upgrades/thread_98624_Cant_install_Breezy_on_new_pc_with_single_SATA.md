---
title: "Cant install Breezy on new pc with single SATA"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by cheech_sp on 2005-12-03
I just got a new pc yesterday, wiped and installed windows with no problem.  When I boot to the Breezy install cd and hit Enter at the ubuntu prompt, it says "loading kernel" then reboots.
I've searched and found threads with people asking if its not possible to install Breezy on a single SATA machine, and there doesnt seem to be a clear answer.
I could probably find an old IDE hd, if I have to.
Also, I've used this install cd (32 bit) on other machines with no problem.

PC Specs
HP a1230n
Athlon 64 3700+ (my machine says its a 3800)
1 GB 3200 DDR2
200 GB SATA
Geforce 7800 GT OC - using DVI on a Samsung 930b 19" LCD

---

### Post by igloocentral on 2005-12-03
Ubuntu seems to have difficulty installing on machines with only SATA which really sucks seeing as many new machines are configured this way. I'm trying to install it on my machine which is SATA RAID1 and not having much luck. Hopefully someone can jump in here and help us both! I'd like to configure my machine with hardware RAID instead of software raid so that I can see my windows partitions. Anyone??

Dell PowerEdge 400SC
Promise Fastrak TX2 S150
2 x 160GB SATA HD mirror raid1

What I would like to do:

Primary - 31 MB dell utility partition
Primary - 11 GB NTFS windows xp OS partition
Primary - 122 GB NTFS data partition
Logical partition
  FAT32 - 11 GB data partition
  Ext3 - 10 GB linux / partition
  Swap - 1 GB linux swap partition

I'm available to help test/debug!!!

Also check out
[http://ubuntuforums.org/archive/index.php/t-15605.html](http://ubuntuforums.org/archive/index.php/t-15605.html)
[https://wiki.ubuntu.com/Installation/RAID1](https://wiki.ubuntu.com/Installation/RAID1)
[http://ubuntuforums.org/archive/index.php/t-2557.html](http://ubuntuforums.org/archive/index.php/t-2557.html)

---

### Post by schdefan on 2005-12-04
I installed ubuntu breezy on 4 machines on SATA harddrives without any problems. What exactly does not work?
igloocentral: This week i installed a Promise Fastrak TX4 S300 to use it as a software RAID5. It was a bit tricky to install the modul but at least it is working.


schdefan

---

### Post by metoo on 2005-12-04
The kernel is getting a bit old now, even if it might be patched/updated. Most likely recently introduced chip sets (like the new VIA Southbrige) and modern CPUs (dual core) which came after 2.6.12 are causing problems. The official kernel is at 2.6.14 right now?
RAID is a different problem. Even if your mainboard supports RAID, it is more a software RAID rather than a real hardware RAID. Sharing this between Windows and Linux is reported to be very tricky.

So to the original question:
check your BIOS if you have some entries there regarding the SATA support. Set it to non-RAID if there is anything like this. On my VIA chip set there was an entry which I don't remember correctly but it mentioned RAID and to what to boot up first IDE or SATA, which in your case will be SATA. Booting from SATA first should already be enabled, as there was an OS on the system before.
Your CPU is still single core? Otherwise you might need a smp kernel.

32bit vs 64bit.
I use 64bit. Most stuff works fine, some flash and windows codecs (wma/wmv file playing) does not.
Performancewise there should not be a difference. It's save to use the 32bit version if you need some of the non supported stuff. I'm happy with the 64bit version. There is more info/discussion in the 64bit forum section.

---

### Post by bwog on 2005-12-04
I also installed on SATA without any problems. Point is that the posts in this section are all from users who have problems, that distorts the picture somewhat :) Anyway, there are posts like this that were solved, but the solution can be unexpected like in cases where the DVD writer is the culprit.

---

### Post by cheech_sp on 2006-01-06
ok, so i installed an IDE hard drive as well and get same result.
When I boot to the Breezy install cd and hit Enter at the ubuntu prompt, it says "loading kernel" then reboots.
I've tried 2 diff ubuntu cds, I'll try the 64 bit.

---

### Post by cheech_sp on 2006-01-07
well, the 64 bit setup gets a bit further,
it gets down to listing the hds, ata 1 sata, ata 2 , etc
then just a blinking cursor.
So I would assume my original problem with the 32 bit version is incompatibility with my athlon 64 3800, or some other hardware, but it seems the 64 bit version doesnt like my hds (one sata in 2 partions, and 1 blank ide)
ideas?

---

### Post by kacheng on 2006-01-07
My system kept freezing upon writing the partition table.  I tried 6 different CDs, i386, AMD64, burned at 24x, 8x, 4x.

However, "linux noacpi nolapic" worked for me.

Thanks!

---

