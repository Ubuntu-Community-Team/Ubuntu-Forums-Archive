---
title: "Cannot setup RAID5 during Edgy install, won't partition RAID dev #0"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by nethbar on 2007-03-23
I've been researching this for a few days but I'm no guru and can't find a solution.  Hope you guys can help

I'm attempting to install Ubuntu 6.10 on a Dell Poweredge 610 workstation using the Alternate install CD.

Hooked up to the onboard Adaptec 7890 Ultra2/Wide LVD SCSI controller are 4 identical Quantum SCSI drives.  Everything tests out physically (termination, bad sectors, etc.) just fine.

When I get the partitioning part of the install, I set up my partitions like so:

> RAID dev #0 - 36 GB   Software RAID device
   #1 primary  36GB

SCSI1 (0,0,0) (sda) - 18.4 GB
   QUANTUM ATLAS IV 18 WLS
   #1 primary 18.0 GB   K   raid
   pri/log     370.1 MB   FREE SPACE

SCSI1 (0,1,0) (sdb) - 18.4 GB
   QUANTUM ATLAS IV 18 WLS
   #1 primary 18.0 GB   K   raid
   pri/log     370.1 MB   FREE SPACE

SCSI1 (0,0,0) (sdc) - 18.4 GB
   QUANTUM ATLAS IV 18 WLS
   #1 primary 18.0 GB   K   raid
   pri/log     370.1 MB   FREE SPACE

SCSI1 (0,0,0) (sdd) - 18.4 GB
   QUANTUM ATLAS IV 18 WLS
   #1 primary 18.0 GB   K   raid
   #2 /boot   74.0 MB  B  f  ext3
   pri/log     296.1 MB   FREE SPACE

When creating the RAID5 device, I use **sda, sdb**, and **sdc** and active devices and **sdd **as a hot spare.  

Once this is all setup, I select Guided Partitioning and pick RAID5 partition #1 to erase and use the entire partition.  It offers this:

> partition #1 of RAID5 device #0 as ext3
partition #5 of RAID5 device #0 as swap

I tell it to go ahead I get this error message twice:

> Error informing the kernel about modifications to partition /dev/md/0p1 -- Invalid argument.  This means Linux won't know about any changes you made to /dev/md/0p1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting. Ignore.  Cancel.

The second time it comes up it's for /dev/md/0p5

It doesn't matter if I ignore or cancel, it goes ahead and starts formatting and gives me this:
> Failed to create a file system.  The ext3 file system creation in partition #1 of RAID5 device #0 failed.  Go back.  Continue
and then throws me back to the partitioner, same layout as before.  (doesn't make a difference picking Go back or Continue)

I was setting this up every time using the Alt CD but I used the Live CD and Gparted and now the table (excepting the /boot partition) stays put.  I made a teeny Swap and / partition on the Alt CD and continued on *without* partitioning the RAID device and now the RAID5 device #0 stays put too.  

Here's what I'd like to know:
**1. **What's going on?  Is there a right way to setup RAID5 using the install CD?
**2. **If not, what's a good way to set up my RAID array outside of the install CD?  (I've found some howtos on mdadm but they're all pretty dated, the instructions aren't very clear, and I have little Linux experience.  Does anyone know a good guide for mdadm?)
**3. **I had heard that making /boot part of the array could cause problems.  Is it necessary to separate it?  I've tried it both ways with the same results.

Thanks!

---

