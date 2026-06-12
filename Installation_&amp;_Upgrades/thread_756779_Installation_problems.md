---
title: "Installation problems"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by roypk on 2008-04-16
Hi,

I've been having some problems installing Ubuntu 7.10.  My system was configured as a dual boot system.  It had previously been running WindowsXP and OpenSuse 10.3.  To try Ubuntu, I wiped out SuSe and deleted all Linux partitions, basically, providing around 25GB of unpartitioned space for the new OS.  Booting up Ubuntu on the CD was no problem but when I tried to install it to my HD, it stopped at 82%.  There were no error messages.  The progress just stayed at 82% and wouldn't go any further so I eventually terminated the installation and rebooted.  That's when the fun started.  The machine wouldn't boot up at all.  The only error message I saw on the screen was "error loading operating system".  I decided to take a look at the partitions using a bootable CD and saw that Linux partitions had been created and set active.  Setting the active partition back to WindowsXP partition didn't help.  The system still wouldn't boot so I tried running the PQMagic on my bootable CD to check the partitions.  The program found some errors and fixed them.  Now, I'm back on the XP typing this message.  Any suggestions on what to do to install Ubuntu on my machine?  I'm a Linux newbie and not a computer expert so any help would be greatly appreciated.  My machine's specifications are as follows:
Intel E6550
Asus P5K(Intel P35)
250x2 Seagate SATA drives.  Each is set up to have two partitions, one primary and one extended.  I shrank WinXP partition to provide 25GB of unpartitioned space to try Linux.
2 LiteOn SATA DVD Writers
1GB DDR2 SDRAM(Corsair)
Nvidia 8600GT Display card

Best regards,
Roy

---

### Post by Pumalite on 2008-04-16
Get Super Grub to fix XP MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Get Gparted Live CD and post a screen shot of your partitions:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Did you do md5sum on your download? Did you burn at 4x or less? Did you check for defects on CD?

---

### Post by roypk on 2008-04-17
MD5SUM?  How?  Sorry, this may seem a stupid question but I'm not an expert.  To answer some of the questions, yes, the CD was written at 4X and the media tested out ok so the last possibility is the download.

BTW, I tried installing it again.  Same problem.  It got stuck at 82% doing something called "scanning mirror".  Does it mean anything to you?  I have got two writers and 4 removable drives (from a card reader) on this system.  Do you think it would make any difference if these additional drives are removed?

Best regards,
Roy

---

### Post by analoog on 2008-04-17
it's a checksum algorithm.It's a way to verify if the file is correct.

[http://en.wikipedia.org/wiki/Checksum](http://en.wikipedia.org/wiki/Checksum)

see 
[http://blogs.developerfusion.co.uk/blogs/thushan/archive/2007/10/25/3398.aspx](http://blogs.developerfusion.co.uk/blogs/thushan/archive/2007/10/25/3398.aspx)
[http://ubuntuforums.org/showthread.php?t=303213](http://ubuntuforums.org/showthread.php?t=303213)
for people who had the same problem.

---

### Post by Pumalite on 2008-04-17
Disconnect everything except CD Drive and internal drive.

---

