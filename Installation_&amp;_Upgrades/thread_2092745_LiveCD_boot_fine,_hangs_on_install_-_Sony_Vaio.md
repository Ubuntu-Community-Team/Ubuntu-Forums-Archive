---
title: "LiveCD boot fine, hangs on install - Sony Vaio"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Woodaaay on 2012-12-08
Hi Guys, 

I'm trying to install Ubuntu on my Vaio VPCEB15FG but installation hangs at same point every time. The laptop had windows 7 installed until something went haywire, tried to recover and couldn't run any recovery methods (internal partition or DVD failed)

So I downloaded 10.1 x64 and 10.1 x86 (torrent alternative) and burnt to DVD at slowest speed. Boots fine but after I select no wireless or connect to a wireless network and click continue it hangs without loading the next screen. It doesn't matter which option I select. Tried with nomodeselect also and no dice.

I can run it from the LiveCD and there are no video, network or audio issues at all. 

Any advice on where to go from here? I previously thought the HDD was gone but I did the disc check from the advanced boot menu and it passed. Ubuntu experience 0.

Many thanks.

---

### Post by Woodaaay on 2012-12-09
Solved (In a way). Removed the HDD and installed x86 version to 8GB USB using noacpi, nolapci, no mode set. Formatted Windows 7 partition using Disk Utility. Relaunched Vaio recovery centre and it's now reinstalling Windows 7 :) 

Next step to shrink 7 partition and try again to install Ubuntu 12.1 on clean partition!

---

