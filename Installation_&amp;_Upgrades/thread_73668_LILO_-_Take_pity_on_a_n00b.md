---
title: "LILO - Take pity on a n00b"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by Pathogenix on 2005-10-09
First off, seriously impressed with Ubuntu - if I weren't a .NET developer I'd just backup my data and drop Win2k altogether, but such is life.

Okay, my box has a severe allergy to GRUB, which I discovered after a brief flirtation with Gentoo a few months ago.

I installed Ubuntu to HD2 (should I mention how fast and all-round wonderful it was?), installed GRUB to the MBR of HD0, rebooted and got an all-too-familiar error 17. Lovely.

So we re-installed, made HD2.1 bootable (HD2.0 is NTFS) and chucked LILO on it to get a working system back. That worked nicely, I fetched the Emergency Boot CD, repaired my MBR and went merrily on my way.

So, I have two bootable drives, hd0.0 and hd2.1 - I can switch OS by altering the boot order, I have Samba set up to hide the difference on my laptop, all is good. 

The problem is that I don't really want to explain to my beloved that she has to modify the BIOS to get Windows up - all geeks living with non-geeks will appreciate my dilemma.

How can I get a LILO boot menu installed in the MBR for HD0? If anyone can provide me with the right magic words, I'll promise to RTFM until I understand each and every one of them, but I'm loath to tinker without firm guidance because I really need a functioning machine for work purposes... and my beloved will glare at me if I break it again.

---

### Post by annex on 2005-10-10
Okay.  Let me reiterate to make sure I understand your setup.

You have the windows boot loader on hd0.0
You have LILO on hd2.1

Why not add an entry to the windows boot loader to boot linux (i.e. LILO)?

I've never done it but this site seems to have a pretty good howto.  Just consider hd2.1 to be the root partition.

[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

Best of luck.  Putting LILO on the MBR might work as well.  Just put LILO on /dev/hda witha section for /dev/hda1 (windows) and /dev/hdc2 (linux)

---

### Post by Pathogenix on 2005-10-12
Okay,

Sorry it took me so long to get back to you - I think I've completely screwed my various hard drives. For some strange reason, when I tried to get my boot image from the linux drive so I could use it in boot.ini I ended up with a blank GRUB instead of the working LILO boot that runs from hd2. This occurred whether I used dd, or the excellent freeware DOS tool, bootpart.

When I set LILO up to boot into Windows I got an NTLDR missing error which no amount of tinkering would resolve. I eventually came to the conclusion that my GRUB woes were down to the 1024 block limit, added a new boot partition and I can now boot Ubuntu from the primary master with GRUB - lovely.

Unfortunately, booting Windows gives me a GRUB error 13, unsupported or invalid executable format. Most of the info I've found about this online is aimed at people who're running Windows elsewhere than hd0,0 which isn't relevant here.

my menu.lst entry, for the morbidly curious, runs

rootnoverify (hd0,0)
makeactive
chainloader (hd0,0)+1

I suspect that I've made a mess of the primary master because there's now 20MB of unpartitioned space on there which is visible to Linux but not Windows (courtesy of ntfsresize), and I think this might be why the chainloader(hd0,0)+1 is not pointing to a valid bootloader.

I'm going to play some more tonight, and if need be I'll format hd0 and reinstall Windows. Thanks heavens for source control, it's nice to know that my work is stored elsewhere when I go on one of these rampages.

---

### Post by ikd69 on 2005-10-12
[QUOTE=Pathogenix]

First off, seriously impressed with Ubuntu - if I weren't a .NET developer I'd just backup my data and drop Win2k altogether, but such is life.

Have you considered the MONO project for your work?

---

### Post by Pathogenix on 2005-10-12
> Have you considered the MONO project for your work?

Only every time I boot.

The problems there are a) that I'd really rather work on the same platform as my coworkers, b) I work in the beta of .Net 2.0, and c) I build PDA apps to run on Windows devices. Not an auspicious combination for Mono, as much as I agree with and admire the project's aims.

I'm intending to get Mono installed at some point, but to be honest I'd rather pick up C, improve my Ruby and Java, and continue to worship at the altar of Python; when in Rome do as the Romans do.

The whole point of my manic escape from Windows is that at some point I'll be forced to install Vista in order to program for it - by that point I'll have Windows fenced off where it can't do me any harm, XP is bad enough, and this thing looks like a control freak's worst nightmare.

---

