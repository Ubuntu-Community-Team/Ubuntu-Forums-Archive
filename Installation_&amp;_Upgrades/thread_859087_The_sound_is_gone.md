---
title: "The sound is gone"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2008-07-14
Under Kubuntu 7.10 my sound worked fine. Now that I upgraded to 8.04, I hear nothing from my speakers. After doing the upgrade, I used aptitude to upgrade nearly all my upgradable packages. The only package I did not upgrade was devscripts which doesn't seem to have anything to do with sound.


david@Achernar:~$ sudo lshw -C sound
[sudo] password for david:
  *-multimedia UNCLAIMED
       description: Multimedia controller
       product: PCI2040 PCI to DSP Bridge Controller
       vendor: Texas Instruments
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm hotswap cap_list
       configuration: latency=0
  *-multimedia
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: 6.1
       bus info: pci@0000:00:06.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
david@Achernar:~$

Any advice or suggestions are welcome. Thanks!

---

### Post by Pumalite on 2008-07-14
Open up your backports and do a dist-upgrade.

---

### Post by David J Bush on 2008-07-14
[SIZE=2]Under "Software sources" I selected everything:
[/SIZE]
[IMG]http://img398.imageshack.us/img398/7144/ubuntuswjz7.png[/IMG][IMG]http://img381.imageshack.us/img381/9435/backportsxz9.png[/IMG]
[SIZE=2]The "important security updates" checkbox was uncheckable. I hope this is what you mean by "open up the backports."

I upgraded all the packages under aptitude, and rebooted.

david@Achernar:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@Achernar:~$[/SIZE]

[SIZE=2]Still I have no sound.[/SIZE]

---

### Post by Pumalite on 2008-07-14
Post:
uname -a

---

### Post by David J Bush on 2008-07-14
[SIZE=2]david@Achernar:~$ uname -a
Linux Achernar 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
david@Achernar:~$

I should add that my machine is amd dual core 64 bit, but I am running 32 bit Intel Linux on it.[/SIZE]

---

### Post by bushda on 2008-07-14
Open up your volume control and make sure that alsa doesn't have it muted by default. 


...and hi from a David A. Bush :)

---

### Post by Pumalite on 2008-07-14
Try:
sudo apt-get install linux-backports-modules-generic
Reboot
Try lshw -C sound again.

---

### Post by David J Bush on 2008-07-15
[SIZE=2]I did as you describe.

david@Achernar:~$ sudo lshw -C sound
[sudo] password for david:
  *-multimedia UNCLAIMED
       description: Multimedia controller
       product: PCI2040 PCI to DSP Bridge Controller
       vendor: Texas Instruments
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm hotswap cap_list
       configuration: latency=0
  *-multimedia
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: 6.1
       bus info: pci@0000:00:06.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
david@Achernar:~$

The sound is not muted. It's also still not there. I appreciate your help![/SIZE]

---

### Post by David J Bush on 2008-07-16
[SIZE=2]No sarcasm was intended. I do appreciate the help, even though the problem has not yet been resolved. I hope we can continue to track down the bug. Thanks.[/SIZE]

---

