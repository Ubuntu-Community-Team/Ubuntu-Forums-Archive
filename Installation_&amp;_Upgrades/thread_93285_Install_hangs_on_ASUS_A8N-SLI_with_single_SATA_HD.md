---
title: "Install hangs on ASUS A8N-SLI with single SATA HD"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by rio-paco on 2005-11-21
Hi,

My machine is a (newly built):
ASUS A8N-SLI Deluxe [BIOS 1013]
AMD64 3800+
250 GB Samsung SpinPoint SATA
CD reader ATAPI [Primary master]
CD/DVD reader/writer ATAPI [Primary slave]

I'm booting from the CD reader.

My installation simply hangs when I try to partition the harddisk. Also, the installer recognizes the SATA disk as a SCSI disk, which seems to be wrong or? 

The first time I ran the installer it managed to partition 47% of the disk before it hung. Now the installer simply says that it failed to access the disk.

Even more scary is that *sometimes* when I run the installer it doesn't even recognize any hard disk at all. I've checked the cables and also verified that the BIOS correctly identifies the SATA harddisk.

I've seen in some forums that there can be problems with NVIDIA SATA controller chipsets. 

Any help would be much appreciated.

---

### Post by yesplease on 2005-11-21
Great machine. Most SATA problems are old but manufactorors are making new ones :)  

Here [http://ubuntuforums.org/showthread.php?t=58278&highlight=ASUS+A8N-SLI+Deluxe](http://ubuntuforums.org/showthread.php?t=58278&highlight=ASUS+A8N-SLI+Deluxe) 
somebody installed on IDE and then needs drivers for SATA. 

If you have the live CD then you can check if Gparted recognizes the disks (and partition also). Did you check the validity of the install CD?

Failing that you could pm Bondolon for info on the drivers, or install on an iDE drive till a solution arrives.

Edit: I installed on sata, but I havent got the drivers Bodolon uses, so they are probably from the nvidia site.

---

### Post by rio-paco on 2005-11-22
Thanks for the reply.

I booted with the live CD. First time it hung when starting LVM. Second time it booted all the way.

Running Gparted results in Gparted hanging. Also I see no /dev/sd* devices. 

lsmod reports that all the modules

  sata_nv
  libata
  scsi_mod
  sd_mod

are loaded which was what the other guy with a A8N-SLI Deluxe motherboard needed to get his SATA drive to work.

I can't mount my floppy disk either to save my dmesg (I can mount it when booting with Gentoo though). Anyway dmesg reports stuff like:

---
ATA: abnormal status 0xD0 on port 0x9E7
ATA: abnormal status 0xD0 on port 0x9E7
ATA: abnormal status 0xD0 on port 0x9E7
ata3: command 0x25 timeout, stat 0xd0 host_stat 0xb1
ata3: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
ata3: status=0x25 { DeviceFault CorrectedError Error }
SCSI error: <2 0 0 0> return code = 0x8000002
sda: Current: sense key: Hardware Error
    Additional sense: No additional sense information
end_request: I/O error, dev sda, sector 476359475
Buffer I/O error on device sda5, logical block 4
---

And so on for a few more sectors.

As it seems that the Ubuntu kernel has loaded all modules that are needed for  the A8N-SLI SATA controller, I suspect that I:

a) have a bad A8N-SLI SATA controller or
b) have a bad Samsung SpinPoint SATA harddisk

Any ideas how I can confirm or dismiss the above?

---

### Post by yesplease on 2005-11-22
Could be bad hardware, but perhaps you are overly pessimistic.

I would try first to confirm if anybody has installed ubuntu on this motherboard by searching for the name of your motherboard and ubuntu on the net. That could also provide info on the install method. You use an onboard SATA controller, right?

You can also try to check your partitions with Gentoo, or repartition with it.
Verify your ubuntu install CD.

---

