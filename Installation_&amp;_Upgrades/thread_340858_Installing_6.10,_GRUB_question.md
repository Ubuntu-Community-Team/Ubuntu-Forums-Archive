---
title: "Installing 6.10, GRUB question"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by Doovoo on 2007-01-17
I've run Ubuntu many times before, but one this install, I wanted to do something slightly different. I had linux installed on my 1 drive (sda) and now I want to install Ubuntu on the same drive, So I went into the manual partition and resized it so there was room. Then, after the resizing and subsequent formatting, there's another 2gb partition showing up flagged for "boot."

So I assumed this is where to write GRUB to so I changed the mount point for that partition to /boot, and when I got to the step before the actual installation I put in (sda,4) in the option for where to write GRUB, Then it gave me an error during installation that GRUB couldn't be installed.

I think I'm telling it to write to the wrong place or something. Any suggestions?

---

### Post by lotacus on 2007-01-17
you need a partition to install the boot loader, you need a partition for / (root) and you need a swap partition. If you already have another distro on there, you should be able to have ubuntu write to the bootsector, over-writing the previous bootloader (it will and should detect the other intsallation and add it to the menu) it should also auto detect that there is a swap partition already set up and ask if you want to use that. So all you really have to worry about is the root partition for the actual installation.

---

### Post by Doovoo on 2007-01-17
well, I've got a swap(was there from before) and I got a root (the new installation) and I've got a boot. The previous installation was dual booting with windows so the bootloader was on another drive, That drive is f***ed now so that's out of the picture and I don't even want to be able to boot into the old linux partition (I'll just mount it and copy out the files I need later). I just don't know what to enter for where to install the bootloader, I mean should it be (sda,4) or (sda4) or what?

---

### Post by Doovoo on 2007-01-17
I tried it with (sda4) and it gave me the error saying "grub_install(sda4)" failed or something along those lines.

I really think I'm just entering it wrong (but maybe that's cuz I'm used to looking for syntax errors in code).

---

### Post by confused57 on 2007-01-17
I'm not really sure about your partition layout, usually a boot partition is located near the beginning of the partition table(after the mbr).
You might want to first boot up the live cd, open a terminal & enter:
```
sudo fdisk -l
```
The -l is a small "L"

If you're sure you want to install grub to sda4, then enter **/dev/sda4** or **(hd0,3)**, or **(hd0)** for installing grub to the mbr.

---

### Post by Doovoo on 2007-01-17
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7314    58749673+  83  Linux
/dev/sda2           30197       30401     1646662+   5  Extended
/dev/sda3            7315       29925   181622857+  83  Linux
/dev/sda4   *       29926       30196     2176807+  83  Linux
/dev/sda5           30214       30401     1510078+  82  Linux swap / Solaris
/dev/sda6           30197       30213      136489+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

That's what it gives me, I wanna enter /dev/sd4 then?

---

### Post by confused57 on 2007-01-17
I don't want to give you any misinformation, since I've never had a separate boot partition.

I assume sda1 is another Linux distro that has it's grub installed to the mbr that you're booting your OS with & you installed Ubuntu after resizing...did you specify a separate /boot partition during your Ubuntu installation or did you already have one from the OS on sda1?  Also, you can share the same swap partition for multi-booting several Linux distros, you can do this by selecting "manual install" when you install Ubuntu & designate the swap partition you already have to be mounted as swap in Ubuntu.

If you're booting from a Linux OS on sda1 and choose to install grub to /dev/sda4(if in fact it is a boot partition, which it probably is since it has the boot flag), you'd need to add an entry to your /boot/grub/menu.lst(sda1 grub) to chainload to your /boot partition to boot Ubuntu:

title     Ubuntu
rootnoverify  (hd0,3)
chainloader  +1

Like I said, I don't have any experience with a separate /boot, so you might want to wait for someone who can give you more helpful advice.

---

