---
title: "[SOLVED] 7.10 stops during installation"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Bix in Austin on 2008-04-15
I am trying to install 7.10 on my IBM 600x laptop. I get the following message when it stops: [334.431932] Code: Bad EIP value.
[334.432058] EIP: [<00000000>] 0x0 SS:ESP 0068: c9bada74
[334.432193] Kernel Panic - not syncing: Fatal exception in interrupt

I don't have a clue what this means. From what I have been reading about this install it should not be a problem. I have W2k pro installed on the laptop and planned to run it dual boot. I got it to do this when I ran Ubuntu off the CD. I used Partition magic to format the partition with EX2 file system. I had Win 98 on the laptop in a dual boot setup. I formatted the partition that the Win 98 was on since I don't use at all. What am I doing wrong?

---

### Post by Partyboi2 on 2008-04-16
Try runnung a memory test (memtest( its one of the options on the live cd).
Another possible thing to try is to add ide=nodma as a boot option, to do this press F6 when you are at the ubuntu main menu screen and at the end of the line add ```
ide=nodma
``` then press enter.

Edit: Also what are your system specs?

---

