---
title: "Problems w/ Xubuntu 7.10 Install &amp; HP Desktop Pavilion 7850"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by HANtwister on 2007-10-22
Hello All-

I hate to add fuel to what seems to be an already large fire, but here goes.

I understand that there are problems with 7.10 and HP Laptops, however, the problem I'm having is with an HP Desktop. It is an HP Pavilion 7850, with 386 MB RAM and a 40 GB Hard Drive. When I tried to install Xubuntu 7.10 using the alternate disc (in my experience the alternate installs faster, and I don't necessarilly need to demo it; I verified the checksum as well), I was told a hard drive could not be found. In addition, I saw this message while the disc was booting: ata1: SRST Failed (errno=-16). I'll mention that there were some threads I've come across while searching for an answer with that error message, but none seem to really pertain to the situation.

I checked the BIOS, and it showed the hard drive as being there. I tried booting into a Parted Magic LiveCD, and it showed the hard drive and even let me mess around with it with GParted. I even tried booting into the Xubuntu 7.04 Alternate CD, and, sure enough, it let me install without any problems. I've also tried resetting the BIOS to it's defaults.

To help, the Hard Drive is a Western Digital Hard Drive, model WD400JB-00JJC0, and is NOT the computer's original hard drive. S.M.A.R.T. Diagnostics don't show any apparent problems, badblocks reports no bad sectors on the drive, and MemTest86+ doesn't show any apparent problems with the RAM. lspci reports the IDE Controller as being an Intel 82801AA IDE Controller, Revision 02.

It seems like the hardware isn't the problem, since Xubuntu 7.04 seems perfectly content with it all, but I've been wrong (more times than I can count) before.

Does this seem like a situation where I should stick with Xubuntu 7.04 for now and watch what happens with 7.10, or should the hardware be considered suspect? If you need any more information or need me to do something, please feel free to ask. This isn't a production computer, so, if necessary, I can get away with blowing away everything on it if and when needed.

Thanks in advance,
-Harrison N.

---

