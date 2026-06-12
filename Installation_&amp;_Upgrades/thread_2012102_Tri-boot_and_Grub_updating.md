---
title: "Tri-boot and Grub updating"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by cogset on 2012-06-28
Hi all,I hope this is the right section and the thread title is explicative enough,however,this is where I may use some help:I've got a slightly complicated set-up with two hard disks,one has a dual-boot Ubuntu 10.04/win 7 installation,the other a tri-boot Ubuntu 10.04/Mint12/Mint Debian installation,this was the last one to be added and has all its partitions ( /root and /home for all three systems plus a shared swap) set up as logical partitions with the only exception of Ubuntu root which is on the first primary partition.At the time I  installed this tri-boot  system,first I've set up Mint and Mint Debian without installing the bootloader,as the last step I then installed Ubuntu with its bootloader and it has been working (as far as I can tell) perfectly since,Grub correctly picked up all pre-installed systems including the other hard disk and (aside of having a very long boot menu,obviously ;)) I've had zero glitches.
Too bad that I now need to wipe the Mint 12 installation (too buggy for me on this machine) and replace it with Mint 13 : I reckon I can just install Mint 13 as before,overwriting the existing Mint 12 /root and /home partitions without installing the Mint bootloader,but what happens next? I doubt that this time Grub will automagically pick up this change and update itself,so how do I properly update Grub ?

---

### Post by darkod on 2012-06-28
After you are done replacing the Mint install, simply boot the ubuntu installation that is controlling grub2 and in terminal run:
sudo update-grub

It will rescan all disks for OSs and update the boot menu.

---

### Post by cogset on 2012-06-28
Excellent,thank you very much.

---

