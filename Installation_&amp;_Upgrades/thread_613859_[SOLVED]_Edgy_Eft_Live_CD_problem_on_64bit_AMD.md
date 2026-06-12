---
title: "[SOLVED] Edgy Eft Live CD problem on 64bit AMD"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by tybalt on 2007-11-15
Hi,

i have been using Dapper for a while (i386 version), and now would like to install Edgy-eft with a 64 bit config (AMD64 processor).
Live CD shows nothing but a blank screen with a very poor static UBUNTU logo in the middle. System gets halted after that. Thus, i cannt even start the installation process!!  :(

Is there any known problem on the ISO files?
Is ther a way i can track the source of the problem instead?

I have been checking other forums and it seems there are graphical issues on the 64 bit systems... but the  are related to "*installed*" systems, not to the live CD.

Thank you so much for your help!

---

### Post by tybalt on 2007-11-16
It is strange i answer to myself... just in case my conclussions are useful for someone out there...

My experience is the following:
1. I installed my first Ubuntu on Dapper version, for i386, from a live CD one year ago. It worked fine.
2. I quickly tried to upgrade to AMD64 versions, both Dapper and Edgy-Eft, but the live CD was not working at all. The live system did never start running. The effect was always the same: a black screen with a clamsy ubuntu logo and system crash.
By adding vga=774 and noapic nolapic parameters in the running menu, i could finally bring Dapper Live system up and running, and even perform my first installation of the AMD64 version!!
... which never worked! :(
At system start, with my successfully installed Dapper AMD64, the result was the same: black screen and black&white ubuntu logo; system crash.

I could notice 2x possible causes: (a) system crashes right after setting up the IRCs for SATA devices (which i have not), and (b) the screen looks like some issues with my graphics board.

3. Last night i installed Gutsy version for AMD64, and it went sooooo smooth that i can do nothing but share my happiness with you! :)
After my first login into the system installed the upgrades for the nvidia and the "regular" upgrades reported by the system; everythig went fine.

CONCLUSSION:
my suggestion for those beginners moving to AMD64 version, try Gutsy release!

My system info as follows:
AMD64 Athlon 3500+
Motherboard: Asus M2N4-SLI
Club 3D 7300GT - Nvidia NV73 graphics board
PATA HDD: 250 GB total space, 50GB partition for /, 2GB partition for Swap; Rest is Windows, which i presume will be removed soon!!
2Gb Memory

Hope this is info is useful for someoue out there...

---

