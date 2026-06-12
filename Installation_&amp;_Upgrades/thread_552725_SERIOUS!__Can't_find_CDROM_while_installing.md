---
title: "SERIOUS!  Can't find CDROM while installing"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by tipiglen on 2007-09-16
I have 3 cd's , two 'live' and one 'alternate' and all checksums are in order.  The two 'live' ones give repeated i/o errors on hdc, and eventually bomb out to a nearly useless busybox terminal.  The 'alternate' one gets through the language, keyboard, and filesystem mount and then can't find the very drive it's been reading from.

It says the cd-rom couldn't be mounted, probably because it wasn't in the drive (IT WAS!)  AGAIN AND AGAIN AND AGAIN AND AGAIN!

I have tried all sorts of changes in bios and boot options (f6), and nothing works.  Somehow, (I can't remember how) I did get it through to writing a bootloader, but it couldn't do that, either on the MBR or any other partition.  I tried both grub and lilo, and eventually decided to let it finish without a bootloader - BAD IDEA!

Now I can't get winxp to boot, or anything!  I have four partitions, one NTFS for windoze, one ext3 where I had gnewsense, the linux-swap, and a fat32 to share between windoze and gnewsense, and it all worked, but I wanted ubuntu (still do!)  The same setup is working fine on an old box which I'm using to write this hoooowwwwwllll!

An examination of syslog shows the cdrom reporting 'busy' and 'tray open', and it does sound busy (hunting for itself), but the tray ain't open!  

Fujitsu-siemens AmiloD Intel pentium 4 (two of them) 538
512 MB RAM 
Fujitsu MHT2080AT HDD, 80 GB, s.m.a.r.t supported
NEC DVD+/-RW ND-6500A  

Any ideas?  I have spent HOURS and HOURS on this!

Apologies for SHOUTING, but I'm going crazy.  :mad:

In desperation,
ed

---

### Post by Pumalite on 2007-09-16
Can you expand on this: Fujitsu-siemens AmiloD Intel pentium 4 (two of them) 538?

---

### Post by tipiglen on 2007-09-16
I think it's got two processors, both p4
32.GHz clock speed

Only one shows in BIOS setup, and I can't get much other information.  It's almost three years old and a good laptop.  Was wiorking fine as double-boot windoze/GnewSense...

Grrrr!
ed

---

### Post by Pumalite on 2007-09-16
In some BIOS>IDE Configuration>Set to 'Enhanced support for PATA+SATA
If not, then set your CD drive to 2nd Master in computer and 'Auto' in BIOS

---

### Post by tipiglen on 2007-09-16
CDROM is second master in BIOS, and set as Auto

thanks for trying to help
ed

---

### Post by Pumalite on 2007-09-16
Have you tried booting something else in your CD drive? (XP, Gparted?)

---

### Post by tipiglen on 2007-09-16
XP recovery disk works fine, but the recovery console hasn't the power I need to backup essential files, and I didn't do the change of permissions and haven't a clue what the admin password might be.  It ain't God, Jehova, boss, etc.  Haven't tried YWHW....

Don't have Gparted on disk, but xp recovery console shows partitions in place.

Other disks seem to work, but there's no OS to really tell...

Thanks.  Do keep trying suggestions, cause I'm dried out.

ed

---

### Post by Pumalite on 2007-09-16
Get Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
And rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And checkout your system.

---

### Post by tipiglen on 2007-09-16
Have supergrub, but burned on a vista machine, and just gives 'disk error - press any key to restart'  Will try rescue cd in the morning (it's ten to 4 AM here!)

I'll burn them using something non-windoze...

Thanks again.  I'll probably be back ;-(
ed

---

### Post by Pumalite on 2007-09-16
OK. Sleep tight.

---

### Post by tipiglen on 2007-09-20
Pumalite,

Just to thank you for the suggestions.  Rescue disk did the trick.  

Saved all my files with midnight commander, Then I was able to reinstall windoze from it's recovery disc (oem), and I knew then why I was trying to get out of gatesware!

Recopied my old files over the re-installed rubbish and got my system back.
(particularly "documents and settings", "program Files", and "Windows" directories)

Back to recovery disk and re-formatted partitions in readiness for Ubuntu one ext3, one share, and one fat32 to share stuff for firefox and thunderbird, etc, so the profiles, downloads, etc are available to both ubuntu and windoze.....

downloaded a fresh image of feisty 7.04 (alternate) and the install was smooth as butter!  Now have wlan and eth working and all's right with my world!

Now, how was it somebody suggested to enable root-type access to the windoze recovery console before it was needed?

Namaste/Salaam/Shalom/Shanthi/Dorood/Peace
ed

sleeping in the trees
aitchttp://tipiglen.blogspot.com

---

### Post by Pumalite on 2007-09-20
You are welcome. Glad you got it all worked out. Come back any time. Good luck.

---

