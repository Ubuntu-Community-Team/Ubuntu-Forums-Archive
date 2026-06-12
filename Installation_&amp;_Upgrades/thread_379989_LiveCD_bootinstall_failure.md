---
title: "LiveCD boot/install failure"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by explemonk on 2007-03-09
Hello,

I got 6.10 installed on a machine at work and like what I see, and I am attempting to dual-boot my laptop as I make a full transition to Linux.  However, I cannot for the life of me to get the LiveCD (i386 and AMD64 both) to boot.  I have gotten to the menu and turned off the splash quick options, and as near as I can tell the DVD drive is failing to be mounted by the kernel.

The message at the point where the boot hangs is as follows:

[number] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[number] Uniform CD-ROM driver Revision: 3.20
[number] hdc: irq timeout: status=0xd0 { Busy }
[number] ide: failed opcode was: unknown
[number] hdc: DMA disabled

I have tried burning new CDs, I've pored over the forums and cannot seem to find an answer.

I was able to succesfully boot a Feisty Herd 5 LiveCD with no issues.

My basic computer specs are as follows:

Compaq Presario R4000 series
AMD Athon64 3200+
1.25GB RAM
ATI Radeon Xpress 200M

Any help would be greatly appreciated.

---

### Post by mikewhatever on 2007-03-09
Looks like hardware incompatibility. I think your best shot is to wait for the stable version of Feisty, or install and use the unstable one meanwhile.

---

### Post by wpshooter on 2007-03-09
Try the ALTERNATE (text based) version(s).

---

### Post by explemonk on 2007-03-09
I hope it's not hardware incompatibility; there are a few different threads on the forums about people who have installed on my same laptop model, so I assume that I should be able to do so as well.  I will give the alternate CD a shot.

---

### Post by rsambuca on 2007-03-09
Try entering the boot option```
ide=nodma
```

---

### Post by explemonk on 2007-03-09
> **rsambuca said:**
> Try entering the boot option```
ide=nodma
```

That did the trick!  Thanks so much!

---

### Post by rsambuca on 2007-03-09
Apparently the DMA thing is a problem with some chipsets.  After you have the liveCD up and running, you will probably want to turn dma back on (Direct Memory Acces) for all of your IDE drives.  If you leave dma off, your machine will be much slower, especially if you are going to install it on your hard drive.

To turn dma back on, open a terminal from the top menu bar (Applications -> Accessories -> Terminal)

At the prompt, you will want to enter the following command```
sudo hdparm -d1 /dev/hda
```
You will want to do this for each ide drive you have. ie /dev/hda, /dev/hdb, /dev/hdc, etc.

---

### Post by explemonk on 2007-03-10
> **rsambuca said:**
> Apparently the DMA thing is a problem with some chipsets.  After you have the liveCD up and running, you will probably want to turn dma back on (Direct Memory Acces) for all of your IDE drives.  If you leave dma off, your machine will be much slower, especially if you are going to install it on your hard drive.

To turn dma back on, open a terminal from the top menu bar (Applications -> Accessories -> Terminal)

At the prompt, you will want to enter the following command```
sudo hdparm -d1 /dev/hda
```
You will want to do this for each ide drive you have. ie /dev/hda, /dev/hdb, /dev/hdc, etc.

Thanks for the help.  After reading up on partitioning and getting that done, I'm running the install process now.  Looking forward to making the transition from Windows.

---

