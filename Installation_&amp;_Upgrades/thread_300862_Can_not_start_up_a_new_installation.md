---
title: "Can not start up a new installation"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by LarsRoan on 2006-11-16
I am new to linux and after installing Ubuntu Edgy x86 with alt CD yesterday on a brand new computer I didn't succeed to start up.  

I got the PC last week and installed Xp during the weekend.  Then I made new partitions  with the ubuntu CD (/, /home and linux-swap) and it looks like the installation succeeded (no error).

At the first start up (and further on...) I got to the grub screen and selected Ubuntu. After this i get a message "Starting up..." and then this error:

[17179572.892000]PCI: JMB26X: Enabling dual function on 0000.03:00.0
[17179572.916000]PCI: Cannot allocate resource region 0 on device 0000.03:00.0
[17179572.916000]PCI: Cannot allocate resource region 1 on device 0000.03:00.0
[17179572.916000]PCI: Cannot allocate resource region 2 on device 0000.03:00.0
[17179572.916000]PCI: Cannot allocate resource region 3 on device 0000.03:00.0
Error when updating region 0000.03:00.0/0 0000c000!=0 0000000
Error when updating region 0000.03:00.0/2 0000c008!=0 0000000

When I made the first trial of installation I got the same message when I tried to start up Ubuntu from the CD.  When I did the same by my old computer (6 years old) then no problem.  Once again I downloaded the iso; [http://no.releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso](http://no.releases.ubuntu.com/edgy/ubuntu-6.10-desktop-i386.iso) , burned it by Imgburn this time, check'ed it for error, and then it went well.  I went on and partitioned and installed Ubuntu. No error.
I made all the partitions inside the extended (When I installed WinXP then I made two primary p.; C and D for win.):
/, 10gb  (ext3)
swap, 1gb
/home, 30gb (ext3)
All of them mounted correcty.  In addition I part'ed one more inside the extended; a fat32 of 80gb.  I know that windows will not partition a fat32 larger then 32 gb, but than can not be the reason for Ubuntu not to start up?    What about the 1st message; "..Enabling dual function ", can my processor, Intel Core 2 Duo E6400 + Gainward GeForce 7300GT and Samsung Spinpoint P120S 250GB, SATA2 explain the problems?  

Any idea what's the problem?  What do you recommend me to do?  To start up in recovery mode?  And do what?

---

