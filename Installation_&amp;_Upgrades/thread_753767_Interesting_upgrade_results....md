---
title: "Interesting upgrade results..."
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by AndrewW on 2008-04-13
Hey all,

I am running Kubuntu 7.10 on my Acer TravelMate 521iT with 320MB RAM

I recently updated about 150 packages using adept.  After this it asked me if I wished to update Kubuntu. This seemed not to work.  I then had trouble starting the updated Adept cleanly.  It said the DB was in use or locked.  I hardware restarted.  After restarting, the boot shows "file not found... press key to continue."  This leads to a list of 3 options which are namely:
[LIST]
[*]Ubuntu 7.10 kernel 2.6.22-14 generic
[*]Ubuntu 7.10 kernel 2.6.22-14 generic (recov mode)
[*]memtest
[/LIST]

the two important ones don't work.  
Anybody know what this is about?

Also, just before updating, i noticed that the complete update would have been 200mb+ so i changed all the addresses in /etc/apt/sources.list from my local archive to my ISP archive (ftp.iinet.net.au) as it seemed to be another mirror.

 Thanks.

---

### Post by tvtech on 2008-04-14
thats a standard grub boot screen sounds like you've gubbed up your boot.  throw in the cd / dvd and repair your system from that.

---

