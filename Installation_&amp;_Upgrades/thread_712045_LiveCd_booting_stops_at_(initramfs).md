---
title: "LiveCd booting stops at (initramfs)"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by bill48er on 2008-03-01
Hi
Complete newbie - wanting to give Ubuntu a try on my PC but....
I'm having a Livecd boot up failure - following the instruction from elsewhere of placing break=top at the front of the boot options drops me to a (initramfs) prompt. Entering modprobe piix results in "FATAL: Module piix not found".
Then entering exit restarts the splash screen and the pc starts hunting for a floppy in dive A then drops to the (initramfs) prompt. The same thing happens when allowing the LiveCD to boot normally. Disabling the floppy in bios does not help.

The LiveCD work fine on my Dell laptop - boots almost as fast as XP - connected to the internet via wireless - played games checked out Open office etc - all looks good now I want to try in on my PC prior to installing it.

Any further suggestions welcome as I'm hoping that I can avoid upgrading to windoze vista. 

My kit:

< Hardware >
    Processor:          AMD Athlon(tm) Processor 1.0 GHz
    Math Support:       On Chip
    BIOS:               Award Software 
    Motherboard    ASUS A7V
    Bus Type:           PCI,ISA,USB,AGP
    Ports:              1 Parallel, 2 Serial
    Memory:             511 MB  (42% Utilized)
    Floppy Disks:       1.44 MB
    Hard Disks:         37.27 GB, 28.63 GB
    Multimedia:         Sound, DVD-ROM, DVD RW
    Video:            1024x768 in 256 Colors, NVIDIA GeForce2 MX/MX 400 Ver. 4.0
    Monitor: AOC

---

### Post by Pumalite on 2008-03-01
Install with the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less, as 'image' and not 'data', in good quality CD-R media, check CD integrity before installation.

---

### Post by rustygates on 2008-03-01
try the 6,06 the 7.01 didnt work for me on this puter but the 6.06 works boots to the live cd no proublem.

---

### Post by bill48er on 2008-03-09
The "Alternate" CD did the trick - many thanks.

However, it took 2 different PC's, 3 different burning programs and three different makes of blank CD's before I got a fully working bootable CD (why is it so difficult?) - it took a download of InfraRecorder before I got a working copy. (A set of coasters anyone?)

I am puzzled as to why the "Alternate"  works and "LiveCd" does not ?!

Now - it's time to explore the world of Linux.
My printer and scanner both installed at first connection - the scanner has never worked satisfactorily in Windoze. Camera connected fist time. Only problem so far was getting my USB memory sticks to work.

On-wards and up-wards.

Cheers
Bill

---

### Post by Pumalite on 2008-03-09
You are welcome. The Alternate is made to avoid hardware/graphics problems.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by st0n3cutt3r on 2008-03-10
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Read this.  It helped me with the same issue!

---

### Post by Pumalite on 2008-03-10
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by bill48er on 2008-03-10
> **Pumalite said:**
> You are welcome. The Alternate is made to avoid hardware/graphics problems.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

Brilliant - "13 Things to do immediately after installing Ubuntu" - just what the doctor ordered!

I'm bookmarking this thread until I check out the rest of the links.
'Tis many a year since I played with the DOS prompt and wrote .bat files - it looks like I will be brushing up on those skill - I just need to get to grips with what some of the strange command names are and what they do. :lolflag:

---

### Post by Pumalite on 2008-03-10
Good luck. Lots of fun ahead.

---

