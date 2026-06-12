---
title: "Latest kernel upgrade broke SATA support?"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Michael Steinberg on 2008-02-06
One of the benefits of upgrading to Gutsy for me from Feisty was that I didn't have to use the command line on each boot to keep my SATA HD from spinning down all the time. In Feisty the drive would spin down after 30 seconds or so unless I executed an hdparm command as root.  Gutsy seemed to control the HD properly and keep it active as needed, a nice improvement. 

Yesterday I installed the latest kernel upgrade to 2.6.22-14and the drive started spinning down again. I edited the menu.list order to reboot from the older kernel and all is fine.

Anyone else have this problem?

---

### Post by markitect on 2008-02-06
Kinda a hack, but if you really want to use the new kernel you could just add an init script to run the hdparam on bootup.

---

### Post by Michael Steinberg on 2008-02-06
I tried that in Feisty and it never worked...No, I didn't have a problem with the old kernel anyway.

---

