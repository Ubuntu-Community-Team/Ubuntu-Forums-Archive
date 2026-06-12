---
title: "Bootloader woes..."
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by draconis73521 on 2005-12-06
Ok, I've pulled out what hair I have left..
I've gone through and booted from a BartsPE cd..
I've reinstalled, reformated, regained and lost my sanity.

For some reason, I can go through an install of k/ubuntu on my IDEBus1Device0 drive with no problems.. until I reboot. GRUB installs fine, no errors, nothing to explain why upon rebooting, the bootloader halts with no recognizable error to me.
It just displays about 5 rows of the number 9(nine) across the screen.

I've booted from LiveCD, I've done the mkdir -> mnt -> chroot method, everything I could find to get GRUB to work. No dice.
I've installed to the drive with & without using LVM, using multiple or even only 2 partitions.

I'm glad I keep my hair short, else I would have pulled it out by now.

System - 
Dual processor Xenon P4's - 
2 HD's
hda - 250GB on IDE0 master, slave is a DVD-RW
Was attempting to run Kubuntu - Had it working but apt-get'ed myself into dependency heck..
hdb - 120GB on IDE1 master, slave is CD-RW
WinDoze XPsp2 - Only there until I pickup another HD to replace this one, and turn this one into an external USB.
ATI vid cards (All in wonder 2006 ed. - 9600 Radeon) and secondardy HDTW wonder card.
Mb is old, but has current BIOS flash applied.
2GB of ram (4x512)

Any help?

---

### Post by fourchannel on 2005-12-06
you probably don't want to hear this...

but i had a similar problem a while back. I got this new 250G drive and installed hoary. got it customed out and all, and when i rebooted, got errors like drive seek error. and other not good stuff.

my temporary fix was to open up fdisk and rewrite the partition table every time before i rebooted. if i re-wrote the table then it would reboot no probs. ended up replacing harddirve.

try the fdisk thing. if not then maybe try installing your boot loader on another harddrive, if you have one.

---

### Post by bwog on 2005-12-06
" maybe try installing your boot loader on another harddrive, if you have one. "

Or on a floppy.

Otherwise, post your partitioning info and menu.list (via the live CD).

---

### Post by draconis73521 on 2005-12-07
Ever have one of those "Duh.." moments..
See.. when I installed this nice new 250Gb drive, I had installed it on my second IDE bus, planning on just data warehousing...
When IDE1 drive started acting tickling, I reconfigured and moved the drives around..
And I did not update my BIOS boot priority settings.
GRUB works just fine as long as it get's first shot at my system..
Greedy little pig now isn't it?
;)

Drac

---

### Post by fourchannel on 2005-12-07
haha. i swear it took me months to figure out my grub errors. i have 2 harddrives in a comp. 1 is a relatively new WD 40G, the other some old 13G one.

when the comp would halt the drives would spin down. and when it restarted the WD would register in the bios, but not the other one. so the bios would change the priority from the 13G to the 40G, and keep it that way. AND not tell me.

fix was to ctrl-alt-del it like 5 times while letting the harddrive spin up, then go in to bios and fix priority.

---

### Post by bwog on 2005-12-07
My BIOS has a 'force ESCD' function to force an update of new hardware. I dont know iff all BIOSses have that. I suspect that some BIOSses deviate from standards.

---

