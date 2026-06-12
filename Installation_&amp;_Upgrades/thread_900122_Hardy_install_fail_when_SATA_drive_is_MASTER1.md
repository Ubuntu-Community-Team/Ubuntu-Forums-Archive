---
title: "Hardy install fail when SATA drive is MASTER1"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by nanosec@sbcglobal.net on 2008-08-25
Hi All,
Ubuntu 8.04 installation will fail on my machine which has the following setup:
IDE MASTER 0 - no drive 
IDE SLAVE 0 - DVD-ROM
IDE MASTER 1 - SATA Hard drive.
IDE SLAVE 1 - no drive

The same hardware will install KUBUNTU 8.04 without any problem..
I know I can install KUBUNTU since it is essentially the same, I just interested what is the difference.

Thanks,
Peter

---

### Post by wpshooter on 2008-08-25
Is your DVD-Rom a SATA device ?

And I don't understand your reference to "IDE Master1 - SATA drive" - If you have a SATA drive on this motherboard connector then it is NOT an **IDE** connector.

If DVD-Rom is SATA then I would jumper it as master (if it has a jumper) and then put on number 2 SATA connector and I would also jumper (if it has a jumper) the SATA drive and then put it on SATA connector #1.

In short, make your hard drive a master and put it on the 1st or primary connector and make your DVD master also and put it on the 2nd or secondary connector.

---

### Post by nanosec@sbcglobal.net on 2008-08-25
Hi,
I have a fairly new MB (Gigabyte).
The BIOS options are:
IDE (Channel 0) = enable/disable
SATA controller = enable/disable
SATA options = IDE/RAID/AHCI
So the IDE is all the time MASTER/SLAVE channel 0
The SATA - I guess it is translated inside to a some kind of parallel bus, since processors don't deal with serial data very well :-) and I think it is kind of IDE format.
So the result is the SATA drive shows up in the BIOS as IDE MASTER channel 1 even if it is a SATA drive.
Unfortunatelly my DVD-ROM is IDE so I have to enable the IDE controller.
So I think UBUNTU doesn't see IDE MASTER channel 0 and thinks there is no drive to install the OS. However as I mentioned earlier KUBUNTU is working fine.

---

