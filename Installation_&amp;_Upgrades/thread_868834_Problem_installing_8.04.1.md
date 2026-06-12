---
title: "Problem installing 8.04.1"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by jasinner on 2008-07-24
Disclaimer: Complete Linux Newb

Here is my story.  Currently running Windows XP.  I downloaded Ubuntu, checked the md5, burned it, all without issue.  I inserted the cd and tried the live CD.  It brought up Ubuntu and I enjoyed what I saw, decided to give it a shot as the only operating system.

When attempting to boot from the CD the installation program would get so far as a loading screen and eventually (amount of time varied) would kick me out into a "busybox".  I tried the video safe mode and the acpi safe modes with the same result.

I attempted to go back into the Live CD from windows and it would not work.  I tried multiple times finally one was randomly sucessful.  From inside the Live CD I noticed only my two IDE DVD drives were being recognized.  I attempted to "install" from inside the live CD and would get so far as the step for managing partitions and it would say "device not found" and not show any partitions.

Finally, I installed Ubuntu alongside Windows and from the boot menu I was able to press escape and enter verbose mode which I think allowed me to see some of what was going on.  The loading program would display the following error:

ata5:  SATA link up 1.5 Gbps (SStatus 113 Scontrol 300)
ata5.00: FAILED TO IDENTIFY (I/O ERROR, ERR-MASK=Ox4)
APIC ERROR ON CPU0: 08(08)
APIC ERROR ON CPU1: 08(08)
ata5.00: qc timeout (cmd 0xec)

It would retry this about 4 times before kicking me to a busybox.  My assumption is it is not correctly finding my hard drive as I never hear the hard drive spool up.  I also never see any mention of the hard drive info in the verbose mode.

My hard drive is a WD1500ADFD.

Any thoughts on this would be appreciated, I'd really like to dump Windows asap.

Thanks!

---

### Post by jasinner on 2008-07-24
Fixed my own problem by adding all_generic_ide.

Thanks me.

---

