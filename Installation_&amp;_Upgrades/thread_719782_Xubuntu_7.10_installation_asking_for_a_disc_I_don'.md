---
title: "Xubuntu 7.10 installation asking for a disc I don't have and can't find ..."
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by LANjackal on 2008-03-09
Hi, I'm trying to install Xubuntu 7.10 on my Toshiba 2805-S603, 1GHz PIII, 128MB ram using the alternate 286 installation disc. My previous 7.04 installation went kaput, you may see the link in my signature about that. Now I'm trying again with 7.10.

However, now I'm getting this message:

> Media change: please insert the disc labeled  'Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press enter

Can anyone tell me which disc this is, as scoured the available ISOs on the Xubuntu website and can't find any that match the above description. Or am I missing something? Help?

Thanks in advance,
LJ

---

### Post by lloyd_b on 2008-03-09
> **LANjackal said:**
> Hi, I'm trying to install Xubuntu 7.10 on my Toshiba 2805-S603, 1GHz PIII, 128MB ram using the alternate 286 installation disc. My previous 7.04 installation went kaput, you may see the link in my signature about that. Now I'm trying again with 7.10.

However, now I'm getting this message:



Can anyone tell me which disc this is, as scoured the available ISOs on the Xubuntu website and can't find any that match the above description. Or am I missing something? Help?

Thanks in advance,
LJ

Uhm, that *should* be the alternate install disk (Gutsy Gibbon is 7.10).

At what point in the installation are you seeing this? 

One possible alternative: If you have a reasonably fast network connection, choose "install a command line system".  Once that's up and running, edit the file "/etc/apt/sources.list" ("sudo nano /etc/apt/sources.list", and put a "#" in front of any lines that start "deb cdrom:") to remove the CD from the list of sources, and then do "sudo apt-get install xubuntu-desktop" to complete the installation.

Lloyd B.

---

