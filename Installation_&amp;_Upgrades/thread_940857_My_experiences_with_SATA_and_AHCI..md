---
title: "My experiences with SATA and AHCI."
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by zend on 2008-10-07
The following details my issues with setting up a new dual booting machine (XP and Ubuntu) with SATA and AHCI. I'm posting it here in hopes that it may help others that run into the same issues I had.

Last night I was busy trying to move my system over to a new computer. It took a lot longer then I expected. Here is my story:

I bought a new MOBO (DFI LP Jr P45-T2RS), CPU (Intel Core2Duo E8400) and HDD (Seagate 500GB). My idea was to install windows on the new drive, and move my Ubuntu drive from my old machine to my new maching.

I had installed windows XP on my new drive and got all the drivers installed. This worked no problem.

I then pulled my Ubuntu drive from my old machine and put it in the new machine. If I set the windows drive as the boot drive windows booted. When I set the linux drive as the boot drive grub would come up, but Ubuntu would not load. So I thought my Ubuntu install wasn't playing nice with the new hardware and I'd re-install Ubuntu. (I know this is sort of a Microsoft way of thinking, but I don't mind having a nice clean install to work with.)

Since I was going to fresh install, I burned a new Ubuntu *.04 64bit disk. When I tried to boot the live CD it crapped out every time. It would always bring me to a Busybox command prompt. I tried the 32bit version of Ubuntu 8.04 and it did the exact same thing. It didn't matter what I choose on the Ubuntu CD list of boot choices. Doing some reading I thought it might have something to do with the mode of the Serial ATA. It was by default set to IDE, so I changed it to AHCI.

In AHCI mode, the SATA CDROM would not boot. The live CD didn't even recognize as bootable, so I tried just booting to the Ubuntu drive and my original install of Ubuntu worked great. Well my Ubuntu install works great, so I figured all I'd have to do is update grub and I could dual boot, but when I tried to boot into windows it gave me a BSOD, since windows was installed in IDE mode.

I thought I'd just re-install windows since it was basically a fresh install anyway. Of course in AHCI Mode the CDROM would not boot. I had to hook up an IDE CDROM and boot widows.

Finally, I reinstalled windows in AHCI mode and then my computer will boot into windows when I choose that drive as the default drive, and would boot into linux when I choose that drive. Grub would boot the linux drive, but it would not boot the windows drive.

I booted into Ubuntu and re-install grub to the MBR of the windows drive. I fix the menu.lst for the grub menu and my system is now finally dual booting. Oh yeah. And I had to change the BIOS to choose the windows drive first. At that point it is 1:30 AM and I was barely keeping my eyes open. Not to mention I had to work the next day. Now today I still have to re-setup my whole windows install. (Drivers, etc.)

So that's my story. Hope you found it interesting and possibly helpful.

---

### Post by consilience on 2008-10-07
just a thought - if you use nlite you can slipstream all the service packs and drivers, plus create an unattended install.  i've had to install windows like 10 times and nothing is easier than just popping in the disk and letting it do its thing.

---

### Post by zend on 2008-10-07
I'll check that out.  Thanks for the suggestion.  May save me time in the future. 

I'm sure there were probably other things I could have done differently to speed up the process.  Suggestions are always welcome.

---

