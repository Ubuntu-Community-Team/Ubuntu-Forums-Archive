---
title: "Windows is screwing up again"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by lolocaust on 2006-06-29
So i've had the same windows installation for over 2 years, and its well overdue for a format and reinstall.

Basically, I want to know what steps should I take to ensure my dapper partition stays intact, and that the ubuntu bootloader comes up, instead of the one the the windows overwrites it with. I know I have to install windows to the exact same partition that it was originally on, but what else?

Thanks. :)

---

### Post by Maggot on 2006-06-29
Sounds like that is pretty much it.  I'm curious how you can keep windows installation from taking over the current boot loader though.

---

### Post by leo_m on 2006-06-29
Maybe you can not prevent Windows from over-writing the MBR, but you can certainly overwrite the Windows MBR with the Linux one after Windows has finished installing.

Where is Windows installed (an output of fdisk p command on your hard-disk/s will be of much help).  Also, which Windows version do you have?

---

### Post by lolocaust on 2006-06-29
I can't get to ubuntu right this minute, as I am backing up files from my Windows partition. It's installed on the first partition of my first hard disk, which is ide, if that helps. I'm using windows XP/SP1.

Could I just back up my menu.lst and restore it using a live CD?

---

### Post by leo_m on 2006-07-02
Before installing Windows, you can take a backup of the MBR using:

```

dd if=/dev/hda of=/mbr_lin count=1 bytes=1024

```

You should then copy this file onto the Windows partition, either using explore2fs (while in Windows) or by mounting the windows partition (whie in Ubuntu).

You should then edit the boot.ini file in Windows boot folder (C:\ for example) to add an entry pointing to the file you just copied to Windows.  That will help you boot into Ubuntu after you have finished Windows installation.

Now you are ready to install Windows again and not worry about it overwriting the MBR.

Once installation is finished and you land into Ubuntu again, you can then choose to overwrite the MBR with a Grub install or leave it as is, depending upon your choice.

Also see [http://www.ubuntuforums.org/showthread.php?t=205909](http://www.ubuntuforums.org/showthread.php?t=205909)

---

