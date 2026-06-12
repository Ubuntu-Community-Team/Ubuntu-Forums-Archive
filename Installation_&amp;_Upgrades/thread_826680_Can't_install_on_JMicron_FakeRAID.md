---
title: "Can't install on JMicron FakeRAID"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by Dr.Yak on 2008-06-12
I can't manage to get linux to install on a computer with
- a Gigabyte GA-MA790FX-DQ6 motherboard
- 2x Samsung Spinpoint 300GiB as RAID-0 array on the jmicron fakeraid controller (called GIGABYTE-SATA in the BIOS)

The fakeraid array works flawlessly in :
- Vista x84 (using the drivers provided with the board)
- Linux System RescueCD 0.4.3 - using 'dmraid' to activate the array and stock kernel to access the controller.
(and of course in FreeDOS too, but in that case it's the BIOS handling the array anyway).

*BUT* whenever I try to boot on an install CD, either Ubuntu 7.10 or 8.4 (same also happens with openSUSE 10.3 and 11.0 beta) :
- Suddenly the metadata of the first disk in the fakeraid array becomes inaccessible.
- I can't do 'dmraid' from the installation environment - dmraid can't detect the metadata on the first disk and won't activate the fakeraid array. (both disk are readable, though : ahci driver still gives access to the controller. And if I want, I can access the array by manually assembling it with 'mdadm' and carefully using the same exact parameter as in the fakeraid bios).
- The fakeraid bios it self can't detect the array. The first disk is reported as "non raid" and the array is broken.

This situation persist until I power-cycle the machine. Then the array is back again, accessible in the BIOS, in Windows x64 and in SysRescCD.

So in short, the controller works with ahci, but whenever I try booting an installation disk, the raid fails, including in situation where it worked before (bios, linux sysresccd) until I switch the machine on/off.

Has anyone had similar problem ?
Can someone help me how I should proceed to try installing linux on that machine ?

thank you very much.

---

