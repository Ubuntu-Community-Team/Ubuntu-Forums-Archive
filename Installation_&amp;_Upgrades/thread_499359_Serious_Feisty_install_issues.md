---
title: "Serious Feisty install issues"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by ZephyrQ on 2007-07-12
The Feisty install CD is crashing all the time, sometimes at boot, most times while trying to manually partition.  I have to avoid the guided partition because, due to a inpatient user and thinking Gparted was safe (oops), there are 3 partitions I *cannot* change (/graphics, /home, /music (which is currently using Reiserfs).

I've tried playing with other drives (I have 3), and I completely wiped one (hdd) to take the whole Feisty install (using guided install--last resort), but the system locked up again during the partitioning.

I've done this in safe graphics mode, but the problem continues.

FYI, I tried installing CentOS, but got a similar problem during install (seems it doesn't see ReiserFS).

I'm stuck to using the liveCD (when I can get it to boot all the way...40% chance it doesn't).

Am I missing something simple?  or can I use the liveCD to backup the 3 directories to the unused drive (now formatted ext3) and wipe the big drive (60 gig-hda).

Any help will be appreciated!

---

### Post by Pumalite on 2007-07-12
Is better to use the Alternate CD Text Mode in all cases. Nevertheless if 256 RAM or less>Alternate Xubuntu CD. You need to post your specs. SATA drives, mixtures of SATA and IDE drives, Graphics Cards; they are all potential issues.

---

### Post by ZephyrQ on 2007-07-12
3 IDE drives, hda-60G; hdb-8G; hdd-30G

hda has 8 partitions (don't ask, I did this 3 years ago...), the last 3 of which (hda9, hda10, and hda11) can't be touched unless I can back them up (hda11 is biggest taking 19G)

hdb has two partitions, one of them swap, the other archives which can't be touched.

hdd I have wiped and made into just one partition.

NVidia graphics card, which is why I'm using the safe mode.

I'll try and download the alternate CD, but will the liveCD allow me to burn?  I can't seem to find the software

---

### Post by Pumalite on 2007-07-12
What do you have in your comp now? In any Linux you can use k3b>Tools>Burn CD Image>Location of iso>Burn. In windows: Nero or ImgBurn. Have to burn iso as IMAGE. I don't know how to burn iso in Live CD. Maybe somebody else does. In general is not necessary to format with Gparted before install, but maybe in your case it could help you. Boot Gparted>Make one large partition of hdd>Format ext3. Then install with Alternate CD.

---

### Post by ZephyrQ on 2007-07-12
I'm running off the liveCD.  The drives I mentioned are now blank except for the ones I stated didn't/couldn't be touched.

I tried to install a burner...it seems to be working, so I'll try to download the alternate cd before the weather turns bad (slow DSL...).

I appreciate your time. 



~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	What do you have in your comp now? In any Linux you can use k3b>Tools>Burn CD Image>Location of iso>Burn. In windows: Nero or ImgBurn. Have to burn iso as IMAGE. I don't know how to burn iso in Live CD. Maybe somebody else does.

---

