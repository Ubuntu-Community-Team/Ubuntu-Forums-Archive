---
title: "Errors after install - possibly grub?"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by GingerGraham on 2012-04-22
Hi,

I'm wondering if anyone can point me in the right direction to resolve an issue I'm having?

I'm a relative newb to Linux although not to IT in general.  I've installed various versions of Ubuntu in to Windows hosted VMs as well as on to a couple of laptops and played about a bit but not much else.

The issue I'm having is on an old HP Compaq nx6310 laptop I have which I'm using to get more in depth with Linux.  I did manage to successfully install a 64-bit version of Linux Mint on to it, but after coming up against some issues when trying to install a few bits of software I thought I'd switch to a 32-bit OS instead, which is where my issues began.

When I installed Mint 12 32-bit it wouldn't boot.  As soon as the BIOS finished the an error message would appear on screen:

error: out of disk

Nothing else at all.

I then went back to the Mint 12 64-bit which previously worked and the same error came up, again the system would not boot to the installed OS at all.  In both cases the install seemed to happen fine with no apparent errors.

I've now tried the 32-bit version of Ubuntu 11.10 and I get the errors as follows:

error: out of disk
error: no suitable mode found
error: no video mode activated

All 3 errors appear on screen immediately after BIOS POST, but now after a few seconds Ubuntu does boot and seems to be fine.

After researching the out of disk error I tried re-installing and updating grub as per a number of forum posts without any success.  So I'm now at a loss as the hardware is fine and before my messing about the first install of Mint 12 64-bit and before that an XP installation were both working fine.

Any help or suggestions would be gratefully received but if I could ask if I need to head for the Terminal (which I've no problem with) please give me the full commands I'm likely to need, the number of forum posts saying type "sudo grub-install" without mentioning anything about "/dev/sdXY" sent me round in circles for hours!

Thanks in advance


Graham

---

### Post by tmaranets on 2012-04-22
> error: out of disk
error: no suitable mode found
error: no video mode activated
"error: out of disk" seems like a storage problem or it could be something else.

---

### Post by GingerGraham on 2012-04-22
Hi tmaranets, thanks for your input so quickly.

Having gone round this issue all day I've come across that said before and had thought about it but I just can't think how that would be the case.  The laptop is old but the HDD is a new replacement WD Caviar Blue I put in maybe 6 months ago.  Also, as I mentioned after those 3 errors Ubuntu does actually boot and seems to run fine (I using it now).  Also the Disk Utility reports that the disk is healthy.

Confused....

---

### Post by keforex on 2012-04-22
Did you install using the whole disk? That helps. This 'out of disk' message comes from the OS or comes from the BIOS? If it's from the OS (or grub) I'd try to re-install using the whole disk, letting the installer format the HD and do all the partitioning automatically. Should boot fine, unless you have a really small HD in there. You've mentioned it's an old computer...

And when you get the grub menu after the first boot, press F6 and choose nomodeset. Press Esc and then enter to boot it up. Nomodeset prevents the screen from going into a resolution that is not supported.

---

### Post by oldfred on 2012-04-22
You mention new larger hard drive and older system. Does this system have a BIOS that boots only from the first 137GB of a drive but your system partition is beyond the 137 limit. Maybe all the boot files are currently inside the 137GB so it does boot for now.

Some just install a smaller system partition (/) where the full system partition is inside the 137GB. And the rest of the drive is /home or data partition(s). Others use a separte small /boot partiiton which most desktops do not need but servers or systems with RAID or LVM may need. New versions of grub2 often directly boot into RAID or LVM so /boot is not always needed as a separate partition.

---

### Post by GingerGraham on 2012-04-23
Hi Guys,

Again, thank you for your input.

Up until the last attempted install I have let the installers from both Mint and Ubuntu do their thing and partition the whole disk as it seems fit.  In my last/current attempt I came across a forum that suggested manually setting up the partitions.  So I have done this and set up the following partitions in the order below:


[LIST=1]
[*]500MB as /boot
[*]240GB as /
[*]The rest of the disk 9GB(ish) as Swap Area
[/LIST]
keforex - you mention the grub menu and pressing F6/Esc, I don't get any form of menu.  I get the BIOS splash screen with the usual boot options, then the screen pauses (blank) for 2-3 seconds then the error messages appear for 10 or so seconds before the OS then boots successfully.  Should I be seeing something in that 2-3 seconds?

I'm also confused around the potential for older BIOS/partition size issues as I did have Mint 12 64-bit installed and running with no issues at all.  But now when I try and reinstall I get the "out of disk error.

I'm sure I'm missing something, I'm just lost as to what.

---

