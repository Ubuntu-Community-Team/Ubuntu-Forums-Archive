---
title: "Dual Booting WinXP with 2 SATA Drives"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by groundhog on 2007-08-09
[FONT=Arial]I had a heck of a time getting WinXP to boot from a secondary SATA drive, but I finally got it to work.  Here's a review of my adventures.  If you're only interested in how it works, scroll down to the end of the post..  :roll:

I upgraded my PC with a new 400Gb SATA hard drive and 1 Gb RAM.  After installing WinXP (SP2) on the new drive, the grub boot loader could not get the Windoze installation on that drive to boot.  On the original (80 Gb) SATA drive, I had RedHat and WinXP (SP1) installed, and grub continued to boot them both just fine.  I googled around a little and found there were known problems in earlier versions of RedHat with grub dual booting Windows, so I thought it was a good time to install ubuntu. [/FONT]
 [RedHat bug report: [https://bugzilla.redhat.com/bugzilla....cgi?id=115980]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980")  ] 
[FONT=Arial](This was an old report, but the version of RedHat I was running was old, too.)

[/FONT] I could not get ubuntu version 7.0.4 to install. I burned two CDs from two different ISOs, but I kept getting the apparently well known debootstrap error. 
[ [http://ubuntuforums.org/archive/index.php/t-76316.html](http://ubuntuforums.org/archive/index.php/t-76316.html) ]
So I downloaded the earlier version 6.06.1 ISO, and it installed without incident. I think the 7.0.4 version of the ubuntu install has issues. 

OK, now I had ubuntu loaded and working great, but grub was still not working properly. It was the exact same issue I had with RedHat: grub could not boot the Windows OS located on the secondary disk.  The problem is apparently a deficiency in the way Windows boots, but the drive mapping trick in grub did not work for me.  I was starting to believe this "finicky Windows booting" problem was also a SATA issue.

In the GNU grub online manual, in the DOS/Windows Boot section, after a discussion about mapping the drives to trick Windows into thinking it is on the primary drive when it really isn't, there is this note of caution:
"This is effective only if DOS (or Windows) uses BIOS to access the swapped disks. If that OS uses a special driver for the disks, this probably won't work."
[grub manual: [http://www.gnu.org/software/grub/man...OS_002fWindows]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows") ]

It is, in fact, the case that the bios on my mobo does not recognize SATA drives, and there is a "special driver" for both SATA drives on my PC (Silicon Image SiI 3112 SATARaid Controller).  I hated the idea of having to switch the cables on my SATA drives in order to boot the new Windoze OS... :-({|=

I eventually started fiddling with the Windows native boot loader (of sorts), boot.ini, and here's where I finally had joy.  In the [operating systems] section I added a line for the WinXP SP2 installation on the secondary disk.  Here's what the section looks like now:

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="WinXP SP1" /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="WinXP SP2" /fastdetect

Here's how it works: The original 80 Gb SATA is the primary disk with ubuntu and WinXP SP1.   When the PC powers up, grub lets me choose between two OSs: ubuntu and WinXP.  Selecting WinXP from the grub menu gets me to boot.ini, where I can then select between SP1 on the primary disk, and SP2 on the secondary disk.

:-\"

- djb

system:
AMD Athlon XP Barton 2800+
Asus A7N8X-E Deluxe mobo
1 Gb Kingston dual channel DDR RAM
80 Gb Seagate ST380013 SATA hard drive
   (primary disk with ubuntu and WinXP SP1)
400 Gb Western Digital WD4000AAKS SATA hard drive
   (secondary disk with WinXP SP2)

---

### Post by logos34 on 2007-08-09
> but the drive mapping trick in grub did not work for me. I was starting to believe this "finicky Windows booting" problem was also a SATA issue.

In the GNU grub online manual, in the DOS/Windows Boot section, after a discussion about mapping the drives to trick Windows into thinking it is on the primary drive when it really isn't, there is this note of caution:
"This is effective only if DOS (or Windows) uses BIOS to access the swapped disks. If that OS uses a special driver for the disks, this probably won't work."
[grub manual: [http://www.gnu.org/software/grub/man...OS_002fWind](http://www.gnu.org/software/grub/man...OS_002fWind) ows ]

It is, in fact, the case that the bios on my mobo does not recognize SATA drives, and there is a "special driver" for both SATA drives on my PC (Silicon Image SiI 3112 SATARaid Controller). I hated the idea of having to switch the cables on my SATA drives in order to boot the new Windoze OS... 

Interesting, but I'm wondering if 'special driver' does not refer to RAID, LVM or EVMS drivers, or software drivers for PCI SATA host adapter add-in cards...Even though you're not running RAID did you perchance install raid drivers from a floppy during windows install (i.e. F6 routine)?  Or is raid enabled in the BIOS (it shouldn't be)?  I haven't run into that problem personally and I've tried any number of dual boot XP/linux configs on dual disks (usb, ide, sata).  I have an nvidia chipset and I'm using the the Nvidia SW driver **IDE SataIDE Driver (v6.66) "WHQL"**  for my ide devices as well (on x64 XP platform).

Is there a chance there was an error in your menu.lst entry (i.e. map lines) for XP?
(or maybe you didn't edit /boot/grub/device.map)

---

### Post by groundhog on 2007-08-09
Short answers:
- menu.lst was configured correctly but did not work.
- Yes, I did use a floppy to install SATA RAID via F6.

Long answers:
I monkeyed with menu.lst for quite a while, starting with the configuration provided in the GNU grub online manual.  Then I tried various modifications, and nothing worked.  The boot loader would get to the point to where the command lines were repeated, then the screen would hang up.  It was a typical problem reported by many users, both RedHat and ubuntu.   

I'm not sure yet, but the problems may be traced back to the age of the motherboards: mine is from late 2003, when SATA was still very new. My mobo has SATA connections, but the BIOS did not support it (and still doesn't - I have the "latest" BIOS from Asus, dated Jan-2005...).

My understanding of the SiI 3112 SATARaid Controller is that it can be used to configure either a true redundant array or single disks.  *i.e.*, the "Raid" is an option.  At any rate, the SiI 3112 was what I used for the first disk back in 2003, and the Silicon Image website strongly discourages mixing and matching (using different controllers for different disks). One thing I could try, perhaps, is to use a newer version of SI controller for both disks...Hmmm...

I might also add, this system will be 4 years old this fall, but it has been a great performer all these years, otherwise I would have built a whole new system.  It's still running fine and as fast as ever. I'm planning to dive into the world of VMWare, hence the need for more disk space and RAM.

- djb

---

