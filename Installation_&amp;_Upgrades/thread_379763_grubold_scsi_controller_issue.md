---
title: "grub/old scsi controller issue"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by dave__ on 2007-03-08
I am installing 6.10 onto a scsi drive which is connected to an old adaptec card which uses the aha152x driver.

 I was able to boot up onto the live cd, modprobe aha152x and then install to the scsi disk.

The problem is that when I restarted the computer all I got was a grub error. Grubs main menu screen never came up at all. I am presuming that there is no driver loaded for the scsi card. How should I go about resolving this?

---

### Post by Herman on 2007-03-09
What grub error did you get? :)

---

### Post by dave__ on 2007-03-09
All that is displayed is **'GRUB Geom Error' **in white writing with nothing else on the screen!

---

### Post by Herman on 2007-03-09
From the Gnu/Grub Manual,
> Geom ErrorThe location of the stage2 or stage1.5 is not in the portion of the disk supported directly by the BIOS read calls.  This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install). This is an error code from grub's stage1.

I don't know what to suggest, I'll think about it for a while. maybe someone else will come along who has experience with this error.

Regards, Herman

EDIT: I found this link: [SDB:The Boot Process Hangs with the Message GRUB Geom Error]("http://en.opensuse.org/SDB%3AThe_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error")

---

