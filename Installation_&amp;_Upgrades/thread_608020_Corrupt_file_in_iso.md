---
title: "Corrupt file in iso?"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by djm-uk on 2007-11-09
Is it possible that there is a corrupt file in the ISO image ubuntu-7.10-desktop-i386.iso? The ISO MD5 sum is correct but the 'cd integrity checker' reports 1 corrupt file on 2 separate burns one to CDR at 8x & one to CDRW at 10x - pity it doesn't tell me which file is corrupt!  I have just burnt the 6.06.1 image to the SAME CDRW and it checks out OK so I am trying to install that.

The Install of 7.1 fails with an I/O error. When I look at the logs it is a 'SQUASHFS' error but it only gives a block number & not a file name.... It looks like a corrupt file rather than unable to read the data (although that doesn't eliminate a bad burn)...

I am going to try the 7.1 alternate desktop next as the machine only has 384MB of RAM & shared memory graphics...

---

### Post by djm-uk on 2007-11-09
On a hunch I checked the file \casper\filesystem.squashfs on a recorded CD & the MD5 doesn't match that in the MD5SUM.txt file. I don't have the ability to read the ISO directly...

David

Later... Found a utility to open the ISO & Lo the file is OK in there so it is a bad burn....

---

### Post by dabl on 2007-11-09
You need to slow it down to 4X for best chance at a good burn.  "Check CD For Defects" sometimes gives a "false negative" -- you can't trust it 100%.

Don't bother with CD-RW -- won't work at any speed.

:popcorn:

---

### Post by ajgreeny on 2007-11-09
I have burned several isos using CD-RW without any problem.  I've also even burned an iso CD image on to a DVD-RW without any problems, though you can't do it direct by double clicking the iso, as that then assumes you have a blank CD in the drive.  k3b will do it though if you use the "Burn DVD iso image" on the welcome page.  Never yet had a problem burning an iso in any way, but it is a new drive and perhaps I'm just lucky.

---

### Post by Pumalite on 2007-11-09
A good quality CD-R is not so expensive.

---

### Post by ajgreeny on 2007-11-10
Yes, I agree, but I was simply refuting the comment that CD-RWs never work, as I know that they do!

---

### Post by Pumalite on 2007-11-10
Hi:
I appreciate your comment. I actually have never tried because I don't trust them, but I think I'll try one and see.

---

