---
title: "BusyBox Initramfs Install Error"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by grahamt2280 on 2008-07-02
Hi all,

I have got problems installing Ubuntu Hardy on to a large hard drive (specifically a Samsung HD300LD 300 Gig).

If I try to do a normal new fresh install, I end up dumped into the Busybox Initramfs text mode, with error text slowly scrolling up the screen. For the exact error text, see (3) below.

I have done a lot of troubleshooting and have conclusively proven to myself that it is not a problem with the install media (1), or the hardware(2).

If I use the boot option [F6] and remove the "quiet" and "splash" options, I can the look at the boot text scrolling up the screen. The last line of boot text appearing prior to being dumped into the BusyBox/Initramfs error mode is:

sda: <4> Driver 'sr' needs updating - please use bus_type methods

I have read up on "Driver sr bus_type" issue, and it appears that is only a warning and not likely to be a cause of this problem.

I have also read up on Boot options
[http://help.ubuntu.com/community/BootOptions](http://help.ubuntu.com/community/BootOptions)
and have tried "noacpi", but the same failure still occurs.

So now I ask for help from the community. How else should I progress trying to get Ubuntu installed on the 300G HDD?

Thanks in advance.

Graham


(1) It's not a problem with the CD media.
===========================================

I've tried using 7 different CDs. All media pass the "Check CD for defects" test without problems.

Canonical offical snail mail Ubuntu CD
Downloaded main ubuntu & kubuntu cds
Downloaded alternate ubuntu & kubuntu cds
Downloaded LinuxMCE cd
Downloaded Mythbuntu cd.


(2) It's not a problem with the hardware.
=========================================

(i) Ubuntu Hardy installs without problems without onto smaller (e.g. 10 Gig ) harddisks.

(ii) Running Ubuntu Hardy in Live CD mode works well, with a small or even with _no_ hard disk installed.

I see the Language menu, then the "bouncing bar", then the Progress Bar climbing to 100% then the normal Ubuntu desktop.
[I]
But if all I do is power off, install the Hard disk, and try again, I see the Cylon bouncing bar then the Error Text.[/I]

(iii) Fedora, Windows 2000 & even Ubuntu 6.04 install and work well without problems on this 300G hard disk. n.b. installing 6.04 and then trying to upgrade to Hardy presents it's own severe problems, so that's no an option.

(iv) I have tried this on 5 different PCs, all work well with Ubuntu Hardy & smaller harddisks &/or Fedora/Windows 2k and the large hard disk. In every combination tested, it is only the combination of Ubuntu & the 300G disk that fails.

(3) Here is the exact error text copied from the normal install process.
================================================== ======================

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 58.809162] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 58.580406] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in

[ 58.580451] ata1.00: status { DRDY }
[ 88.676227] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 88.676273] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in

Then the three lines from "status { DRDY }" repeat until I power off.

---

### Post by Pumalite on 2008-07-02
Get Gparted Live CD, take a look at the drive and prepartition it:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by avtolle on 2008-07-02
Try this as a boot option: all_generic_ide.

---

### Post by kmARC on 2008-08-29
Thank you very much, it works now, with all_generic_ide.

---

### Post by vedanta_2004 on 2008-09-29
How to use this boot option? I'm getting the same problem showing busybox ...

---

### Post by Dr. Marcus Welby on 2008-10-13
thanks Pumalite for this, I was trying for days to get a RAID drive to work.
This is exactly what I needed. Exceptthat I do not know which file system etc to choose.
If you have the time perhaps you could elaborate on your answer?
I tried MS-DOS and a single partition but still get the BusyBox command line.
I'll try the other solutions here and report.
But your reply has definitely moved me closer to Ubuntu.
thanks again

---

### Post by Pumalite on 2008-10-13
It's hardware Raid or FakeRaid?

---

### Post by Dr. Marcus Welby on 2008-10-14
Partitioned the disk as above but Ubuntu 8.04 still stopping at BusyBosx. Fedora loaded OK. Downloaded the beta 8.10 and ran it as a Live CD. Then did the install from the desktop. This worked fine.
Now I just need to find how to increase the screen resolution above 800 x 600 - using ATI Rage XL on board chip.
BTW it was hardware RAID - I don't believe in  software RAID at all - guess this is FakeRAID?
Thanks.

---

