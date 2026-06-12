---
title: "grub rescue&gt; remove winXP and install 10.10 (64bit)"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by kbrand on 2011-02-06
Reposted from "Absolute Beginner Talk"
<sorry, it was my first post, hopefully not my my last thus :)>

Dear New and Esteemed Ubuntu users,

Yet another-

error: no such device: e7be........
grub rescue>

However i failed to find any threads detailing simply how to install ubuntu 10.10 obliterating a previously installed WinXP.

It cant be so hard, but id really appreciate some tips getting past this error. Some details which will no doubt be needed to help any one with the patience to help me:

1. First attempt to install 10.10 (64bit) from USB went smoothly, until the inital restart and failure to boot into Ubuntu.
2. I fiddled around with the SCSI config utility thinking ubuntu was having trouble with the PERC 320/DC SCSI controller i was trying to install ubuntu onto (2x SCSI dives in RAID0 as XP was previously installed onto, and as ubtunu detected as a single drive (array?) in 1. above). Failure to boot into Ubuntu.
3. Repeated 1. above, failure to boot into Ubuntu.
4. At this point i got the error mesage:

error: no such device: e7be........
grub rescue>

and couldn't even boot from the USB-thumb drive

5. Burned a Ubuntu 10.10 (64bit) live-CD, but it also failed to boot fromt eh live-CD, and again yielded only the message:
error: no such device: e7be........
grub rescue>

6. At the grub rescue> prompt, ls returns:

(hd0) (hd0,msdos5) (hd1) (hd1,msdos1) (hd2) (hd3) (hd3,msdos5) (fd0)

7. System details:
-Dell Precision 670 with dual monitor video card
-PERC 320/DC SCSI controller with 2x maxtor SCSI drives attached
-XP was installed here (on the 2x SCSI's as RAID0)
-2x NTSF formatted SATA drives
-1x cd-rom drive
-1x floppy drive

I geuss the MBR is mixed up. But why i cant boot from USB or CD-ROM is perplexing. And an impasse to getting 10.10 up and running!!

Would very much appreciate suggestions poitners to recources to remove the XP scrouge from this system permanently and get ubuntu running sweet on the SCSI drives.

tia, Karl

---

### Post by kbrand on 2011-08-22
'solved' at:

[http://ubuntuforums.org/showthread.php?t=1682607](http://ubuntuforums.org/showthread.php?t=1682607)

---

