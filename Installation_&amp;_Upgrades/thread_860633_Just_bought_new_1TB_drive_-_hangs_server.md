---
title: "Just bought new 1TB drive - hangs server"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by keymoo on 2008-07-15
Hi there,

I have an Abit NF7-S V2.0 motherboard and have just purchased and tried to install a SAMSUNG HD103UJ 1TB hard disk into it. When I power up the PC it gets to a screen which looks like this:

```
SiI 3112A SATARaid BIOS Version 4.2.47
Press F4 to enter RAID Utility
1 SAMSUNG HD103UJ

```and then doesn't get any further. With my old drive the screen looked like this:

```
SiI 3112A SATARaid BIOS Version 4.2.47
Press F4 to enter RAID Utility
1 <MY_OLD_DRIVE_ID>  464000
```and it then proceeded to boot linux.

**Solutions tried so far:**
I went to the samsung site and downloaded their ESTOOL.EXE but the problem is the system cannot get past the above screen to boot into the tool.
I tried plugging the HD into a different SATA socket on the mobo, but same prob.
I plugged in the old drive using the same cable and all works fine.

Any ideas?

Thanks

---

### Post by axela on 2008-07-25
You can try to upgrade your bios using the files from this forum: [http://www.nforcershq.com/forum/uber-trats-bios-1013-for-a7n8x-e-deluxe-with-4283-sata-vt69351.html]("http://www.nforcershq.com/forum/uber-trats-bios-1013-for-a7n8x-e-deluxe-with-4283-sata-vt69351.html")

Or you can go to [www.samsung.com](www.samsung.com) and download a program to force the hd in sata v1.5 mode instead of 3.0 (but you have to install the hd in a pc with a different motherboard and with windows installed to launch the program).

I upgraded the bios and all is working now! :)

---

### Post by GrfyGrumpyBear on 2008-11-21
You've undoubtedly solved this problem by now, but perhaps I can offer some help for anybody else searching for solutions.

This drive ships in SATA 2 mode. (UDMA mode 300, 3gbps) The SiL3112A controller card only supports SATA 1 (UDMA mode 150, 1.5gbps)

I found that even by lowering the UDMA mode of the drive (using ES-Tool) to 150, it still won't get picked up by the SiL3112A. (But it _will_ get picked up by other controllers - this is what I was using the SiL3122A for. Long story. ;) )

However, I was able to use the SiL3112A with ES-Tool to modify the drive settings, and here's the trick I stumbled across for getting past the hang-on-boot-detection problem:

Disconnect drive.
Boot, wait for DOS prompt.
Connect drive.
Start ESTOOL, wait for autodetection.

At that point, the controllers and drives will be scanned again, and ES-Tool will allow you to tinker with the drive.

I could get the drive to be detected by setting the maximum size the drive will report down from 953869MB to something smaller, but this probably isn't a good idea. :) Interesting, nevertheless.

---

