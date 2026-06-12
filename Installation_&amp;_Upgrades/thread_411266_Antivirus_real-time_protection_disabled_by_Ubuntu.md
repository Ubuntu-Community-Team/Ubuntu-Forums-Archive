---
title: "Antivirus real-time protection disabled by Ubuntu?"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by pnsubuntu on 2007-04-16
New to Ubuntu and Linux (groans all round..!) and have one problem with my first installation - everything else has been pretty straightforward; a credit to the distro.

My system is dual-boot (separate physical disks) with XP, and since installing Edgy I have noticed that the real-time protection for my CA Antivirus in XP refuses to start. XP is on one 80Gb disk, running as slave on IDE 0 (following a CD drive), Ubuntu is on another 80Gb drive running as master on IDE 1 on it's own.

BIOS is set to boot from HD, and I have edited grub's menu.lst to make sure the XP is default for the rest of the family (this didn't make any difference).

Questions:

1. What is it that the antivirus doesn't like? Something written to the boot sector of the XP disk? XP not being on a master?

2. Is it possible to force the writing of (MBR?)  to the Ubuntu disk instead of XP? Would this fix it?

3. If this is insoluble, does anybody know a Windows AV that doesn't mind whatever it is that Grub is up to?

Many thanks for any constructive comments...

Paul

---

### Post by Zimmer on 2007-04-17
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I believe it is possible to have GRUB loaded on a Linux partition. You would need to change the BOOT order in BIOS for that disk to be first on the list. You would also need a valid entry for the Win XP disk in the menu.lst file and make that the default . 
I also think you will then need to restore the MBR on the WinXP disk so it does not contain GRUB.

As for the AV. No idea why it is unhappy. I used AVG on a dual boot WinXP/Mepis installation some time ago and it seemed to work OK.
 It has a Resident Shield feature which sounds much like your real-time component in CA.

Hope this helps
Regards

Zimmer

---

### Post by pnsubuntu on 2007-04-21
Thanks for the response, I don't really want to poke around and mess up my sweetly running Windows system if I can help it though.

I have uninstalled my CA antivirus, and am trialling BitDefender, which does run it's realtime protection OK, and seems stable at the moment.

Cheers,

Paul

---

