---
title: "Xubuntu Installation problems"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by Dod_basim on 2007-05-07
Hey

I try to revive my old laptop (after a success revive to my new laptop with ubuntu Fiesty) with Xubuntu 7.04.
Same as Ubuntu i'm asked to boot from the Xubuntu CD but the system can not even run from the CD.
It takes hours to get the GUI and when it gets there you can't hit the install button.
My old laptop is Fujitsu-Siemens P-III 128 MB, Windows XP is installed and working very very slowly.
Is it too old to run Xubuntu?  how can i know if there is a hardware problem with CPU, memory or HD?

---

### Post by leg on 2007-05-07
I had the same problem on a desktop with 256mb of ram and 128 is the minimum requirement. I fixed my install by putting xubuntu 6.10 on it and that was much more responsive and is now running very nicely. You could look at the [fluxbuntu]("http://www.fluxbuntu.com/") distro if you really want to go lightweight. I have never used it but I have used fluxbox and it is very nice. If you really want to go light you could attempt a [DSL]("http://www.damnsmalllinux.org/") install on your laptop.

---

### Post by Dod_basim on 2007-05-08
thanks,

before i try those other-like distros i would like to publish the output of one of first steps of installation
it stuck for hours (or if i try ubuntu fiesty it's just stuck) on this output


> [ 202.908000] Buffer I/O error on device fd0, logical block 0
[ 241.012000] Buffer I/O error on device fd0, logical block 0


anyone? why if i'll try the Xubuntu 6.* it will work for me?

---

### Post by Topsiho on 2007-05-08
fd0 is your floppy drive, or more precise, the first one (\:A in MS speech).

If you don't need it you can try and remove it, if you need it you could replace it with another.

You of course can replace it later if the present floppy drive proves to be the culprit.

Topsiho

---

### Post by Dod_basim on 2007-05-08
hey

so, i have disabled the fd0 (with BIOS settings), yeah it skiped that error output but still it is not working.

:\

---

### Post by Topsiho on 2007-05-10
Did you also try to remove the fd0 physically? Just removing the cables from it (remember though how they were attached, so you can easily put them back. The flat cable has a red line on one side).

If this does not make a difference than I am sorry that I can not help you...

Topsiho

---

### Post by Dod_basim on 2007-05-10
thanks

the only resort i had was to install Dapper --> Edgy --> Fiesty......


--> = upgrade

---

### Post by rub1m on 2007-05-11
I had the same problem installing xubuntu-desktop on my laptop. The problem was that xubuntu-desktop requires at least 192MB of RAM to run & install, but I only have 128MB.
I downloaded xubuntu-alternate instead and I successfully installed it! xubuntu-alternate only requires 64MB of RAM, but 128MB is recommended

---

### Post by chang47 on 2007-05-11
Having installed 4 times on my old Dell Celeron with 128M RAM, I can tell you that the best bet is to use the alternate install CD.  It should get you somewhere.  I am running very snappy now, it is as fast or faster than the old WinME running on it.

BTW you will run into problems if you plan to use Ktorrent or Azureus that came with the install disk.  These are known problems reported in the forum.  Solutions are to download the latest versions of these software and do a manual install.

You may also meet partition problem with the Desktop CD.  That is a confirmed bug.  Check Launchpad for details. 

The lesson I learn is to keep the system simple and use lightweight applications.  Azureus is a Java app so it will take more CPU as it needs JVM which is another layer of software to run.  So I chose Ktorrent.

Good luck!

---

