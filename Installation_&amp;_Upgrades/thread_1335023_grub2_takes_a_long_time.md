---
title: "grub2 takes a long time"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by cornik on 2009-11-23
I have windows7 on one disk, then i installed kubuntu9.10 on another disk partition. I have 3 disks in my desktop pc. I chose to use grub2, but when i rebooted after the install, it says grub error.  So I reinstalled grub2 following the instructions on the internet using grub-install. I installed  it on all MBRs of my 3 disks because I don't know what it will use. It works, but the problem is that it takes 40 seconds for it to display the grub menu list. It stays on "Grub Loading" for 40 seconds and I could hear the disk making a sound like it's searching for something. I have the very latest Grub2 1.97~beta4 version. So, what shall I do to speed this up? Is this a Grub2 problem? In my laptop which has Windows vista and Kubuntu9.10, grub2 just works fine. The grub menu list shows up immediately.

---

### Post by xeddog on 2009-11-23
I don't have an answer for you, but I'll take that 40 seconds.  I have Ubuntu Jaunty installed on a 1TB SATA2 drive.  I also had Windows 7 RC installed on a second 320GB IDE drive, but I wanted to try out Karmic 64-bit so I wiped out the Windows 7 and put Karmic there.  That install obviously installed grub2.  It takes TWO FULL MINUTES for me to get the Grub menu.  Any my machine ain't no slouch.  Intel I7 processor with 6GB DDR3 memory.  Well.  It's SUPPOSED to have 6GB,  I have to RMA my mobo because it apparently has a bad memory slot and I am only using 4GTB at the moment.

xeddog

---

### Post by xeddog on 2009-11-23
I just read another post where someone said that they changed the disk order in the bios to fix his issue, making the disk with grub2 installed on it as the first in priority.  I tried it and it did not work for me, but I did find something else that did.  Sorta.  At least it got me to the 45 second load time for grub2 instead of 2 minutes.  That was to change the SATA/IDE controller mode from AHCI to IDE.  The system seems to run ok too, but I don't know if it would cost me anything when running my Jaunty installation from the SATA drive, which I do most of the time for now.

anybody??

xeddog

---

### Post by cornik on 2009-11-24
After I switched the hard disks list in the BIOS setup, it now takes 2 seconds for grub to display the menu list. Thanks.

---

