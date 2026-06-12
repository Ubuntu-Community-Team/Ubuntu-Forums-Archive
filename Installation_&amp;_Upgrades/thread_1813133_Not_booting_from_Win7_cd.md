---
title: "Not booting from Win7 cd"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by harrythehorton on 2011-07-27
So my sgt comes in asking questions about using his new solidstate hdd along side his older larger hdd.  He tried installing win7 on the new solid state(and did) but didn't understand the bios changes that needed to be made to boot from the solidstate rather than the other(not just boot order, had to switch out which was recognized as the hdd).  There was some sort of a lock on the Old hdd that prevented it from being wiped, formatted, ect.  I opted to run an ubuntu live cd to try to wipe the old hdd that way.  It worked(of course) however the drive still couldn't be 'formatted' so we just wiped the file system as the bootmgr on the old hdd would be used, it was just for space.  When the sgt accidentally wiped each partition and hdd he looked at the ubuntu system asking what the hell he was using.  I explained the finer points of ubuntu and he decided to give it a shot instead.

At this point he's come back after trying to get WOW to run on it's own.  He tried setting it up as a VM but had trouble as the computer wouldn't read the win7 cd at all.  Not just the OS, the computer as before wouldn't even boot to the cd no matter how much I tinkered with the boot configurations(it would only boot from the ubuntu cd).

The windows cd is verified and working on other computers.

Using the ISO works for the VM, but he'd rather have a sep partition.

If anyone has any non hardware specific tips on how to figure this out, i'm all ears.


Thanks community

---

### Post by dino99 on 2011-07-27
better to ask your MotherBoard's support to get help with that bios, and/or read their forum

---

### Post by oldfred on 2011-07-27
I think a few BIOS require you to set BIOS to boot CD and use one time boot key to select CD to get it to boot from CD.

But since you reconfigured drives, are all cables fully plugged in. SATA or PATA connections? I do not think I was able to reconfigure system with all the PATA cables without having one come half way out and show power but not signal. I now only have SATA but still find a lose connection. Now I only use locking SATA connectors.

Also if PATA are jumpers correct on drives?

---

### Post by Mark Phelps on 2011-07-27
Not able to afford an SSD myself, but I've read numerous times that there are special things you need to do to format and boot from an SSD. Simply installing to one may not be enough.

If I understand your situation, the following is true -- The PC can boot from an Ubuntu CD but not from a Win7 DVD (it comes on DVDs not CDs).  Can you confirm that your PC optical drive can also read DVDs (I know, all recent drives can -- but there's no info on the age of the drive).

So, can it boot from other DVDs, just not Win7? Or can it only boot from CDs?

You said the "CD" was verified in other PCs, but did you try to boot these other PCs?

Also, are you trying to boot the PC when it's cold? Or are you waiting until it's been running a while? Asking because I had a PC whose optical drive wouldn't function once the machine got warm.  Would only work upon initial startup of the PC.

---

