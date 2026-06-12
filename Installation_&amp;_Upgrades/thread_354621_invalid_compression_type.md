---
title: "invalid compression type"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by secretspicy15 on 2007-02-06
Ok, I have tried both version 6.06 and 6.10 and have been stopped at the same point with each. I insert the disc and reboot; the ubuntu menu screen comes up fine. I go down to check the cd for defects, it loads the linux kernal, and then when it goes to uncompress it it halts the system and says err(1) invalid compression type (or something to that extent). I have done checksums on both isos, and have used infra recorder to burn cds; after having trouble with the first cd i tried (6.06) i burnt another cd in case there was something wrong with the first one. This second cd gave me the same error. I then downloaded version 6.10 just to see what a new version and new iso file would do for me. It gives me the exact same problem.
Does anyone have any idea what this even means, and how I can fix it?

thanks,
TJ

---

### Post by apjone on 2007-02-06
try isorecord or a different iso burner,
Also burn at a lower speed.

---

### Post by secretspicy15 on 2007-02-06
Ok, I'll try that. It's quite feasible they were lousy burns; my CD-RW drive is kind of crappy.  I can browse the cds with windows though... I'll make a new CD; I may even borrow someone elses computer to do the burning just to make sure its not my lousy hardware.

---

### Post by secretspicy15 on 2007-02-06
Ok, I found the source of this problem. My CD-RW drive had slipped into PIO mode. I reinstalled the drivers and reburned. Everything went smoothly. I checked the disk for errors, and it was clean. However, when I went to do a live boot, I got a couple bugs. I haven't searched the forums yet, so I may be able to find an answer but i got the following:
b44:eth0: BUG! Timeout waiting for bit 000000002 of register 42c to clear.

...  a few lines of startup stuff, no bugs here ...

Bug: soft lockup detected on cpu #0

And then it stopped, and I had tor estart into windows (boo).  Any ideas here? (like I said i'm going to check the forums, i don't mean to post something thats already solved, i'm just giving an update)

Thanks again,
TJ

---

### Post by secretspicy15 on 2007-02-06
ok nevermind, everyhting is keen and peachy and wonderful, and now i can use ubuntu freely!! hooray!

---

### Post by apjone on 2007-02-07
great to hear

---

