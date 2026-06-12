---
title: "Can't Boot After Canceled Install--Computer completely dead"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by jimalan on 2007-01-08
I've been searching the forums for two hours for anything like this and haven't found it, so here goes:

I spent the last week reading over the posts about how to do a dual hard drive install with Ubuntu Dapper Drake and Win XP SP2 on two separate SATA drives.  Today, I inserted my ISO disk for 6.06 for the first time.  Had some trouble with "respawning" but cured it with Ctrl-Alt-Del and a reboot.  Went to the Ubuntu desktop to look around and clicked on the Install icon.

I went partway through the process, always making sure Ubuntu was working with my new 160 GB drive, not my Win XP boot drive (40 GB).  When I got a bit confused, I restarted a couple times but NEVER told it to install anything to any drive.  Finally, I took a break for lunch WITHOUT installing and told Ubuntu to Cancel and Shut Down.  It did this just fine.

Imagine my surprise when I returned to my computer and found it won't boot.  It keeps asking me to insert a Windows boot diskette into my A drive!  Say what?  I went into BIOS and did everything I could think of--making sure the CD was first in the boot sequence (it was, but it never gets activated), turning off the A drive (makes no difference), turning off the SATA drive I was looking at with Ubuntu (no difference).  I have a copy of the Super Grub Disk on CD, but I can't get at the CD drive.  The computer always asks for a disk to be inserted in the A drive.  It never checks the hard drives or the CD.  The only thing I can access is the BIOS.  I have a back-up utility program called GoBack, but it jams during boot and won't let me reset my hard drive to a previous time.

I fired up my old Win 98 machine and tried downloading the Super Grub floppy only to find out it's 1.44 MB, and my disks all max out at 1.38, so I can't copy the program.  I have it on CD, but that doesn't do me any good until I can get the CD drive to work.

What the hell happened?  I never did an install, just messed around with various partition possibilities and then pressed Cancel.  I'm worried that if I use the Windows XP Boot Floppies I copied from the MS support site, I'll end up erasing everything on my hard drive when Setup is finished.  It seems to indicate this would be a clean install.  There must be something wrong with the boot loader in Windows, but how do I get at it?  And how did it get messed up in the first place?

I'm running on my old Win 98 until this mess is straightened out.  Can anyone offer me a suggestion?  I'm beginning to feel a bit desperate.

Thanks, Jim

PS.  My frozen system: Dell 4700 Desktop with 2 SATA Hard drives (160Gb & 40Gb--the 40 is my boot drive), one floppy, two CD burners, Win XP Home SP2, 2GB RAM, P4 2.7 GHz processor.

---

### Post by budgie9 on 2007-01-08
> **jimalan said:**
> I've been searching the forums for two hours for anything like this and haven't found it, so here goes:

I spent the last week reading over the posts about how to do a dual hard drive install with Ubuntu Dapper Drake and Win XP SP2 on two separate SATA drives.  Today, I inserted my ISO disk for 6.06 for the first time.  Had some trouble with "respawning" but cured it with Ctrl-Alt-Del and a reboot.  Went to the Ubuntu desktop to look around and clicked on the Install icon.

I went partway through the process, always making sure Ubuntu was working with my new 160 GB drive, not my Win XP boot drive (40 GB).  When I got a bit confused, I restarted a couple times but NEVER told it to install anything to any drive.  Finally, I took a break for lunch WITHOUT installing and told Ubuntu to Cancel and Shut Down.  It did this just fine.

Imagine my surprise when I returned to my computer and found it won't boot.  It keeps asking me to insert a Windows boot diskette into my A drive!  Say what?  I went into BIOS and did everything I could think of--making sure the CD was first in the boot sequence (it was, but it never gets activated), turning off the A drive (makes no difference), turning off the SATA drive I was looking at with Ubuntu (no difference).  I have a copy of the Super Grub Disk on CD, but I can't get at the CD drive.  The computer always asks for a disk to be inserted in the A drive.  It never checks the hard drives or the CD.  The only thing I can access is the BIOS.  I have a back-up utility program called GoBack, but it jams during boot and won't let me reset my hard drive to a previous time.

I fired up my old Win 98 machine and tried downloading the Super Grub floppy only to find out it's 1.44 MB, and my disks all max out at 1.38, so I can't copy the program.  I have it on CD, but that doesn't do me any good until I can get the CD drive to work.

What the hell happened?  I never did an install, just messed around with various partition possibilities and then pressed Cancel.  I'm worried that if I use the Windows XP Boot Floppies I copied from the MS support site, I'll end up erasing everything on my hard drive when Setup is finished.  It seems to indicate this would be a clean install.  There must be something wrong with the boot loader in Windows, but how do I get at it?  And how did it get messed up in the first place?

I'm running on my old Win 98 until this mess is straightened out.  Can anyone offer me a suggestion?  I'm beginning to feel a bit desperate.

Thanks, Jim

PS.  My frozen system: Dell 4700 Desktop with 2 SATA Hard drives (160Gb & 40Gb--the 40 is my boot drive), one floppy, two CD burners, Win XP Home SP2, 2GB RAM, P4 2.7 GHz processor.
Jim are you assuming the floopy disk you are downloading is not simply an indication of the size of floppy it has to be installed to.
I suspect the file you have/will download will install on to a floppy disk.
You may also want to look at posts re re-building your MBR file. This may get you back again. As to SATA my only experience with them has been troublesome, so I can't help you there.

---

### Post by budgie9 on 2007-01-08
> **budgie9 said:**
> Jim are you assuming the floopy disk you are downloading is not simply an indication of the size of floppy it has to be installed to.
I suspect the file you have/will download will install on to a floppy disk.
You may also want to look at posts re re-building your MBR file. This may get you back again. As to SATA my only experience with them has been troublesome, so I can't help you there.
Are you sure you can't access the BIOS and set the CD to be the primary install drive? In most instances this can be set so.You may have to move the CD drive to the top of the list, to make it active as first boot option.

---

### Post by atlien on 2007-01-08
If all else fails, you can always reset the motherboard by removing the battery.  But that will take you back to your original bios.  I've had to do that before with serious lock-ups/dead computer type situations.  You may not need to do that but as a last resort, it will probably get you at least to the point where your bios will allow cd-rom booting.

---

### Post by jimalan on 2007-01-09
Problem solved.  Thanks to all for your help.  I kept playing with it and finally was able to get the situation fixed by unplugging the power for my new hard drive.  Suddenly, I was able to boot into Windows again, so it had to be something on the new drive.  I plugged the new drive back in, hit Restart with the Ubuntu CD in the CD drive, and prayed.  It booted, and I was able to finish an install without any trouble, though I've got another question I might have to post today about something else entirely.  At least I have my computer back and I can play with/learn about Ubuntu.

---

