---
title: "Help with step 2 of install"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by Narcoleptic_Insomniac on 2006-08-28
I'm not sure if im doing anything wrong but when I try to install and get to step 2, select my city, I zoom in on my city (Halifax, Nova Scotia) and then it wont let me do anything. I can move my mouse around and stuff but it wont let me click anything. Whats going on?

---

### Post by Narcoleptic_Insomniac on 2006-08-28
bump

---

### Post by aysiu on 2006-08-28
How much RAM does your computer have? 128 MB? 256 MB?

---

### Post by Narcoleptic_Insomniac on 2006-08-28
I'm not sure, how do I find out

---

### Post by aysiu on 2006-08-28
When you're running the live CD, go to Applications > Accessories > Terminal and type ```
top
``` There should be (on the second or third line) some information about how much memory you have.

---

### Post by Narcoleptic_Insomniac on 2006-08-28
I have 156 of ram.

---

### Post by aysiu on 2006-08-28
Yeah, that's a bit light and would explain the freezing. I would advise using the **Alternate CD** instead of the **Desktop CD**.

Great tutorial on the Alternate CD right here:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by jdr00ejr on 2006-08-28
I'm having the exact same problem with 256mb of Ram...any ideas for me?

Thanks.

---

### Post by aysiu on 2006-08-28
> **jdr00ejr said:**
> I'm having the exact same problem with 256mb of Ram...any ideas for me?

Thanks.
I've never used 256 MB of RAM for a Ubuntu installation, so I don't know. Freeze-ups generally occur for one or more of several reasons:

1. The disk is corrupt (either the ISO corrupted during download or corrupted on burn to CD). If you think this might be the case, try doing a checksum and burning at a low speed following these instructions: [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

2. Something's wrong with your hardware--your CD-ROM drive, faulty RAM, whatever.

3. You just don't have enough RAM, so it freezes up because it's true to run a fully functional live session *and* install Ubuntu at the same time. I would recommend this for only 512 MB of RAM or above. I think it can be done at 256 MB, but I'm not sure. If you don't have enough RAM, use the Alternate CD.

---

### Post by jdr00ejr on 2006-08-28
The LiveCD I'm using is an original.  It says a minimum of 256mb Ram.  I understand what you are saying about running the OS and installing at the same time though.  I'll research this Alternate CD stuff I keep reading.  My biggest killer is dial-up...so I can't download these huge files...which I suspect the Alternate CD is.

---

### Post by aysiu on 2006-08-28
Based on what I've seen on these forums, a Desktop CD being shipped from Canonical doesn't guarantee it's not corrupt. It may have been burned at a high speed. Do you have several CDs? Have you tried a different one?

The Alternate CD is huge for dial-up (I believe it's just shy of 700 MB). If you are going to download it over dial-up, I would advise using BitTorrent--you're more likely to get an uncorrupted ISO.

---

### Post by jdr00ejr on 2006-08-28
I only have the 1 CD...though I've requested another one be mailed.  I have used this CD to install on another machine (Dell Laptop with 512mb Ram) and it installed just fine.  Just hanging on the Desktop.  Someone suggested Ctrl+C to bypass the step it's hanging on and see what happens...so I'll try that tonight.  700mb is a lot for a dial up connection.  I have Broadband at work...but it's monitored on MB usage.

Thanks for the info.

---

### Post by aysiu on 2006-08-28
If that CD worked for another machine with 512 MB of RAM, I'd say it's the 256 MB that's holding you up.

---

