---
title: "Installing Edgy on OLD computer"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by KX36 on 2007-04-02
I'm trying to install any kind of linux that will look enough like windows for barely computer literate linux newbies to use. I'm trying to install it on a very very old computer (1998 Compaq).

Pentium3 500Mhz
128MB PC100 SDR-SDRAM
10.2GB hard drive

I am not new to linux myself, but the computer isn't for me. Although I always hear that linux is good for crappy old machines that won't run NT based windows, this is the first time i've put linux on an old machine.

I downloaded the alternate install CD of Ubuntu 6.10 and tried to run the text install (as it only has 128MB ram) and it gets as far as trying to detect the hardware, then after it gets to 100%, the foreground "window" of the installer disappears, leaving it frozen in the blue background.

Is there any way to get this to actually install, would I have a better chance of detecting the hardware if i could find myself a copy of Ubuntu 4.10 (Warty), would it even be worth trying Warty. 

(it only really needs to work on those low specs and run a web browser and OpenOffice.org)

PS. I was quite disappointed with these results. after hearing so much about running linux on old machines, when i come to finding a distro for it I find that none with a desktop environment will really run on <192MB ram (i tried xUbuntu for the lighter weight xfce also in vmware; but looking at the memory usage, they were both about the same)

---

### Post by cyberdork33 on 2007-04-02
I have ran Ubuntu 6.10 on lesser hardware / RAM (Dell OptiPlex with a PII 350, and maybe 128MB of RAM). you should not have an issue with it actually running... as for the installer crashing, it seems odd, and would need more information to diagnose. (Could be a hardware issue, could be the CD, who knows?). I did just do an install the other day where it sat at the blue (only) screen for a few minutes before continuing on, have you tried letting it sit for awhile, or are you positive that it is "frozen"...

---

### Post by djheadley on 2007-04-02
I've never been able to get Ubuntu to install on anything with less than 192mb ram.  Maybe you could scare up some more ram?

---

### Post by serfcx on 2007-04-02
I tried once to load Xubuntu 6.06 on an old PII with 128 RAm and it wouldn't have it.
Was succesful with PCLinuxOS, Zenwalk and currently have Elive - which is Debian based.
PCLinuxOS would probably be best to show something that looks and feels like windows

---

### Post by KX36 on 2007-04-03
yes, i'm sure it was frozen, i left it for 2 hours before posting. It may have been the CD or it may have been that the hardware was too old to autodetect. I installed 5.10 with no problems and upgraded to dapper and then edgy. it took a total of about 8 or 9 hours to do all that (my 10Mbps cable line and ubuntu's excelent servers meant only 15 mins of that was the 2 actual downloads).

on the dapper-edgy upgrade, i tried to use my 6.10 alternate install CD as the 
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
page says you can, but it froze up when i put the disk in, so maybe it was the CD after all.

In the breezy-dapper upgrade i had a mild case of the PCMCIA issue, although i could still get into gnome to take it out of init.d. Really wish they'd written in the DapperUpgrades page the precautions to take BEFORE the "how to install" section. (althoguh i probably should have read all the links in the "before you start" section) i only read after getting half way through the install that there's a precaution and a "workaround" and i hadn't taken the precaution ¬_¬)

It runs fine on 128MB ram as long as there are relatively few apps open, using around 50-85MB physical memory with normal usage (plus around twice that in swap), the standard install from a LiveCD that comes on dapper and above won't run on <192MB, but the older debian text installer (from the alternate install CD) will work on 128MB ram.



I'm trying not to buy anything for this computer (it was a freebie from an office clearout), although the serial mouse that i was using on win98 won't work by default in ubuntu, i'll have to see if I can set up xorg.conf to use it or see if theres any packages i can install to get it working, otherwise i have to buy a £5 PS/2 mouse. (I'll post asking for help usung a serial mouse in another thread).

That and the spare wireless card i have is only 802.11b with only WEP support, so it won't work with NetworkManager (which gnome.org says the network-manager-gnome works with ubuntu, but i cant seem to find how to launch anything except the daemon from terminal) and it may not even work with the network it's intended to be used in. Not being able to use NetworkManager to control the wireless networks is a shame as now it has to be set up every time from network-admin.

Thanks for the replies.

---

