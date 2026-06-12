---
title: "Ubunto install hangs"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by lukemack on 2007-01-13
Hi,

I am trying to install Ubunto 6.10 server onto a Dell Dimension (2Ghz, 1GB RAM) and the installer is hanging at 83% during the 'installing the base system' stage. I'm installing to a 40GB disk on IDE1 Slave with 2 partitions - one primary of 30GB and 1 logical of 10GB (swap area). The message on screen at that time is 'Installing the kernel'

Can anyone suggest what might be causing the installer to hang? I have left it for over an hour at that stage - the machine becomes completely unresponsive and I have to pull the power cable out to reboot it.



many thanks,

lukemack

---

### Post by taurus on 2007-01-13
I am sure you burned the CD a little too fast!  How fast did you burn it anyway?  Try burning it at a slower speed like 4x.

---

### Post by lukemack on 2007-01-13
I burned it at 4x as there seemed to be so many posts saying to do that (although I find it pretty incredible that this should have such a huge influence - I have installed many operating systems without having to worry about this). The installer's own CD check also does not find any problems with the CD.

---

### Post by Pobega on 2007-01-13
Reburn the CD and try again, if that doesn't work try redownloading and burning on another CD. If that doesn't work then it is probably your CD-Drive, or just bad luck.

---

### Post by NMeyne on 2007-01-13
Perhaps prove the drive with another Linux distro, like DSL-N?   Worked first time with my Dell PC...  So I think for me its not the CD or the drive on my machine that are the problem. It's something about the drivers or Dell bios that blows up Ubuntu (and X, K, and Fluxbuntu) install every time.  Maybe the same for you?

Sorry - not much help... you're not alone!

Nick

---

### Post by lukemack on 2007-01-14
i burned yet another CD from a different iso file (downloaded from another mirror) and that worked.  ubuntu is now installed. i had to jump through a few hoops to get the wireless card working but otherwise all is well.

---

