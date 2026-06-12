---
title: "bad introduction to ubuntu"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by war-totem on 2005-04-07
first time poster here so bear with me.  i had been thinking about trying ubuntu to compare it to fecora core 3 that im quite comfortable with.  someone game me the cd so i figured why not.  on my box i had winxp and fc3 on two partitions.

i fired up ubuntu using the space that fc3 was using and everything seemed to work fine.  it seemed quite nice.  hwoever i had to check my mail through winxp so i rebooted and while loading up win i got the blue screen saying:  Stop 0x0000ED (0x866c29e0)  0xc00014f.

thinking i could just hop back onto ubuntu and find a solution to the problem on the net, turns out their was nothing on my hd anymore.  no ubuntu, no winxp, no fc3.  i did not particularly want my pc wiped yesterday but it did.  my question now is whether or not this is a common problem? perhaps i did something wrong or who knows what could have gone on.  id really like to give ubuntu another chance but i need to have a reasonable idea that this wont happen again.  

anyone care to gander a guess?

---

### Post by skoal on 2005-04-07
Doesn't sound like a ubuntu *install* problem to me.  The fact you rebooted into WinXP after the Ubuntu install should say something.  Maybe you did something to your WinXP partition while in Ubuntu before you rebooted.

Do you remember what you were doing just before you rebooted into WinXP?  That might help diagnose the problem.  I may be wrong but if the install process had anything to do with your problems, I doubt you would have been able to even reboot into WinXP to start.

---

### Post by bored2k on 2005-04-07
How sure are you the drives are 100% cleaned? It could be a messy GRUB configuration, or a *if it is your doomed* MBR wipe.

---

### Post by scarecrow on 2005-04-07
[QUOTE=bored2k]How sure are you the drives are 100% cleaned? It could be a messy GRUB configuration, or a *if it is your doomed* MBR wipe.[/QUOTE]
 A bad grub config does not amount to XP BSOD's- XP either boots, or doesn't.
"No Ubuntu, no WinXP, no FC3"- how do you know? Fdisking is not part of Ubuntu (or any other Linux) boot precedure- not even a windoze one!

---

### Post by jfdill_2 on 2005-04-07
[QUOTE=scarecrow]A bad grub config does not amount to XP BSOD's- XP either boots, or doesn't.
"No Ubuntu, no WinXP, no FC3"- how do you know? Fdisking is not part of Ubuntu (or any other Linux) boot precedure- not even a windoze one![/QUOTE]
Yep, I say boot up the Ubuntu Live CD or KNOPPIX or FeatherLinux and check fdisk and report back what you find.  Check the drive geometry C / H / S as reported in fdisk vs the manufacturer specs--that is normally not a cause of problems or something you would need to check, but lately I was doing a net install Debian Sarge on an old Dell GX1 and somehow the partioner gave too many cylinders to the disk drive when it modified the partition table, but that was very weird, haven't seen that before, just a hunch for something to check.

---

### Post by war-totem on 2005-04-07
bear with me here.  i tried everything i could think of for a couple hours then simply reinstalled winxp so everything is gone.

ill get back to you on the fdisk thing shortly. how about this, is their anything i should do/check before i partition and try loading ubuntu again?

---

### Post by MetalMusicAddict on 2005-04-07
I think you might have hit the same thing many of us have. Having the "Access" mode for the hard drives in the BIOS set to "AUTO" instead of "LBA" (Large Block Addressing).

---

### Post by war-totem on 2005-04-08
I think you might have hit the same thing many of us have. Having the "Access" mode for the hard drives in the BIOS set to "AUTO" instead of "LBA" (Large Block Addressing).



i looked in my bios but couldnt find the access mode.  where is it exactly?

---

