---
title: "Can't install 12.04 on new Acer V3-771G. &quot;nomodeset&quot; causes installation to hang"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by sbreble on 2013-08-22
Hi,

I have been trying to install Ubuntu 12.04 64-bit on a brand new Acer V3-771G (no-dual boot, Ubuntu will be the only OS).

System:
intel i5
NVidia GEForce 730M (optimus)
750Gb HDD
120Gb SSD
Secure boot is disabled

I have read many posts and tried many things but nothing solves the problem. Here is a summary of the problem:

[LIST=1]
[*]With UEFI enabled I get a blank screen but I can hear the sound when it goes to the setup screen. Also when I press enter I can hear the CD-ROM respond so it seems the install loaded fine but I can't see the screen. 
[*]Using "nomodeset" and/or "b43.blacklist=yes" I don't get a blank screen but the installations stops loading some modules. The exact point where it stops varies. It usually stops at "*Stopping System V runlevel compatibility [OK]" or "*Check battery state [OK]". Not sure if it matters but I do get a "*restore sound card state [[COLOR=#ff0000]FAIL[/COLOR]]" earlier on. 
[*]With Legacy Bios I also need to set "nomodeset" to prevent the blank screen but the failure is different. It gives some errors loading the installation bit it proceeds unitl I get a prompt "ubuntu@ububtu$:". If I try startx it fails saying the server fails to respond. 
[/LIST]

I'm totally lost on how to proceed with installation.
Most posts I found show solutions assuming the system is already installed but failed to boot. And it most involves changing GRUB or installing updates which I can't do since I don't have anything installed.

Any help is greatly appreciated.
Thanks
Sbre

---

### Post by bcschmerker on 2013-08-23
I can vouch for this problem, having had to fix the X.org installation **from the terminal** on an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon 64® LE-1620, nVIDIA® MCP78S chipset, planar nVIDIA® GeForce® 8200 IGP) upgraded with a Shuttle® power supply and Asus® EN210/DI/512MD3(LP) (nVIDIA® GT218 GPU) when installing Ubuntu® 12.04.1-LTS (updated to 12.04.3-LTS as of 22 August 2013), AMD64 Edition.  Historically, nVidia Corporation has been uncooperative with LinUX operations in general, and in fact the [LinUX Kernel Project](http://www.kernel.org/) had to reverse-engineer the MCP78S drivers for earlier versions of Microsoft® Windows® to get critical register data necessary to make the chipset work in LinUX Kernels 3.*.

For repairing X post-installation, needful Packages include jockey-text, nvidia-current, and nvidia-settings, all of which are in the Restricted repository.

---

### Post by sbreble on 2013-08-23
[**[COLOR=#000000]bcschmerker[/COLOR]**]("http://ubuntuforums.org/member.php?u=609186"), thanks for the reply. The problem is that I can't get to install so I can't run any post installation fixes.

I know it is possible to install on the machine because I found a few posts were people were successful but they don't give much detail on the solution. The posts just say [solved] which not much information on what helped.

Any information on how to proceed with installation is appreciated.

Thanks

---

