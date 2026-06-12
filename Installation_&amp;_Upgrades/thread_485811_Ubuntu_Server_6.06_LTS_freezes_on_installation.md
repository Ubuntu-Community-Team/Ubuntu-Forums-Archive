---
title: "Ubuntu Server 6.06 LTS freezes on installation"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by andrewwk on 2007-06-27
Greetings all,

I am trying to install Ubuntu Server 6.06 LTS 32 bit.  The server has an Intel BLKDG965WHMKR motherboard with a Intel Core 2 duo processor, and a 3ware 9650SE-4LPML Raid card running 4 Seagate hard drives in a Raid 10.  The Ubuntu Server 6.06 LTS installation disks boots, but when I select "Install to the hard disk",  the computer will freeze after the line, "Uncompressing Linux... Ok, booting the kernel."  The cursor blinks underneath the line.

Here's my troubleshooting:

I can boot the server 6.06 LTS disc on another computer.
I can boot the ubuntu 7.04 disc
I can install ubuntu 7.04 with Raid 10 from the 3ware card.

The only reason I'm installing server 6.06 LTS is because the is little driver support for the 3ware raid card in server 7.04.

Does anyone know why the computer freezes after the booting kernel line? 

Thanks,
WK

---

### Post by andrewwk on 2007-07-05
guess not :-x:mad::-x:mad:

---

### Post by Rob_Stewart95 on 2007-07-08
I am having a very similar problem with an EPIA M1000.  I am also trying to run 6.06 (Kernel 2.6.15-26). The install went pretty flawlessly and went I went to reboot after the initial install I get the same line

"Uncompressing Linux...  Ok, booting the kernal."

And it freezes.  I have let it "boot the kernal" for 30 minutes with not luck.

Any suggestions?

---

### Post by andrewwk on 2007-07-10
Are you using IDE or SATA?  I'm using a 3ware card for a hardware raid 10 with SATA hard drives.  I think that might be the problem with mine.

---

### Post by scapalexis888 on 2007-07-13
I have the same problem too. I have a intel dual core on an intel motherboard with a 250gb SATA hd. When i tried to install ubuntu 6.06 on it with a live CD it goes to "Uncompressing Liunx...OK booting the kernel" and then hangs. Also tried the alternate 6.06 cd...same thing happens. Is it just that 6.06 doesnt work on dual cores or SATA harddrives? will feisty work on it?

---

### Post by Pumalite on 2007-07-13
I have Intel D975XBX, Core 2 Duo, 2GB RAM, 3 SATAII drives, 5 distros. One of them is Feisty 7.04

---

