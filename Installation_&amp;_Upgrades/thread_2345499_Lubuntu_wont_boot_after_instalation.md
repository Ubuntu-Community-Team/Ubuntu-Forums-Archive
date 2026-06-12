---
title: "Lubuntu wont boot after instalation"
date: 2016-12-04
forum: Installation &amp; Upgrades
---

### Post by apexpredy on 2016-12-04
I am downloading lubuntu on a pc it is probably around 5-6yrs old.

Spec: BIOS A02 
Intel Pentium 4 2.20GHz 400MHz 
512KB ram 
2048 total memory with a 180GB hard disk

Issue #1
When installing it stopped on the grub_2 package which I solved by connecting to wifi 
Issue #2
After installation complete it would tell me to take out the cd and restart post restart my pc would load a black screen with a error
PXE-E61"Media test failure, check cable

PXE-M0F: Exiting Broadcon PXE ROM.
NO BOOT DEVICE DETECTED, INSTERT SYSTEM DISK AND PRESS F1 TO CONTINUE OR PRESS F2 TO SETUP MENU 
After pressing F2 and configuring boot options to boot from hard-disk first it would still give me the same error I tried reinstalling lubuntu but when I got to the install screen it said that I have Ubuntu installed I setup a custom partition (from guide) then formatted the /boot ,/ and /home mount points

---

### Post by mörgæs on 2016-12-05
The computer is much older than 5-6 years, probably from around 2002, but still it should be possible to run Lubuntu. 

If you go into BIOS you can disable PXE boot.

---

