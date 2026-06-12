---
title: "Windows 7 instantly bluescreens and reboots after using Ubuntu 10.04"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by nerr on 2010-08-02
Hey everyone, I installed Ubuntu 10.04 LTS x64 on my laptop about a month back and I have been very, very pleased with its maturity and stability. However, I have seem to have hit a snag with my ventures into desktop Linux: I also dual-boot Windows 7 Professional x64, and it seems that every time I run Ubuntu 10.04, Windows 7 will immediately bluescreen on boot, reboot, and then be fine. I'm not sure what kind of harm this could be doing to the system, but it strikes me as very odd, and it's something I would like to resolve.
 
I have suspected this may have to do with mounting NTFS drives under Ubuntu, because my Windows OS and all of my media is stored on NTFS partitions. Needless to say, I would really rather not change this, because NTFS seems to be one of the few filesystems with large-file-support that will run with ease under Windows and Linux.
 
I have tried removing my main Windows 7 OS partition from the fstab in Ubuntu to see if that made any difference, but the problem persists. Could a secondary NTFS media partition mounted in Ubuntu really cause these sort of issues? Thank you very much for your help!

---

### Post by nerr on 2010-08-04
Anyone?  I'd like to figure this out if at all possible.

---

### Post by Rubi1200 on 2010-08-04
Have you tried running the chkdsk utility in Windows?
 
[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

---

