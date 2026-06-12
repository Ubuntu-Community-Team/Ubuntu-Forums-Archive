---
title: "Wireless help needed"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by gillyphoto on 2008-11-02
Hello all.
I am new to this forum and ubuntu in general.  I have read many helpful posts that made me decide to dive in and try ubuntu with my new laptop.  That and vista is a disaster to work with:).  I have read many posts here and in other places about doing a dual boot.  Here is my system specs
Dell XPS M1330
Intel T8100  2.10GHZ
4.00GB RAM
320 gb hard drive 5400RPM
nvidia geforce Go 8400 GS
dell wireless 1505 draft wlan mini card
I have vista installed on 100GB section
I have a 10 GB swap file and I also have media direct installed.
The rest of the hard drive is set up for Ubuntu
I have tried Vista and it seems to be working correctly and everything seems to function properly.  However I cannot seem to get my wireless to work in Ubuntu.  I have tried several methods for getting it to work that I have found but none seem to work.  Any help with this would be greatly appreciated.  I installed Ubuntu 8.10.  I am not extremly savvy around computers but I would like to learn.  
Thank you in advance

---

### Post by David Ehrenberg on 2008-11-09
After fighting to create the boot disc from a memory stick (my version of Nero CD burner doesn't recognize .iso files, had to get another burner), I installed Ubuntu 8.04.

Installation was straight forward, but my wireless card (plugged into the card cage) was never found--I checked with <lspci -nn>

So, I tried to use the setup disc that came with the DWL-520 (non plus version), but of course this didn't work, it's MS Windows centric.

So, I tried to download and compile <ndiswrapper>. Didn't work, won't compile.

So, I tried downloaded a driver for DWL-520. <make> claimed it was up-to-date, but I couldn't located the executable.

I think I'll just reinstall a fresh version of XP.

I'm surprise the support for cards in the cage was not included in the release. The operating system didn't locate the card and the initial set of user questions never asked.

Are the releases really this crude, or have I missed something?

DE

---

