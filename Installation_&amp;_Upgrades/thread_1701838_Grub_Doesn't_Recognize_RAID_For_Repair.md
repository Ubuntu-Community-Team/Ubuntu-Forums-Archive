---
title: "Grub Doesn't Recognize RAID For Repair"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by FireDemonSiC on 2011-03-07
Yet another problem.

Last night I upgraded my 10.04 install to 10.10 and guess what?  It broke the boot loader.  Grub falls to a recovery shell at boot so at the moment I have NO OPERATING SYSTEM.

No problem I can fix that with the LiveCD.

So I popped in the live CD, installed kpartx so I can properly read my RAID array and verify this in gparted.  4 Linux partitions and two Windows so we should be good to go.

> ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,3)
root (hd0,3)

Error 22: No such partition
grub> root (hd0)
root (hd0)
grub> root (hd1)
root (hd1)
grub> root (hd2)        
root (hd2)
grub> root (hd3)
root (hd3)
grub> 


As you can see, grub isn't reading the RAID array.  It's still recognizing 4 individual drives.  How do I correct this?



I must say, for a Linux distro that is intended for beginners this one has given me THE MOST trouble out of all the distros I've tried.  This all started with a network connection that sopped working by itself and kept progressing from there.  Each time I try to fix a problem, I have to find a fix for the solution.  I feel like I'm watching inception.

---

