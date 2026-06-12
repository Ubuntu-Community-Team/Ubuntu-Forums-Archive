---
title: "Triple Boot Problems"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by wgriffiths on 2011-05-02
Hi,

I'm having serious trouble getting a triple boot setup working on my Macbook Pro 5,1.

I originally had a 1TB drive partitioned about 500 GB for OSX and another 500GB for Windows, but I used iPartition to create space for a linux installation, by reducing the size of Mac Partition by 100 GB, giving 100GB for Linux. 

So I went ahead installing Linux which installed OK, with the Bootloader installed on the Root Partition as well as a 1GB Swap between the OSX and Windows Partitions.

Problem is now that while OSX works fine, I cannot get either Windows or Linux to boot, even through loading a bootloader via the CD and selecting boot first hard disk.  It simply says 'Missing Operating System'.

So I tried to get Windows working, I was then shocked to find that the Windows partition said 'Unallocated Space' (when booting the Win7 disk) but in OSX the Partition mounted fine. So I went to use PartedMagic and used TestDisk to rebuild the MBR, which allowed me then to mount the disk under the Windows disk, and carried out a chkdisk, and it mounted under Windows. However Windows no longer appears under OSX nor when I hold down 'Alt' at boot. The Linux partitions seem fine, but cannot be booted.

I have tried rEFIt but, it refuses to appear on boot.

So sorry for the massive array of problems...if anyone can provide any help or expertise on this, it'd be really helpful!

Thanks,

Wgriffiths

---

### Post by mikeydangerous on 2011-05-03
I had an issue like that. Just uninstalling and reinstalling rEFIt fixed the problem for me.

---

