---
title: "GRUB install failed - fresh OS install"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by jameswm on 2011-11-19
I had it with Windows 7. I bought my Lenovo B575 about 4 months ago and I've had to restore the OS 3 times. This last time I went into an irreparable reboot loop, I decided it's time for Linux. 

I tried 11.10 on a disc. File copy error. I tried 11.10 on USB. File copy error. So I tried 11.04 on USB, this time it said "GRUB install failed" and then the install launcher crashed. I downloaded another copy of 11.04 (same copy) and tried again from USB. Same results. I'm on a FRESH hard drive. Totally wiped. What the HELL could I POSSIBLY be doing wrong?

---

### Post by darkod on 2011-11-19
Did you try running 11.10 or 11.04 in live mode first (the option Try Ubuntu)? Not that it matters much but it's better to see if it runs OK in live mode first.

---

### Post by coffeecat on 2011-11-19
That is a run of bad luck - sorry to hear it. Clutching at straws here, but...

> **jameswm said:**
>  I bought my Lenovo B575 about 4 months ago

...

I'm on a FRESH hard drive.

Do you mean the 4 month old drive, or an unused new one? Whichever, new drives do sometimes fail, and this one could have too many bad sectors. Boot into the live Ubuntu session and open Disk Utility. Look for SMART data and do the SMART self-tests.

Also - to get a corrupted download three times running would be extremely unlikely, but did you [check the md5 hashes](https://help.ubuntu.com/community/HowToMD5SUM)?

---

### Post by jameswm on 2011-11-19
After burning about three 11.04 discs, one FINALLY worked. I wrote them each at lowest speed, too. Geeez. Talk about a string of crappy luck. lmao
Thanks anyway, fellas

---

### Post by jameswm on 2011-11-19
New problem. 
-_- It says that my system can't run Unity?? (64bit)
If I downgrade to 32bit, would I be able to?

Lenovo B575 stock specs
AMD E-350 dual core 1.6ghz
AMD 6310 graphics
4gb ram
15.6" display (1366x768)
HDMI
E-sata
320gb drive

---

### Post by coffeecat on 2011-11-20
No - 64/32 bit wouldn't make any difference. 

Your AMD 6310 is a relatively newer GPU which was released about a year ago. It could be that the default open source driver in 11.04 is not able to support 3d acceleration in that GPU. Two suggestions. Once you have installed, try installing the proprietary fglrx driver. Or - and I know you've had problems burning an ISO - try to get 11.10 working on a CD. The ati open source driver in 11.10 is a later version than in 11.04 and may work better with that card.

---

### Post by jameswm on 2011-11-20
> **coffeecat said:**
> No - 64/32 bit wouldn't make any difference. 

Your AMD 6310 is a relatively newer GPU which was released about a year ago. It could be that the default open source driver in 11.04 is not able to support 3d acceleration in that GPU. Two suggestions. Once you have installed, try installing the proprietary fglrx driver. Or - and I know you've had problems burning an ISO - try to get 11.10 working on a CD. The ati open source driver in 11.10 is a later version than in 11.04 and may work better with that card.

I updated to 11.10 through classic mode on 11.04. Unity works fine now. :)

---

### Post by jameswm on 2011-11-20
Also, how rude of me. Thank you all for your time!

---

