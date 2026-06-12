---
title: "Dual Boot - Windows + Ubuntu. can't boot ubuntu"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by xcvbnso on 2016-07-29
I have no way to boot Ubuntu. everytime I restart the PC Windows 10 loads, I don't have the GRUB boot loader or whatever is called installed... Ubuntu was well installed, the partitions are created, used 25GB partition. what can I do?

---

### Post by ajgreeny on 2016-07-29
You probably have Windows 10 installed in UEFI mode and may have installed Ubuntu in BIOS/legacy mode; does that ring any bells?

Did you install from a DVD or USB and when you booted to that did you notice if it mentioned UEFI at the start of the named device that you used?

Boot repair from my signature below may help us so boot to a live Ubuntu system again and follow the instructions there to run the Boot-Info-Script; don't at this stage run the default repair but just that script and post back here the pastebin link it gives you.

---

### Post by xcvbnso on 2016-07-29
problem solved! my bios was set to Legacy, switched to UEFI, than used the Boot repair to put the entry on the boot sequence. now it's working fine, thanks!

---

### Post by ajgreeny on 2016-07-29
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

