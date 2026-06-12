---
title: "Dual-boot (Ubuntu and Windows7): partition layout?"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by veroslav on 2012-02-29
Hi all,

I bought a new laptop from Dell and now I would like to make it dual boot Windows 7 with Ubuntu 11.10. 
Windows 7 is already installed on the laptop. I have attached a screenshot that shows the partition situation in gParted.

My first question is: how many partitions are already used, 3 or 4? I am guessing 3 but I am not sure what to make of the
unallocated stuff.

In case there are three as I think, then my plan is to shrink sda3 (by using Partition Wizard from within Windows) and then
use the unallocated space left to create a new extended partition and within it, a few logical partitions needed for the
Ubuntu installation. Does this sound ok to you?

In case there are four partitions (unlikely), which partition would be a candidate for a deletion? I would like to be able to
re-install/recover Windows installation at some later time, if possible.

And one more thing: I would actually like to tripple-boot (Windows7/Ubuntu 11.10/Kubuntu 11.10), so the plan is to create
one logical partition (/) for Kubuntu 11.10, one logical partition (/) for Ubuntu 11.10 and one swap logical partition, inside
the extended partition I mentioned above. Does this sound ok?

I appreciate any tips and suggestions.

Thank you in advance!

---

### Post by veroslav on 2012-02-29
I just realized that I probably should have posted this in the "Installation and Upgrades" category. I apologize for this and I would like to ask mods to move the thread to the correct place.

Thanks.

---

### Post by howefield on 2012-02-29
So done.

3 partitions and your planning sounds fine.

---

### Post by veroslav on 2012-02-29
Thank you for both moving my thread and replying to my questions, howefield!

Glad to hear that I was on the right track, and it is nice to have it confirmed by somebody here.

Thanks again :)

---

### Post by Mark Phelps on 2012-02-29
Because of the risk nature of dual-boot installs, suggest you read through the material below ... BEFORE you do the setup:

If you decide to go ahead with dual-boot, then do the following:
1) Use the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. This can be run from inside Win7.  If you want to use Partition Wizard, I believe you have to boot from their CD to do that. Do NOT use the Ubuntu installer to do this.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by veroslav on 2012-02-29
Thank you for you valuable input, Mark Phelps.

I will check out whether I need to run the Live CD of Partition Wizard in order to shrink the Windows partition.
I wasn't sure myself, so I will check that out before commiting any changes.

I have already the backup DVD:s and I dont have any valuable data that needs to be backed up because I just received this computer yesterday :) I think I should be fine from that point of view.

Thank you again.

---

### Post by veroslav on 2012-03-01
I would just like to say that I managed to both shrink Windows 7 partition successfully with Partition Wizard, and then install both Ubuntu 11.10 and Kubuntu 11.10 on the remaining space without ANY problems whatsoever! :)

I am so happy and a little bit surprised that all went so smoothly as it did!

Thanks again for all the help.

Regards,
Veroslav

---

