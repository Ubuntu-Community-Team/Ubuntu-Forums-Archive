---
title: "Dual-boot crash upgrading from 14 to 15"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by nthnjustice on 2015-10-30
If anyone is willing and able, I'm in serious need of some assistance!

I've been running a dual-boot Ubuntu 14 and Windows 10 machine for a few months without any problems. I recently tried upgrading from Ubuntu 14 to 15 through the Ubuntu OS, and it seems I've crashed my OS. During the upgrade/installation there were a few error messages that popped up, but I dismissed them. The installation claimed it was successful, but upon reboot the Ubuntu 15 OS won't load.

When I start my machine I get the expected boot-option menu: [ATTACH=CONFIG]265264[/ATTACH]

When I select Ubuntu I get this (blank) screen indefinitely (it's run for >6 hours): [ATTACH=CONFIG]265265[/ATTACH]

I tried booting from a "recovery mode": [ATTACH=CONFIG]265266[/ATTACH]

But I get this monstrosity that indefinitely stops (the error seems to be "Kernel panic - not syncing: Attempted to kill init exitcode=0x00007100"):  [ATTACH=CONFIG]265267[/ATTACH]

If I truly botched the upgrade/installation, that's fine. I have everything backed up and I'm okay with performing the dual-boot procedure from scratch. The problem, and this is the part I'm terrified to skew up, is that I don't know how to reset my drives.

Here is an image from my disk management screen on Windows 10: [ATTACH=CONFIG]265268[/ATTACH]

As you can see, I have a handful of unnamed partitions. If someone could carefully instruct me on how to consolidate these drives so it's partitioned similarly to factory defaults, I would be eternally grateful. I need to know what drives I can and CANNOT modify (I really don't want to break Windows and I want to maximize free drive space). Any advice on how to fix this problem would be appreciated. 

If you need any clarification, I will happily oblige.

Thank you in advance for your help.

---

### Post by oldfred on 2015-10-31
Have you tried booting one of the old kernels? Or its recovery mode.

Did you have ppa for other software or proprietary video drivers for nVidia or AMD? Those have to be uninstalled & then reinstalled after update or you get issues like you have.

Looks like a UEFI system, so you need all those partitions. Windows have several required partitions. Vendors have one or two & then you have your Linux partitions. 

You may be able to chroot into system and finalize or fix system. 
If you elect to reinstall you should use Something Else and choose / as existing /. If /home was separate you choose it also but DO NOT tick the format box.

To see details run this from Ubuntu installer or any working Linux. Be sure to always boot in UEFI mode.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

