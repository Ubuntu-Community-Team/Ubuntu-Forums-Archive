---
title: "UEFI does not want to boot from the Hard Drive."
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by mistermagio on 2013-12-19
Hi, 

I just got a new Laptop (Zenbook UX301, Dual SSD thingy), yesterday, and I've been trying to install Ubuntu 13.10 on it ever since. However, nothing ever comes easy in UEFI world.

The LiveUSB I used booted just find, I messed around for a bit, testing things to make sure it was gonna run smoothly, without too many hitches, and it did.
So I decided to go ahead and install it, after going through the BIOS to switch my SATA config from Raid0 to AHCI, therefore wiping everything in the process.

I didn't encounter many problems during the Install, in automatic mode with the LVM partition thing checked. 

So then I rebooted, kinda expecting something to screw up, and indeed something did.
The Zenbook booted immediately to the BIOS, and did not seem to detect any kind of hard drive to boot from. I decided to go back to my Ubuntu LiveUSB, install Boot-repair, and ran it with its recommended options. Followed the instructions (here's the bootinfo I got then: [http://paste.ubuntu.com/6599313](http://paste.ubuntu.com/6599313)), then rebooted, and once again, UEFI doesn't seem to think there's anything to boot from. 

So I went back to the LiveUSB, back to Boot-repair, tried a few other options that seemed tightly related to the problems I was experiencing, followed the instructions, and got this: [http://paste.ubuntu.com/6599369](http://paste.ubuntu.com/6599369)
Still nothing to boot from according to UEFI, back to the LiveUSB, and now typing this message. I did run boot-repair once again, and asked for the Bootinfo right away, on the off chance UEFI screws it up itself at every reboot, and got this as an answer. [http://paste.ubuntu.com/6599410/](http://paste.ubuntu.com/6599410/)
Please note that I've tried to enable Legacy Mode, with SecureBoot ON and OFF, and up until now, none of it has given me any kind of results.

I hope someone here will be able to save me from madness, though I'll be enjoying myself on this wonderful LiveUSB in the meantime.

Thank you in advance for your answers,

---

### Post by oldfred on 2013-12-19
You are showing a /device/mapper/....

That is RAID. So it seems your dual SSDs configured as RAID not two standard drives? The standard desktop installer does not have the RAID drivers. Boot-Repair adds both LVM & RAID drivers but both use /device/mapper, so it has difficulty telling them apart. 

Not sure that you can break the RAID as if it is RAID 0, then any drive failure destroys both drives data. As half of everything is alternated on each drive. 

Do not even know if you can fully backup Windows so you have it as one image and then restore that to one drive or not. 

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

