---
title: "[SOLVED] Hardy partitioner does not detect disk"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Phasmus on 2008-07-30
-----
Is your partitioner showing a big unallocated space on your drive, even though you can access your drives' contents with other applications?  Then read on, because you might have the same problem I did (overlapping partitions).  Using testdisk as described on page 2 can uncover and repair that, plus a lot of other oddball disk issues.
-----

G'day.  My problem is mysterious.  I have 2 SATA disks on my computer.  In the installer-partitioner and GParted one of them shows up as 'Unallocated' even though it is NTFS (and even if I were willing to risk manipulating a disk whose partition was incorrectly detected, that's not the one where I want to install).  The other one doesn't show up at all (it's partitioned into NTFS and EXT3).

All of my disks, and their contents show up correctly in Nautilus though, so it's not that the disks can't be read or mounted.  It's just that the partitioner isn't seeing them.  Even after mounting them through Nautilus the partitioner's behavior does not change.

To add still more confusion, I successfully installed a Hardy beta on this system a few months ago.  While it is possible that I had to do some kernel-line tweaking to do so I certainly don't remember that being the case.

I observed due-diligence in searching for an answer to this problem, but didn't spot much in the archives.  I did try loading the live CD with the all_generic_ide kernel parameter to no avail.  My cd is correctly burnt.

Any help would be appreciated.

---

### Post by Phasmus on 2008-08-02
G'day,

My own further investigations have revealed... not so much... over the past couple days.  Perhaps this, the output of fdisk -l, will shed some light on the subject to those savvier than myself?

omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b2c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6526    52420063+  83  Linux
/dev/sda2   *        6527       12928    51424065    7  HPFS/NTFS
/dev/sda3           12929      121601   872915872+   5  Extended
/dev/sda4          120846      121601     6072538+  82  Linux swap / Solaris
/dev/sda5           12929      120845   866843239+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)


So the issue is not of one hard drive being detected (I don't know why I thought I had two in there...) it is that my one internal hard drive (the 1-terrabyte on /dev/sda) isn't getting its partitions detected by the partitioners.  In gparted it just shows up as 'unallocated \ 931.51 GiB'.  

Repartitioning the whole thing isn't an option.  As you can see I have a little chunk of space ready for Ubuntu and the other areas are full of user data I don't want to mess with.  For the record, there is a broken and unusable install of a Hardy-Beta on the exiting linux partition.  Broken as it may be it does boot (I have no desire to do anything with it but over-write it, bit it demonstrates that my disk parameters are linux-bootable as-is).  So the question remains how do I help the installer-partitioner to get a clue here?

One theory I had was that this is a bug specific to gparted or one of its constituent packages (surely if part of the OS correctly detects my partitions the programs that don't are broken), so if I could upgrade it in the livecd environment it would work and I could proceed, but I don't see anything obviously relevant in the updated packages.

I am... aware... of options such as the Alternative Installation CD and other distros, but I would really prefer if it didn't come to that.  I know the regular installer -can- work because it -did- work before.

---

### Post by redraiderbum on 2008-08-02
> So the issue is not of one hard drive being detected (I don't know why I thought I had two in there...) it is that my one internal hard drive (the 1-terrabyte on /dev/sda) isn't getting its partitions detected by the partitioners.

You do have two hard disks in there.  It says your first hard drive is a 1 TB drive and your second is a 250 GB drive.  Both are sata drives.  Do you not want to install Ubuntu on the 250 GB drive?

I'm not totally sure what you want to do?  If you don't want to repartition you could just start up the installer and tell the installer not to do anything but repartition the existing 'linux' partition for use with the installation.  It is strange that gparted detects it incorrectly, but that doesn't mean the installer is going to.  If the installer is recognizing incorrectly simply cancel the installation before proceeding.

If you go to the places drop-down menu and choose computer can you not mount the other partitions?  If not you can force them to be mounted using the mount command, specifying the file system and mount point (a local folder).  Generally, if the partitions are recognized there the installer will know they exist during installation.

---

### Post by Phasmus on 2008-08-02
The 250 gb drive is an external usb drive.  I've now removed it for clarity's sake.  There is only the 1TB drive, partitioned as shown above, in this system.  I apologize for indicating otherwise earlier, with a drive that size it's easy to forget there's just one.  :)

As for what I want to do, it is just as you suggested.  I want to install Ubuntu over the old linux partition.  The problem is the partitioner isn't detecting the partitions.  In the attached screenshot you can see that the drives are mounted and their contents displayed, but gparted still (clearly erroneously) says the whole drive is unallocated.  The installer says the same thing, so I can't use it.  As far as the installer is concerned the whole drive is nothing but empty space for it to install over.  This is the problem I need to overcome.  I need the installer/partitioner to see my existing partitions.

---

### Post by redraiderbum on 2008-08-02
Wow that is amazing, I've never have seen gparted mess up but not the ubuntu installer partitioner.  Try this partitioner from the command line:

sudo cfdisk

If you can partition the 'linux' partition to ext3 it may help to at least detect that one for installation.  That is the best I can suggest.  It might be that the first partition is causing everything else to be detected incorrectly.

You didn't obliterate the master boot record right?

---

### Post by Phasmus on 2008-08-02
The MBR seems to be in working order, I still load Windows and the old broken Ubuntu via GRUB.  cfdisk detects the partitions correctly, though I'm a little hesitant to actually modify the contents of the disk with it at the moment.  

I have my data backed up, but operations on this disk can take a while and if something were to go awry it'd take too long to get everything running again.  I'd prefer to figure out what's throwing things off with the partitioner before trying any work-arounds that might exacerbate (for example) a glitchy boot-loader.  Having said that if nothing else turns up, I'll probably give cfdisk a try in a day or two, when up-time is less of a concern.

---

### Post by redraiderbum on 2008-08-02
If cfdisk works then the server installation disk should work.  At the moment I can't think of a way to fix the partitioner problem.  If your computer will boot to an external drive, you could install ubuntu to a thumbdrive.  Make sure if you do this you change the location of the grub boot loader installation to the usb drive.  The optional will come up after the system is installed.  If you do that then you could update the packages on the usb drive which might fix the partitioner problem.

---

### Post by Pumalite on 2008-08-02
Did you do md5sum on the iso, burn at 4x or less on a CD-R?

---

### Post by Phasmus on 2008-08-02
> **Pumalite said:**
> Did you do md5sum on the iso, burn at 4x or less on a CD-R?

Yes and yes (plus the cd's diagnostic checked out).  However, when I can get my hands on it, I'll use another cd which I am entirely sure installed correctly on another system to eliminate this possibility from the running.

---

### Post by Phasmus on 2008-08-06
Okay, we have a breakthrough!  This post:

[http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121)

lead me to the nature of my troubles, which were right under my nose all along.  If you look up at my fdisk output you will note that my extended swap partition is overlapping one of my NTFS partitions.

So that's the why (the how remains uncertain, NTFS was here first).  What is important now is what I can do to fix it.  It looks like the testdisk utility is the way to go but I remain somewhat concerned that tinkering with things will cause (recoverable with extreme tedium and irritation) data-loss.

I will report back when the modifications are complete (contingent more on when I have the guts to try it than logistics).  In the meantime, if anyone has any suggestions on the 'right' way to non-destructively untangle my partitions (the NTFS partition I need to keep, the extended/swap is expendable), I'd be happy to hear it.

---

### Post by Phasmus on 2008-08-06
Testdisk did the trick.  I just ran the 'analyze' operation, committed the suggested changes and restarted and then the partitioner worked fine.  My NTFS partitions full of data were undisturbed.

---

For anyone else wanting to try this solution, take note:  testdisk isn't installed on the Ubuntu live-cd.  However the program is fairly light-weight so if you enable the universe repository on a live-cd you can install it in the live environment.  That's what I did and it worked fine.  Note that other live/rescue cds do come with testdisk installed, but this solution is probably still faster if you already have an Ubuntu cd on hand.

---

Thanks for the advice everybody.  Case closed!

---

