---
title: "Ubuntu hangs after install on Asus motherboard"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by arava on 2006-10-07
Hi everyone:

I am trying to install the Ubuntu 6.06 LAMP server and cannot get past Ubuntu hanging after the first reboot.

I'm using an old Asus P2B motherboard. I've tried another machine (similar motherboard) with the same results. Various versions of Red Hat, Fedora and Windows work quite happily on these machines. So it is not the hardware and has to be something that I have not configured correctly in Ubuntu.

I've tried installing the same Ubuntu server disk on a P4 (Intel motherboard) and it does not have this problem.
```
Sep 25 04:13:59 ubuntu kernel: [ 46.513268] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Sep 25 04:13:59 ubuntu kernel: [ 46.513300] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Sep 25 04:13:59 ubuntu kernel: [ 46.513320] ide: failed opcode was: unknown
Sep 25 04:13:59 ubuntu kernel: [ 46.513337] end_request: I/O error, dev hdc, sector 1430336
Sep 25 04:13:59 ubuntu kernel: [ 46.513358] Buffer I/O error on device hdc, logical block 178792
```
I'm guessing from the error messages that there is a problem with the IDE driver not working with something on this family of ASUS motherboards.

My second machine with the same problem has a P2L97 motherboard. Both the P2B and P2L97 have PIIX4 chips.

Can someone please explain what the following errors mean.
```
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05
hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: status=0x84 {DriveStatusError BadCRC}
```

I think that hda is my IDE hard disk and hdc is the CD drive.
Where can I find some information on these error codes and how do I fix them?

As I was trying to install a web server, I posted this question with detailed information and a screen photograph on the 'Server talk' forum.
[http://www.ubuntuforums.org/showthread.php?t=264705](http://www.ubuntuforums.org/showthread.php?t=264705)

I've also tried the beginner forum [http://ubuntuforums.org/showthread.php?t=267949](http://ubuntuforums.org/showthread.php?t=267949) without luck. Hopefully someone here can be kind enough to point me in the right direction as to where I should look to find the solution for this problem. It doesn't seem right to me that Ubuntu cannot work on an Asus motherboard.

I was hoping to use Ubuntu as a LAMP server because I was impressed with the how good the desktop version looked and ran off the Live CD.

Any help is appreciated.

---

