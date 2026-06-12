---
title: "[SOLVED] Ubuntu 7.10 won't install: Black SoD"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Thanatus on 2008-02-22
Loading kernel, then black, with zero activity after an hour of waiting.

ISO and disk have been MD5 checked, no problems.

I've tried adding multiple things to boot options, like noacpi and all that jazz, not working.


System specs:

8800GTS

HD with 2 partitions (NTFS for Vista and one unformatted, hopefully for Ubuntu to install on) NOTE: plugged in to SATA port 2

2GB RAM


Please help! thanks.

---

### Post by Pumalite on 2008-02-22
If you want to install, try the Alternate CD and at the end configure your xserver.

---

### Post by pbcartwright on 2008-02-22
what happens when you hit- CTRL-ALT-F1 do you get to a text-based login prompt?
sounds like a video problem. log in ( if you can and try:
sudo dpkg-reconfigure xorg.conf

you have an NVIDIA video card maybe?? or ATI??

---

### Post by Thanatus on 2008-02-22
jeez, do you guys read posts before you answer?

8800GTS=nvidia card (known to have issues with installation, i'd like to know how to get around this)

I don't think I can login (or at least see at all). I've tried those key commands, no dice, it stays black.

I will try the alternate version, but something tells me it won't work either.

To be continued...

---

### Post by Pumalite on 2008-02-22
Try it and we''ll see. When you get to the blank screen, report back.

---

### Post by Thanatus on 2008-02-22
> **Pumalite said:**
> Try it and we''ll see. When you get to the blank screen, report back.

Well, this as certainly a learning experience in Linux.

After much tinkering I have it going on an ext2 with grub successfully installed on the MBR.... sorta.

```
ata1: (irq_stat 0x00000040, connection status changed)
ata1: soft resetting port
ata1: SATA link down (SStatus 0 SControl 300)
ata1: EH complete

exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x2 frozen
```

Safe mode cascaes that eror eternally, sometimes hiccuping and spitting  something else out, but never staying long enough to be read. Fortunately, Vista still works perfectly fine.

I'm a complete novice but it seems that it can't access the HD period. It behaved similarly on install but would sometimes work just long enough so it'd finish initializing. But there's no way it's going to boot.

Perhaps the kernel isn't getting along with my JMicron SATA drivers?

And of course, there's still a black screen on normal boot. Unfortunately it seems everyone's having all sorts of weird problems with this release.

Thanks for the assisstance.

---

### Post by Pumalite on 2008-02-22
This is the problem:

'JMicron SATA drivers'

---

### Post by Thanatus on 2008-02-24
Well, after much tinkering, and a near panic after I broke grub and couldn't boot Windows...

 (THANK JESUS AND BILL GATES for bootrec.exe and command prompt in Vista installation disk)

... I'm pretty much back to square one, but fortunately after this mess I think I finally know how to properly proceed with dual booting Vista and Linux.

I beleive the big problem was that I was using a formerly illegitimate copy of Vista Ultimate, but I eventually purchased a key a long time ago. Only problem is, it was still cracked using the BIOS ACPI_SLIC emulation, thereby confusng the Linux kernel to no end and maybe interfering with the MBR as well.


(Big breath) So...

I deduced that there must be some way to configure 2 OSes to run safely, otherwise what would be the point of a "bootmanager" in Vista, which I only learned about because of grub breaking after I got rid of the Linux partition, making any boot from the HD impossible.

C'mon, Microsoft, If you have a cool feature let us know about it. You'd be sooo much better off in the PR department if you could advertise like Apple...

[Ahem] Anyway, I'm thinking of following [this tutorial]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx"). Please tell me if you don't think it would work for some reason.

But, even with ACPI out of the way, it is true there could be driver issues with JMicron as well. Unfortunately those are the drivers designed specifically for my motherboard (ABIT IP35 Pro), so I don't see many options there. Please let me know if Linux is known to have problems.

Until next time...

---

### Post by Pumalite on 2008-02-24
[http://www.google.com/search?hl=en&q=installing+Ubuntu+in+ABIT+IP35+Pro&btnG=Google+Search](http://www.google.com/search?hl=en&q=installing+Ubuntu+in+ABIT+IP35+Pro&btnG=Google+Search)

---

### Post by Pumalite on 2008-02-24
[http://www.google.com/search?hl=en&q=ubuntu+and+JMicron&btnG=Google+Search](http://www.google.com/search?hl=en&q=ubuntu+and+JMicron&btnG=Google+Search)

---

### Post by Thanatus on 2008-02-24
Wow, that's interesting...

I wonder how hard it would be to make a kernel compatible with SATA/IDE combinations...

Interesting indeed, and helpful, to a certain degree, seeing that it prevents me from wasting my time.

I suppose I will give up for now until something arises to support the JMB drivers. Which rightfully should happen because (at least I think) it isn't crazy or uncommon to have a SATA HD and an PATA/IDE optical drive, especially considering SATA optical drives are a little newer compared to SATA HDs (not to mention more reliable than their newer brethren), along with the fact most of the newest chipsets use the JMicron drivers.

Unless there's an actual workaround for this, I suppose I'm very much out of luck.

Thanks once again.

---

### Post by Thanatus on 2008-02-25
I am now happily dual booting Vista and Ubuntu!

It seems JMicron tries to share control with Intel ICH9 and the kernel doesn't like that.

The soultion was as simple as plugging in the SATA HD into a port controlled exclusively by ICH9.

Thank you once again.

---

### Post by Pumalite on 2008-02-25
Glad you got it working. Good luck.

---

### Post by ?uestion on 2008-03-09
Well, I hate to re-open this thread, but I'm having a similar problem to the OP.

I've got an Abit IP35 Pro, 4GB (2x2GB) of RAM, an 8800GT (not GTS), 2 SATA HDDs (one 500GB WD and one 200GB Seagate), one 250GB WD IDE HDD and 2 ODDs (LG H62N and Pioneer DVR-212D). I also can't get past what I see is called the Black SoD. I'm an absolute n00b to Ubuntu (and Linux in general) but I've got a completely blank partition so I wanna give it a shot.

My SATA HDDs are both plugged into the ICH9R ports, as are my ODDs (ports 0 through 3). My IDE hard drive is plugged into the JMicron JMB363 controller along with an eSATA enclosure (currently turned off), and I'm trying to install Ubuntu onto a free partition on the Seagate drive.

So without coming across as totally retarded, what do I need to do?

If it helps, I'm running Vista Business 32-bit (legit) and I'm trying to install the latest release (Gutsy Gibbon 7.10) in 64-bit form. System specs as follows:

Q6600 @ 3.2GHz on abit IP35 Pro
4GB (2x2GB) Mushkin HP2-6400 @ 1068MHz
XFX GeForce 8800GT 512MB @ 700/1000
500GB WD SATA, 200GB Seagate SATA, 250GB WD IDE
Pioneer DVR-212D, LG GSA-H62N

My 200GB Seagate is partitioned into a 120GB drive (where Vista is installed) and a 60GB drive (completely blank except for Norton backup temp files). All drives are NTFS. I'm trying to install Ubuntu on the 60GB partition.

Help please =)

---

