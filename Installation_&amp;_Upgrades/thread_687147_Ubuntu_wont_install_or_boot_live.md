---
title: "Ubuntu wont install or boot live?"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by winblows.exe on 2008-02-04
I downloaded the Ubuntu Live CD and burned it to disc. Now when I try to install it or boot live, it wont work. I get a bunch of errors showing....

hda: error code: 0x70
sense_key: 0x03 asc:0x02 ascq:0x00
buffer I/O error on device hda, logical block 296595
squashfs error:unable to read page, block240f965b, size 9453


Any ideas with whats going on here?

---

### Post by winblows.exe on 2008-02-04
anyone??

---

### Post by justsomedude on 2008-02-04
Probably a bad burn.

First, make sure the .iso file downloaded without errors:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) (scroll down to MD5SUM on Windows)

Then, burn the .iso file as slowly as possible and select the option 'Check CD for Defects' at the CD  menu. It should check with no errors.


If the CD checks with zero errors and still doesn't boot, we could try different boot parameters but do the CD check first.

---

### Post by winblows.exe on 2008-02-04
The .iso is fine. I should've  noted that I have done that already.

---

### Post by justsomedude on 2008-02-04
And did you do the 'Check CD for Defects' at boot, too?

Also, is it possible there is a system hibernating on the drive?

---

### Post by winblows.exe on 2008-02-04
Yeah, I tried everything. No system hibernating on the drive neither. Thanks for the help. Any other suggestions?

---

### Post by Niteowler on 2008-02-04
It could be that your cd rom drive is not being mounted.  Your problem sounds very similar to mine.  I've tried many linux versions with no luck.  Live cd's lock up or give errors and won't install, even alternate install cd's.  After many "hdc:drive not ready for command" and "buffer I/O error on device hdc" errors, I've came to the conclusion that my cd rom is my problem.  Haven't figured out how to fix it yet but I just posted the problem and I'm waiting on some help hopefully.  If I find out I'll repost here.

---

