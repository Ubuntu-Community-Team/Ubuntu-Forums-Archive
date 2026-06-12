---
title: "Edgy an Feisty won't instal but Dapper does"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by azelter on 2007-04-21
I have a Dell 710m and I am trying to do a fresh install of Feisty. I had previouly installed dapper on it, run that for 6 months and upgraded to edgy. Both of these versions ran fine. Now I decided to do a fresh install of feisty, however, the desktop i386 cd won't boot. The alternate version boots, but instalation fails after a few minutes (having got through the initial questions and begun the real install) complaining of errors on the cd. If I run a 'check cd for errors' from the boot menu it says the cd has errors - however, if I do the same thing from another computer all works fine and the check program says there are no errors on the cd. All this made me think I had a problem with my dvdrom drive on the laptop, however, the really strange thing is - if I take my old dapper i386 install cd it boots fine into the live ubuntu version (remember the feisty desktop cd won't even load the kernel to do a checksum or anything else on this laptop). If I check the dapper cd for errors on the 710m it says all is well. This is consistant - as is the error with the feisty cds. So I am confused. This does not looks like a cd error despite the fact that if I go to a consol in feisty after the instalation starts to fail I see errors in the syslog like:
buffer i/o error on device sr0 lock 147243
read error ...
sr0 current sense key medium error
scsi error: return code 0x00000002 etc. etc

I have also done a memtest on this laptop and it has no problems.

If anyone has any clues for me or other things I should check I would be very grateful indeed!
Thanks in advance,
Alex

---

### Post by bwhite82 on 2007-04-21
> buffer i/o error on device sr0 lock 147243
read error ...
sr0 current sense key medium error
scsi error: return code 0x00000002 etc. etc

This tells me you have a bad burn bro, try burning at a slower speed on different blank media.

---

### Post by azelter on 2007-04-21
How can that be. The disks work fine on another computer.
I was wondering if it was something to do with the introduction of the scsi drivers for all ide devices

---

### Post by azelter on 2007-04-23
Well, you may have been right. I reburned the image on a dvd (on the basis that it also uses a different wavelength on the reader) and it installed no problem. I'm still confused why one box thought the disk was fine and the other couldn't read it. Thanks for the suggestion though. Got me going again.

---

