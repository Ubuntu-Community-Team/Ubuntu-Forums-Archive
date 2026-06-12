---
title: "Install problems on SATA+IDE AMD64 system, please help!"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by mobgame on 2007-06-18
Hi, I've try lot of times to install ubuntu 7.04 i386 version into my system. it's does't work still.
My system configuration list below:
AMD64 3000+
Gigabyte K8N SLI(NForce4 platform)
Maxtor 160G SATAII
Segate 120G IDE
NVidia GF4 6600GT
1024G Memory

When I'm using ubuntu 7.04 Amd64 Version live CD to boot my system. the system running error, keep report errors of deskop script and mix script. So i give up and change to i386 version, it's runs well.
Then I try to install this into my IDE driver with 1025 swap and 8G to root mount point. After I boot my computer(change my harddisk boot order to ide harddisk), it frzzen with the first boot screen.
I boot in recovery mode, the last error message i've got was:
ldm_validate_partition_table disk read failed
dma_intr: status =0x51 Driveready seek complete error
dma_intr: status = 0x84 DriveStatusError BadCRC

I don't know why this happen, could anyone can help me?:(
Thanks in advance!

---

### Post by Pumalite on 2007-06-18
> **mobgame said:**
> Hi, I've try lot of times to install ubuntu 7.04 i386 version into my system. it's does't work still.
My system configuration list below:
AMD64 3000+
Gigabyte K8N SLI(NForce4 platform)
Maxtor 160G SATAII
Segate 120G IDE
NVidia GF4 6600GT
1024G Memory

When I'm using ubuntu 7.04 Amd64 Version live CD to boot my system. the system running error, keep report errors of deskop script and mix script. So i give up and change to i386 version, it's runs well.
Then I try to install this into my IDE driver with 1025 swap and 8G to root mount point. After I boot my computer(change my harddisk boot order to ide harddisk), it frzzen with the first boot screen.
I boot in recovery mode, the last error message i've got was:
ldm_validate_partition_table disk read failed
dma_intr: status =0x51 Driveready seek complete error
dma_intr: status = 0x84 DriveStatusError BadCRC

I don't know why this happen, could anyone can help me?:(
Thanks in advance!

What else is in your IDE drive?

---

### Post by crxvfr on 2007-06-18
I've got amd64's on a system with sata devices. Ubuntu would not load for me.
I had to use the "noapic" option to get the cd to boot.

Also, why change boot devices? Doesn't setup have a list for boot order?

On my dell I hit f2 when the first screen appears to get into setup where I find a list of devices to boot from. If theres no cd in the drive, it moves onto the next device.

---

### Post by mobgame on 2007-06-19
Nobody meet this problems?

---

### Post by AllenGG on 2007-06-19
Hi Mobgame, well yes, sort of......
unable to load 7.04, Feisty from the live CD.  Switched to regular install for X64, there were a few glitches, mostly with the NVidia card.  Used the SATA drive immediately as primary, and discovered the IDE "drivers", no IDE HDD on mine.
  AMD64 on ASUS K series. 
....and I still have problems with my USB 2.0 2gig jump drives.
Have you tried the "regular" or "alternate install" ?

---

