---
title: "Grub Rescue Prompt After Install?"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by pittdaydreamer on 2013-05-23
Hello all.  I recently installed 12.04 and am having some boot issues.  In particular, when the system boots, it displays "file not found" and then drops me to a Grub resuce prompt.  I know my root is at (hd0,gpt2).  But when I run an ls (hd0,gpt2)/boot/, the directory is completely empty!  However, if I boot off of a rescue cd, the root drive is listed as /dev/sda2, and I can see all of my files in the /boot/ directory.  What in blazes is going on?  How do I fix this issue?  Thanks!

---

### Post by ubfan1 on 2013-05-23
Take a look at what devices grub thinks are present.  At the grub prompt, type set root=(  then TAB, and grub should offer all the possibilities.  hd0 certainly used to always be the first internal hard disk, but the disk assignments are no longer as stable as they used to be.  Check hd1 etc. if that is an offered possibility.  Certainly, if you installed on an external USB, you can expect device mix-ups which need to be manually corrected to boot, then run sudo update-grub to fix.

---

### Post by pittdaydreamer on 2013-05-23
The grub files are definitely on hd0.  I also tried running update-grub after booting from the rescue cd.  It correctly locates the kernel and adds the appropriate entries to grub.cfg.  But, upon reboot, I'm still dumpted to grub rescue.

Thanks!

---

### Post by arpanaut on 2013-05-23
see this: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Either while booted to the live cd install boot repair
Or download the boot repair disk and run the report function and post back here the pastebin URL
This will give us some insight to the problems.

Are you booting in uefi mode or bios mode.
Why is your disk partitioned gpt?

If you are trying to boot gpt disks in bios mode you will need a "bios grub" partition at the beginning of the drive.
Post the results of the boot repair create report function and we can go from there.

---

### Post by pittdaydreamer on 2013-05-24
I booted into the repair disk and selected the option to attempt an automatic repair.  This failed, but it did generate the following diagnostic report if anyone can help me make sense of this:
paste.ubuntu.com/5696747/

---

### Post by grahammechanical on 2013-05-24
This is what interests me.

> [COLOR=#000000]I know my root is at (hd0,gpt2).[/COLOR]

Does this mean that the disk is using GUID Partition Tables?

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

see this link and read down until Converting Ubuntu into Legacy mode and you will see this:

> [COLOR=#333333][FONT=Ubuntu]If Ubuntu is installed on a GPT disk (you can check it via the 'sudo parted -l' command), use [/FONT][/COLOR][Gparted]("https://help.ubuntu.com/community/Gparted")[COLOR=#333333][FONT=Ubuntu] to create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag) at the start of its disk.[/FONT][/COLOR]

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I do not know if the solution is in that link but it seems that with GPT disks things have to be done a little differently.

Regards.

---

### Post by pittdaydreamer on 2013-05-24
But, it looks like a BIOS-boot partition already exists:

GUID Partition Table detected.

[FONT=courier new]Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2           4,096 4,684,648,447 4,684,644,352 Data partition (Windows/Linux)
/dev/sda3   4,684,648,448 4,693,030,911     8,382,464 Swap partition (Linux)[/FONT]

Am I interpreting the following correctly that grub.cfg does not point to the BIOS Boot partition?

[FONT=courier new]insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'[/FONT]

If so, should I just update the grub.cfg file to read as follows?

set root='(hd0,gpt1)'


Thanks!

---

### Post by pittdaydreamer on 2013-05-24
Well, changing the root to (hd0,gpt1) does not work.  Any ideas?

I also verified through gparted that a BIOS-boot partition does exist and the bios_grub flag is set.

---

