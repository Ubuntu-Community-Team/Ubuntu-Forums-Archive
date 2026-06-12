---
title: "How do I install ubuntu on a hard drive with no OS"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by Odin888 on 2010-06-11
Hi all. We have been really enjoying or Linux experience (installed Ubuntu last year). Our drive died on us...11 years old!! Well I thought I could install a new blank (no OS or any files) hard drive in and use disk at boot. Yikes, Ubuntu will not install. Unplugged my other 2 hard drives and set cd drive as slave. At start up the initial installation with Ubuntu 10.04 The initial start up language question pops up after hitting enter Ubuntu screen with loading dots show loading. Nothing loads up. I tried Ubuntu 9.10. It loaded up to the partition step. There was an error message saying "No root file system is defined" "Please correct this from the partitioning menu." Which meant squat to me. I exited out of install and ran Ubuntu from disk. I tried using Gpart and Disk utility, but new hard drive was not seen..... 

Thank you

---

### Post by arrange on 2010-06-11
[COLOR="Silver"]There was an error message saying "No root file system is defined"[/COLOR]
Were you doing manual or automatic partitioning?

---

### Post by dandnsmith on 2010-06-11
First check if the BIOS is 'seeing' the new HDD - it sounds as if it may not be, as otherwise gparted should at least show the drive, even if it hasn't been partitioned.

If the BIOS doesn't see the drive, then -
what is the new HDD (size and type)?
how old is your system?

---

### Post by Odin888 on 2010-06-12
Thanks for getting back so fast. I will have to check all on Sunday. System is older. I toasted my first hard drive a number of years ago. and installed the current older one. The system was built 6-7 years ago. The new Hard Drive is a Samsung 80G. It is dated 2005. Has not been used much. Am thinking of buying a new IDE drive...

---

### Post by Odin888 on 2010-06-12
> **arrange said:**
> [COLOR="Silver"]There was an error message saying "No root file system is defined"[/COLOR]
Were you doing manual or automatic partitioning?
Automatic. I have no idea how to do it manually...

Thanks for being so quick getting back to us.

---

### Post by oldfred on 2010-06-12
You may have to learn to partition in advance and use manual install.

If the BIOS is that old you may have to have the boot files at the beginning of the hard drive.

Herman's MBR page
[http://members.iinet.net.au/~herman546/p6.html](http://members.iinet.net.au/~herman546/p6.html)
Separate /boot and BIOS limits
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

If you put the full install in a 10-20GB partition at the beginning of the drive it may be the same as having a /boot at the beginning. But then to use the space you will need a separate /home for the rest of the drive (except swap).

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

IF you create partitions in advance then you use manual install and tell it which partition to use for / (root) and what format (ext3 or ext4), which is /home and format (if existing with data do not reformat), it finds swap on its own.

---

