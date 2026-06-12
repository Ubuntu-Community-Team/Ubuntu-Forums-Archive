---
title: "CD drive not responding to Live cds"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Taters on 2007-11-06
Firstly, I have the BIOS set to plug and play, but nothing is happening. I insert the CD, restart my computer, and after the HP welcome screen I get grub. 
This happened after I ran this into the command terminal using grub:

Debug = IO APIC (or maybe just apic, I can't remember)
It accepted this.
noapic
It bounced this one.

So now I have no access to any upgrade. I tried turning APIC off for 7.10.

My machine is a HP Pavilion a1200y
Here is all the stuff I know about it:
512 MB RAM
40 GB Hard Drive
Celeron D processor 
ATI Radeon Xpress 200

I know 7.10 isn't very HP friendly, but I just want a few key programs (Gimp 2.4 mostly)

Importance of questions:
How would I get live CDs to run again?
How would I turn of IO APIC?
Also, when I was trying to upgrade to 7.10 it said I wasn't connected to the timer, is this a part of the problem?

---

### Post by logos34 on 2007-11-06
changing apic in linux won't help--this is a bios or disk drive issue.  You're not even getting the cd to boot, so either the cdrom is not set first in the Bios device boot order or there's something wrong with the drive. Can you read discs in linux?.  Is there any activity with the cd drive before it boots to grub on thje hard drive?

---

### Post by Taters on 2007-11-06
The disk reader is fine. I just finished burning an ISO file 2 days ago, after the problem occurred.

And I do here the cd drive running when  I turn my machine on (if there is a cd in there, that is.)

I'll go through the BIOS again. The thing to turn on is "Plug and Play", right?

Thank you.

---

### Post by logos34 on 2007-11-06
it's just a matter of whether you want the Bios or OS to detect and configure plug n play devices.  I have mine set to OS. 

> And I do here the cd drive running when I turn my machine on (if there is a cd in there, that is.)

yes, but it has to be set in the bios as the first boot device (ahead of removable/floppy and hard disk).  If that's the case then i'm not sure what the problem is.

---

### Post by marciano#1 on 2007-11-06
I had a similar problem and fixed in Bios.
Boot sequence was set to "Advanced"
I changed it to "Normal"

---

### Post by Pumalite on 2007-11-06
Others require AHCI or 2nd Master and 'Auto'

---

