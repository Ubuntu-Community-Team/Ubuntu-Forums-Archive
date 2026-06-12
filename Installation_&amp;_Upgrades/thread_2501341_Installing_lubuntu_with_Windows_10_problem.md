---
title: "Installing lubuntu with Windows 10 problem"
date: 2024-10-03
forum: Installation &amp; Upgrades
---

### Post by dosh on 2024-10-03
I am trying to install lubuntu on a laptop (Dell Latitude) that has Windows 10. Wanting to dual boot with the current Windows 10 and lubuntu through Grub. I have hit the following problem. As I am loading from a USB thumb drive. The installation comes back "No partition found to install on" (or similar). KDE partition manager only shows the Thumb drive not the hard drive. After some searching I noticed this was due to it having SATA as  Raid On not AHCI (please note Fast Startup was turned off). After changing this to AHCI (had not gone ahead with the installation) I tried to boot into Windows. It could not. Now the question is if I do change it to AHCI so to find the hard drive (which I do when I have AHCI set I find in KDE partition manager so presume install will) do I then install lubuntu and then change back to Raid On will I be able to access lubuntu. If not how do I overcome this problem to be able to dual boot via Grub for both indows 10 and lubuntu?

---

### Post by nicolasdentremont on 2024-10-03
When I first installed Ubuntu alongside Windows I had to switch from RAID to AHCI in the BIOS every time I wanted to boot the other OS.

I got it working by following the instructions here [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/) for configuring Windows for use with AHCI. 

I would definitely recommend you have all your important stuff backed up before you start. Windows failed to boot when I attempted to switch over the first time and I had to follow the instructions on that page for using startup repair.

---

### Post by dosh on 2024-10-03
Thanks  worked it out. Yes did as you said able to use Msconfig in Windows to boot to Safe Mode on restart then changed to AHCI  then reset the boot so not booting to safe mode and this worked then able to fid the hard drive and install lubuntu.

---

