---
title: "Trouble with 10.04 install and Gigabyte MA785GMT-UD2H"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by gcornelisse on 2010-05-13
I can't seem to get my new Gigabyte mobo to work with 10.04 or 9.10.  After everything I've tested, and from experience, I'm assuming at this point its a mobo issue. After the installation process is complete it restarts and GRUB starts.  It just flashes up the first boot message and then the monitor turns off and the HD light goes out, and there it sits.

The only boot message I see:
shpchp: shpc_init: cannot reserve MMIO region

I've..
- installed Windows XP with success
- updated BIOS to latest version
- tried default, optimized, and fail-safe BIOS settings
- set BIOS to use Natural IDE instead of AHCI
- ran MemTest86+ 4.10 with no errors
- shuffled around the RAM
- tried one and two RAM modules
- made sure HD was in SATA2_0
- tried two different IDE CDROM drives
- tried booting without CDROM drive connected
- tried different hard drives
- disconnected the power several times
- removed the extra Intel NIC
- checked dmesg and several other logs, but didn't find anything that jumped out at me

One other quirk I seem to get randomly is while reinstalling, the partitioner basically says it can't change the HD because its in use.

Gigabyte doesn't list my RAM at all in their compatibility list. But, memtest and windows XP doesn't seem to have a problem with it.

I'm now looking at boot parameters, but I'm not sure what to try without any real information to go on.  Anyone have any ideas or what I should look for?

Thanks, Gary

Specs:
Gigabyte MA785GMT-UD2H
AMD Phenom II X4 965 3.4 GHz Quad Core
DDR3-1600 PC3-12800 2 sets = 4 sticks = 8GB (F3-12800CL9D-4GBNQ)
WD Caviar Black 750GB 16MB
450Watt PS

---

### Post by ronparent on 2010-05-13
You have a later version of my setup. Although I had some problems with the alpha thru rc versions of 10.04 I had only minor glitches with the final release. So you definitely should be able to run it. Some questions:

1) Are you using the onboard video (probably nvidia)?
2) Have you run the live CD or are your problems during or after install?
3) I presume your ram is not edd?

Regarding partitioning, The partition you want to work on must be unmounted - a left click option in gparted.

If you haven't tried to run the live cd 1) boot to the cd and bring up the menu by hitting any key (ie spacebar) immediately after the bios screen passes. 2) after selecting language, hit F6 to bring up the list of boot option - you might not need any at this point so just hit esc to retun to the main menu. 3) a boot line will now be listed on the boot menu - hit end to position the cursor at the end of the boot line, back arrow to the end of "quiet splash" and backspace orver them to remove them for the boot. 4) hit enter to boot. Even if the boot process stops you will see the point it stops. 

If the boot is not sucessful, the likeliest cause may be to add nomodest to the boot line - through the F6 option if you like. 

Report back on how your doing. I or someone else can give you additional help if you need. 

Also note, you will probably have to edit the grub boot line with the same default to sucessfully boot after the system is installed. Once into the system you can permanently add any needed boot parameters by editing the /etc/default/grub file. Can give you explicite instructions as you need. Good luck.

---

### Post by snkiz on 2010-05-13
DDR3 is triple channel ram and you have an even number of sticks. could that be it?? (I honestly don't know, just a guess.) Have you tried pulling ram, use one stick at a time?

My Gigabyte M68M-S2P is dual channel and there is a switch for single/dual in the bios.

I've installed xp with bad ram before, windows don't pay very good attention that way.

Edit: I also have onboard Nvidia and nomodset was not necessary it fell back on its own.

---

### Post by gcornelisse on 2010-05-13
I may have made a little more progress.  Grub is now consistently dumping me into a "grub rescue>" prompt.  However, I'm supposed to be able to "ls" the (hd0,1)/boot/grub directory, but it says the file or directory is not found.  That makes me think grub is missing.  I know I told the installer to install it.  

I'm trying to build a server, so I don't have the desktop/live CD.  I'm downloading the ISO now.  Hopefully, that will allow me to mount the drive and install Grub manually if its really not there. What's odd is that 9.10 did the same thing.  I just can't think of a good reason why grub wouldn't have been installed, or why I can't see it if it is.

---

### Post by ronparent on 2010-05-14
The live CD will help you find any needed boot parameters. Also to fix grub.

---

