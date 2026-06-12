---
title: "Can't install freezes"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by xanfantasy on 2011-09-04
I am trying to install Ubuntu or one of it's variants and I am having no luck. The installer crashes either after the keyboard selection (while clicking trough or waiting for the Waiting on you message) or in the case of the Alternate installer and Mint 11 it's while it is installing/copying files to the HDD.

Computer Specs
Asus 1005HA
Intel Atom N280 (1.66 ghz)
1 Gb ram
160 Gb HD
Flashed latest BIOS before attempting anything

Attempted versions
11.04 Desktop
11.04 Alternate
Backtrack 5
Backtrack 5 R1
Mint 11

I have also tried to find information on possible solutions. I have tried each of these methods on each of the variants.

One person suggested it's the sector size on the hard drive and suggested running the following command:
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

Another suggested to turn off acpi.

Others have suggested that it could be cause by bad images which I have checked and all downloaded correctly.

I have tried them all on both CD/DVD and USB.

Any help would be most appreciated as I am tired of a slow running Win XP installation on this machine.

---

### Post by JD8182 on 2011-09-04
[http://ubuntuforums.org/showthread.php?t=1633873](http://ubuntuforums.org/showthread.php?t=1633873) "just an idea" and maybe you have already seen this Thread..

---

### Post by xanfantasy on 2011-09-05
I did try the IDE/AHCI thing and it also did not improve anything.

As far as the dummy sd card I lost mine long ago so the slot is just empty.

---

### Post by xanfantasy on 2011-09-30
I'm not sure what the problem is or how to solve it but I removed the hard drive from the netbook. I used an external dock with my laptop to install to the netbook HD and it worked but once I replaced it in my netbook it will start and work for a few minutes but will then all input will freeze. Applicaitons would still update but I could not use the track pad or keyboard. Just to try it, I plugged and external mouse in and it worked to move the cursor but I still couldn't click on anything. I've given up on this netbook and will eventually get a new one.

---

