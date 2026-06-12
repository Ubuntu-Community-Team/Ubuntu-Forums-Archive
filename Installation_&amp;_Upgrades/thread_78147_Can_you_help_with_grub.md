---
title: "Can you help with grub?"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by savvyside on 2005-10-17
Hello,

I am an Ubuntu lover I loved Hoary, so I pulled that drive (for safe keeping :) and put in a new IDE drive.  I had no problem installing Breezy or with any hardware, install went perfect. Kudos to the boys/girls in brown!

Ah, but alas, I tried to add two KNOWN good extra IDE drives from my old Hoary install. Grub could not boot. I just get constant GRUB GRUB (ad infinitum) on the screen. I pull both drives and try one at a time. No joy. 

All jumpers are fine (Master/slave).

My BIOS settings are auto. Some web grub posts warn to set to manual. That doesn't work, i get a grub 15 failure.

I go to add a Sata drive (as /dev/sda1), no problem.

No matter what I have done or tried, i can not get breezy to let me add these extra IDE drives.  I even booted a live CD and repartitioned them and layed down a new ext3 FS. No help! Live CD works fine with them tho.

This is not a dual boot problem. I just want linux with some spare hard drive space. There is nothing on the drives I care about, they can be wiped again if needed.

I tried blowing away the MBR on both spare drives (setting them to zero).

Just to prove the drives were fine, I pulled all drive, and put in one of the failing drives and was able to install breezy on it and it would boot fine. 

It is only when i have MORE than one IDE drive connected, grub completely fails!

This is a newer (about 1 year old) Gigabyte MOBO and P4 2.6 GHz with a gig of ram.

Does anyone have any ideas?

Thanks!

---

### Post by Murgle on 2005-10-17
do both drives have the bootable flag set, or perhaps neither do? that might be the problem.

---

### Post by savvyside on 2005-10-18
[QUOTE=Murgle]do both drives have the bootable flag set, or perhaps neither do? that might be the problem.[/QUOTE]

That is a very logical suggestion. I booted in the livecd and had set the two other drives to have boot flag OFF, with the primary on.

I can't be positive it is truly off for the add on drives, but I can be sure that it is on for the primary drive because all I have to do is remove the extra drives and the system boots (and works) fine. Therefore, the main drive must have bootable set correctly.

Thanks for trying to help. I am in Kettering Ohio. I see you are in Wooster.

M

---

### Post by GizzardBoy on 2005-10-18
I understand that cross-posting is not cool, but I made the unfortunate mistake of posting my problem under a part of this help section with "(Solved)" at the end, so I fear that no one knows of my plight.  :( Please, if you know how to restore an MBR or make grub allow dual boot on a new floppy-less laptop, see my posts under that section next door.

Thanks,

GB

---

### Post by Murgle on 2005-10-18
I just grabbing at air here, but does anthing happen when you rig them to be master and slave,  also are both of their pins set correctly for master?

I am indeed at Wooster, I go to the college here

---

### Post by savvyside on 2005-10-19
[QUOTE=Murgle]I just grabbing at air here, but does anthing happen when you rig them to be master and slave,  also are both of their pins set correctly for master?

I am indeed at Wooster, I go to the college here[/QUOTE]

I do have them configured as master/slave on one IDE channel.

On the other channel, I have a DVD burner as master and the spare drive as slave.

I wonder where all the grub experts hang out?

M

---

### Post by Murgle on 2005-10-19
you might want to try #ubuntu on irc, it should be one of the presets in xchat.  maybe someone can help you there...

---

### Post by savvyside on 2005-10-27
I finally updated the BIOS in my motherboard and now it all works. Hope my failure helps someone else!

Michael

---

