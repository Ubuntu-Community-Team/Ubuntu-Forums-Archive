---
title: "Windows Installer 11-10 Hangs"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by gemjack on 2012-04-25
Hope someone has some ideas with this.   I have installed this installer in the past with no problem, however I need to do a re install on XP PC and the system is now hanging on Expanding... please wait, left it for over an hour.   Done the normal Windows stuff rebooted, download the file again etc...

---

### Post by Mark Phelps on 2012-04-25
IF your PC already has Ubuntu on it (these are the Ubuntu forums, not the Windows XP forums ...), XP will choke on the install because it will not be able to comprehend the Linux filesystem there.

You can either remove the Linux filesystem (you will have to boot from an Ubuntu LiveCD or LiveUSB to do this), or you can shrink it and leave some unallocated space for installing XP.

---

### Post by gemjack on 2012-04-25
No this a Windows XP machine and I am installing with the Ubuntu Windows installer.  Like I said I have had Ubuntu running fine before, but had to re build the PC, (XP problem) so I need to build everything from scratch.....

---

### Post by Mark Phelps on 2012-04-25
Sorry, misunderstood you ... thought you were trying to install XP dual-boot on an existing Ubuntu PC.

So basically, you have a old XP machine, you boot from an Ubuntu CD, it only gets part way -- and hangs for over an hour, at which point you turn it off.  Have I got that right?

How old is the PC, or better, how old is the hard drive? Asking because if the hard drive is failing, any installation is likely to hang if it encounters bad sector while trying to do the install.

There could be other problems as well (like video) -- so next time, boot from the Ubuntu desktop CD, and when you get the selection screen, choose the Try Ubuntu option -- and see if it gets all the way to a working desktop.

---

