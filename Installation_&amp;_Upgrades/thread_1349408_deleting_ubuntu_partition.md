---
title: "deleting ubuntu partition"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by nathang1392 on 2009-12-08
i had a 20 gig partition on my laptop. i got crunched for space and decided to just full install on my desktop and uninstall my laptop partition. i used easeus partition manager to take my swap and my ubuntu install and delete them and then reallocate the space to my vista partition. everything went okay with this and it went through a restart and then said it was finished. i rebooted and came to a grub screen that read: grub loading error no such partition. i used a vista reinstall disk to try to fix the bootloader, but that didnt work. im stuck with my laptop only booting to this grub screen and from there i have no idea what to do. help would be appreciated. thanks in advance.

---

### Post by darkod on 2009-12-08
> **nathang1392 said:**
> i had a 20 gig partition on my laptop. i got crunched for space and decided to just full install on my desktop and uninstall my laptop partition. i used easeus partition manager to take my swap and my ubuntu install and delete them and then reallocate the space to my vista partition. everything went okay with this and it went through a restart and then said it was finished. i rebooted and came to a grub screen that read: grub loading error no such partition. i used a vista reinstall disk to try to fix the bootloader, but that didnt work. im stuck with my laptop only booting to this grub screen and from there i have no idea what to do. help would be appreciated. thanks in advance.

Since you deleted your ubuntu partition as you wanted, this is MS issue in restoring your vista boot with the dvd. In general, the dvd with the Repair This Computer option should sort it out.

If you have multiple drives make sure the windows bootloader is not installed on the wrong drive.

---

### Post by nathang1392 on 2009-12-08
the only problem im having with this is that i already tried the reinstall disk. it attempted to fix the start up problems, and it even said that it did, but when i restarted i had the same problem.

---

### Post by OrangeCrate on 2009-12-08
To restore your MBR for Windows...

Use your installation disk, and go to Repair Your Computer. Then, under System Recovery Options, choose Command Prompt.

Type at the prompt:

```
Bootrec.exe /FixMbr
```

Hit enter, choose to reboot, and you'll boot into Windows.

---

### Post by presence1960 on 2009-12-08
> **OrangeCrate said:**
> To restore your MBR for Windows...

Use your installation disk, and go to Repair Your Computer. Then, under System Recovery Options, choose Command Prompt.

Type at the prompt:

```
Bootrec.exe /FixMbr
```

Hit enter, choose to reboot, and you'll boot into Windows.

+1

For future reference here is a [link]("http://ubuntuforums.org/showthread.php?t=1014708") that explains how to restore XP, Vista, Windows 7, GRUB legacy & GRUB 2 bootloaders

---

