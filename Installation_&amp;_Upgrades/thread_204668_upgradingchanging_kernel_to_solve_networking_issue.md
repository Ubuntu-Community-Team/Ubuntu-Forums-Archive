---
title: "upgrading/changing kernel to solve networking issue"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by strattonbrazil on 2006-06-27
I've been having a problem with my ethernet and wifi connection on my Toshiba Tecra S2 laptop.  They have been working fine since being autodetected, but they stop working off and on (nothing goes down, they just don't work).  I don't just mean the internet, but network stuff in general like pinging local computers.   Eventually they start working again sometimes hours later, or after a system reboot.  Other distributions like SUSE and Debian worked fine, and so did Windows.  

Anyways, I heard several people had this problem, but only one guy had a possible solution.  He changed his kernel from the generic kernel to the K7 kernel.  I was wondering how to do that.  I'm used to compiling my own on Debian, but have never done it in Ubuntu, and don't want to screw up any nice package configurations.  But I have the 2.6 kernel but all the headers and stuff are for the 2.4 kernel.  I was wondering why the other images are for 2.4 and not 2.6?  I just want to swap to a specific architecture to see if that fixes the problem.  Is that possible?

---

### Post by John.Michael.Kane on 2006-06-27
For intel spec cpu
sudo aptitude install linux-686
sudo aptitude install linux-headers-2.6.15-23-686

For AMD 32 bit
sudo aptitude install linux-k7
sudo aptitude install linux-headers-k7

---

### Post by Gtaylor on 2006-07-29
Look under "Restoring USB/Network" on this page:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4)

---

