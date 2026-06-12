---
title: "problems with installing Hardy from Alternate CD."
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-04-27
I am having various problems including the grub not wanting to install to the hard drive when attempting to install Hardy from the Alternate CD.

I wonder if there is a possibility that I might have better success by trying to install from the Live CD ?

Thanks.

---

### Post by wpshooter on 2008-04-27
Well to answer my own question, switching to the Live CD does not seem to help.  As a matter of fact, the Live CD version has seemed to exhibit more problems than even the Alternate CD version.

IMHO, Hardy should not have been released at this point !!!  

I sure hope that there is going to be a revised implementation of the final release of Hardy.

Again, IMO, Ubuntu is not doing itself any favors in releasing its O/S when it has this many major bugs (even in the installation of the O/S itself) remaining.

Thanks.

P. S. - It appears that none of the bugs that I have reported while testing this O/S (Hardy) over the last several months have been fixed as of the final release.

---

### Post by punkybouy on 2008-04-27
Can you give us some more background?  Is this a clean install or an upgrade?  I used the alternate cd yesterday on a laptop hard drive that already had a Windows OS on it.   The alternate cd wiped out the partition and setup a new one with an encrypted LVM and I had no issues.
Were you trying to set up Hardy as a second OS/

---

### Post by wpshooter on 2008-04-27
> **punkybouy said:**
> Can you give us some more background?  Is this a clean install or an upgrade?  I used the alternate cd yesterday on a laptop hard drive that already had a Windows OS on it.   The alternate cd wiped out the partition and setup a new one with an encrypted LVM and I had no issues.
Were you trying to set up Hardy as a second OS/

No, not upgrade.

Clean install from scratch after WIPING drive completely clean on both Live and Alternate CDs.

For instance, when trying with the Live CD, when the installation gets to the end and gives message about needing to restart the system, it says nothing about needing to take the CD out of the machine, it just says machine needs to restart in order to use Ubuntu and then afterwards it just ejects the CD on its own accord and says nothing about closing the CD tray and then it goes to a blank/blank screen and NEVER does restart.  Have to manually turn the machine off and back on, at which point it does go into the Ubuntu desktop.  After this when I try to open the Login preferences screen it takes about 4 minutes for the login preferences to open and no it never took it that long to open under any of the prior versions of Ubuntu.  And there are many, many other problems with this release of this O/S to numerous for me to describe in detail here.

Back to Gutsy for now !!!

Thanks.

---

### Post by wcorey on 2008-04-27
> **punkybouy said:**
> Can you give us some more background?  Is this a clean install or an upgrade?  I used the alternate cd yesterday on a laptop hard drive that already had a Windows OS on it.   The alternate cd wiped out the partition and setup a new one with an encrypted LVM and I had no issues.
Were you trying to set up Hardy as a second OS/

Please refer to my post as well, under [ubuntu] 8.04 not ready yet?  in the install and upgrade forum.

I, too, have several issues with this install, especially the LVM piece of it. I, too, submitted bugs early on in beta of 8.04 that were not addressed. If you could detail your experiences, esp with the LVM install, I, for one, would appreciate it. 

I just answered one of my questions. While the LVDisplay shows 465+ GB in the logical volume the df command was correct that only what's available on the first PV is 'available'. Why is the second PV being ignored? I believe only the first volume was built in the fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/cor720-root
UUID=1484d5c4-baa1-4520-a443-de92282cb1f9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=73da84e4-e2f7-4855-a206-28e256177864 /boot           ext3    relatime        0       2
# /dev/mapper/cor720-swap_1
UUID=bbaa7c3c-c1a4-477e-a6f3-69a2ec756972 none            swap    sw              0       0

Here is the lvdisplay

  --- Logical volume ---
  LV Name                /dev/cor720/root
  VG Name                cor720
  LV UUID                g2Jod5-ZqxW-U5Ju-TS7B-QJG5-yIUP-v68cJJ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                456.56 GB
  Current LE             116880
  Segments               2
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0

I just noticed the UUID is different between the lvdisplay and fstab. Could the fstab have been constructed incorrectly at build time??????

SO I played with this. Using the disk usage analyser with the original fstab uuid it shows 444GB total, hmmm, really close to 465 from the pvscan and 456 from the lvdisplay yet df showed 232GB total. Using the uuid shown in the lvdisplay disk utilization analyser shows 222GB total. I am very confused here.

Mine also was a clean install.

Thanks,
Walt

---

