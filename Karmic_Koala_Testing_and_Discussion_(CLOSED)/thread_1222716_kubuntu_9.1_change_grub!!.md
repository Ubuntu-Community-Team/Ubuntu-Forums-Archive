---
title: "kubuntu 9.1 change grub!!"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hananias on 2009-07-25
I use to dual boot kubuntu 9.04 with ipcos x (hackintosh).  Well, after I did a fresh install of the alpha beta 3, I lost the settings in grub (i know).  I know how to change grub in the old kubuntu(ubuntu, etc).  open  "/boot/grub/menu.lst" as root, place your new settings:

title iPCOSx
root (hd0,0)
chainloader +1
makeactive
 
that`s it!  But now, grub completely changed!  I didn`t read the release notes... actually I didn`t read anything!  I didn`t expect something that`s been so constant and easy to use... to CHANGED!:confused:

 "If it aint broke, dont fix it!"

Any help I`ll appreciated!!!  I really need to get back to OSX.  If not I`m left with the option to erase and downgrade.  (but I don`t want to do that, I love the new look).

---

### Post by SuperSonic4 on 2009-07-25
Is iPCOSx the first partition on the first hdd? Can you post the output of  ```
sudo fdisk -l
``` and indicate which one is OS X

edit: you should be careful with development versions as some members may expect you to know how to solve your own problems

---

### Post by ELD on 2009-07-25
Before you start messing around with development versions you should AT LEAST read up on it a bit.

---

### Post by hananias on 2009-07-25
wow! thanks for the quick replies!!!:D
Yes osx86 is my main partition. (hd 0,0) I think...
I`m sorry post such a demanding question.:(
I just did it, in case there`s some one who had a similar problem (even if its with windows, or another os)... But if there is no experience on this, then I`ll just downgrade.  What do you all think???  like I said up top, I like to keep kubuntu beta.  

Well here`s my fdisk output :

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00035577

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55451   445410126   af  HFS / HFS+
/dev/sda2           55452       60801    42973875    5  Extended
/dev/sda5           55452       60801    42973843+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312571192+  af  HFS / HFS+

Disk /dev/sdc: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00061492

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         983     7895916    7  HPFS/NTFS

---

### Post by BwackNinja on 2009-07-25
I'd try doing a 'sudo update-grub2' which should call os-prober and find your OSX.

---

### Post by ranch hand on 2009-07-25
The 2 on the end of grub is not needed.

sudo update-grub

will do the job.

---

### Post by tad1073 on 2009-07-25
pull down all the updates for alpha 3, there is an update to grub that fixes the issue, atleast with windows anyways.

---

