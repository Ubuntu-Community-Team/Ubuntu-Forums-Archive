---
title: "Moving the boot loader"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by ehennessey on 2007-05-09
My current situation is that I have 3 hard Drives

First the was:
HD1 - Edgy (Grub resides here)
HD2 - SuSE

Then I added:
SDA - Feisty

I have mostly experienced that when installing a new operating system, that new operating system is compelled to take control of boot priority.  When I added the sata drive and installed Feisty, this was not the case.

The problem is I would like to remove the Edgy disk (HD1) but I know doing so will result in failure to boot the remaining two operating systems.  

Could somebody please outline a strategy for resolving this issue?  And if this requires installing grub directly to the Sata drive, pointing in the direction of a good tutorial would be very helpful.

Thanks

---

### Post by starcraft.man on 2007-05-09
I'm not a super expert on GRUB, but I think this is the [guide]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") you are looking for.

 You can likely with it, remove your edgy HD and then pop in the CD, boot it and restore your MBR to whichever drive you designate, good luck :)

---

### Post by psusi on 2007-05-09
You can remove the drive and configure your bios to boot from the sata disk instead of the ide disk and everything will work fine.  This is because feisty installed grub to the sata disk, but right now your bios isn't booting from that disk, which is why feisty did not "take over the boot" as you put it.  Once you set your bios to boot from that disk, it will have.

---

### Post by ehennessey on 2007-05-23
Thank you for your input.  I did end up fixing the problem.  There were some strange issues that were preventing me from being able to move forward with the installation.  

For reference this is what I did.

I first had to disconnect the IDE drives leaving only the SATA drive.
I then installed Feisty from the desktop CD (I couldn't get past step 4 without disconnecting the IDE drives...i have no idea why)
With the new install of Feisty came a new MBR of course.
I reconnected my IDE drives and set my bios to look for the MBR on SDA rather than HD1
Now it works as I would expect.

That may not be the best way.  You can check these links I found but for whatever reason I was unsuccessful in editing grub (or installing grub and making it believe it was the MBR)
[http://ubuntuforums.org/showthread.php?t=435223&highlight=move+grub](http://ubuntuforums.org/showthread.php?t=435223&highlight=move+grub)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

