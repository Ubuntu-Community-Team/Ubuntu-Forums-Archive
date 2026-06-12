---
title: "Unable to install on SCSI RAID?"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Muskiet on 2010-02-16
First off I'd like to say I'm very new to Ubuntu, so I'm still trying to learn.
I have a K8 motherboard with an adaptec U320 SCSI card with RAID ability.
To that card I connected two 15k RPM 35 GB Maxtor SCSI drives.
For some reason I'm not able to install Ubuntu 9.10 onto these drives with both drives in RAID 0.
With both drives separately configured Ubuntu doesn't even see them.
I have by the way run Windows XP and 2000 succesfully on these drives in Raid 0 configuration.

I set up the array in the card's bios as bootable with write cache enabled.
The system's bios sees the array as the array to boot from.
Ubuntu (both standard and alternate) sees the array and I have tried to install Ubuntu on it by manually partitioning it or having me guide it with or without LVM.
I tend to delete and rebuild the array between attempts so I have a clean slate to start from every time I try.
I have no other drives (except the CD of course) installed on this computer.

The whole installation goes very well untill the end where I get a message that it could not install the boot loader (grub?).
Every single time I've tried to install Ubuntu in all sorts of ways onto my RAID 0 array I have run into problems installing that boot loader, and I've tried that card and those disks in another computer as well.

Tomorrow I'd like to try to manually set up the partitions with a small /boot partition on a standard hard drive with / on the array, but if somebody please has any idea's on how I might get it working without having to rely on another hard disk (which might not even work of course) I would surely appreciate you sharing this with me.

---

### Post by byStanderone on 2010-02-16
...about raid: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by darkod on 2010-02-16
You don't need the separate disk but I think you still need /boot to be separate partition outside the array. When configuring the array leave about 200MB at the start, not included in the array.
And use ubuntu alternate install cd. Hopefully it will be able to see that space and you can create the /boot partition on it.

---

### Post by Muskiet on 2010-02-16
> **byStanderone said:**
> ...about raid: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I have read that yes, several times.
But it's about software RAID, not hardware, which is what the Adaptec card is for.
The card fools the computer into thinking there is only one hard disk while there are really two in RAID 0 config.

---

### Post by darkod on 2010-02-16
Did you manage to try with leaving a small 200MB partition at the beginning outside the array? And use it as /boot partition.

---

### Post by Muskiet on 2010-02-16
> **darkod said:**
> You don't need the separate disk but I think you still need /boot to be separate partition outside the array. When configuring the array leave about 200MB at the start, not included in the array.
And use ubuntu alternate install cd. Hopefully it will be able to see that space and you can create the /boot partition on it.

When creating a hardware RAID 0 array it will use 100% of both disks.
This is all set up in the bios of the SCSI card.
Therefore I cannot make a separate /boot partition outside the RAID 0 array without a separate disk, which I'm gonna try in a few minutes.

---

### Post by darkod on 2010-02-16
> **Muskiet said:**
> When creating a hardware RAID 0 array it will use 100% of both disks.
This is all set up in the bios of the SCSI card.
Therefore I cannot make a separate /boot partition outside the RAID 0 array without a separate disk, which I'm gonna try in a few minutes.

From my limited experience with hardware raid on Dell servers, you should be able to choose part of the hdds to be left out of the array. Delete the array, start from scratch and take a better look, there should be some option.

But I might be wrong, note that. :)

---

### Post by darkod on 2010-02-16
How about this idea?
[http://simplysimple.info/installing-ubuntu-server-hardware-raid/](http://simplysimple.info/installing-ubuntu-server-hardware-raid/)

I agree it's not the optimal solution, but it seems it worked. :)

---

### Post by Muskiet on 2010-02-16
> **darkod said:**
> How about this idea?
[http://simplysimple.info/installing-ubuntu-server-hardware-raid/](http://simplysimple.info/installing-ubuntu-server-hardware-raid/)

I agree it's not the optimal solution, but it seems it worked. :)

The Adaptec raid controller only allows for entire hard disks to be part of the RAID 0 array.
And thank you for finding the above idea, but unfortunately it's an idea that works in RAID 1 where both disks share the same information so it doesn't matter if one is missing during installation, but in RAID 0 you split the information over both disks so you basically read half of the information on one disk and at the same time half on the other making the array faster then a single disk (not twice as fast of course, but noticeably faster).
Therefore I need to have both disks installed and assigned before I can even install anything on them.
If I take one disk out I'd be taking out half the information with it and thus the remaining disk is useless.
It's slightly risky of course, one disk goes bad, both are bad, but I ran a hardware raid system for 5 years with two IDE Maxtors without any problems (Windows XP, and those disks are still good) and these SCSI Maxtors are known to be able to survive the next ice age (okay... just a tad too optimistic I think) ;)

---

### Post by darkod on 2010-02-16
Sorry, I missed the RAID0 part. I know the difference otherwise. :(

---

### Post by Muskiet on 2010-02-16
> **darkod said:**
> Sorry, I missed the RAID0 part. I know the difference otherwise. :(

I didn't want to imply that you don't know the difference and I certainly don't want to insult you in any way, I just wanted to clarify the problem so please no hard feelings.
Before trying to use a seperate disk for /boot I'm going to try another installation, the 64 bit one.
I do remember having much less of a hard time installing the 64 bit version of Windows XP on my RAID array then the 32 bit one so let's see if that works.

Oh... and I have no clue whatsoever what I'm doing with Ubuntu :)

---

### Post by darkod on 2010-02-16
No hard feelings at all. I just typed it like that, I wasn't having a go at you. :)

Too bad you need fakeraid for windows, I was just playing with software raid in virtual box and I'm pretty impressed I have to say. Not that I didn't expect it. :)

---

