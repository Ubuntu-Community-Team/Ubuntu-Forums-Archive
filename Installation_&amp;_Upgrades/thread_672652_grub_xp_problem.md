---
title: "grub xp problem"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by foz1284 on 2008-01-19
hi, I installed ubuntu for the first time this evening, 

it is installed on to a USB IDE HDD  connectec to the laptop which has win xp  on the internal drive,

I didnt realise during the installation that I had installed grub onto the xp drive, 

Now grub encounters and error 21 if the usb drive is not connected, if connected it runs both xp and ubuntu fine,

I tried to use the xp cd to fixmbr and fixboot but the cd does not see the internal drive, bios seems fine

if usbdrive is connected it can see a fat partition and an unknown partition both from the external drive,

with the usb dissconnected it sees nothing,

I am not bothered about ruining the ubuntu install but I could really do with the xp install intact

thanks in advance,


Mark

---

### Post by louieb on 2008-01-19
Well 1st I guess you want to get XP to boot without having the external drive attached. Lots of ways . The SuperGrub Disk is one.
Heres a  list of few diffrent way to do it. I am surprised your XP CD could not fix it.   [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm") Don't let the name fool you this page is all about fixing the MBR so the PC will boot Windows.

---

### Post by foz1284 on 2008-01-20
Thanks for the link, I used supergrub disk and it worked fine restoring the win mbr.

---

