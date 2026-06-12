---
title: "Problems installing/runni Ubuntu Server 6.10 AMD64 and i386 on Intel E6400 Core 2 Duo"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by egars on 2007-01-11
Hi,

I'm using a freshly bought Dell Dimension 9200 which contains an Intel E6400 2,13 GHz, 2Mb Cache 1066MHz FSB Intel Core 2 Duo processor.

Now, both Ubuntu Server version 6.10 AMD64 and i386 yield the same errors,
something like:

[42949376.760000] ACPI: Getting cpuindex for acpiid 0x3
[42949376.760000] ACPI: Getting cpuindex for acpiid 0x4

Then the system hangs.

Furthermore: installation of Lilo or Grub combined with XFS fails miserably (Lilo is recommended in combination with XFS, but still fails). This was only tested using the AMD64 Ubuntu Server 6.10 version.

Using EXT3 (both the AMD64 and i386 version) results in the error messages about ACPI.

After using Linux for more than 10 years now, I'm stuck with Linux, for the first time!

My configuration:
boot.ini in the installed windows partition (which is what you get when you buy Dell) contains a line:
c:\linux.bin="Linux", which is a file that consists of the first 512 bytes copied from /dev/sde8 (which is the /boot partition of the Ubuntu installation), that was created with this statement:
dd if=/dev/sde8 of=/tmp/pen/linux.bin
and then copied from the USB stick (mounted on /tmp/pen) on the windows c: partition.

After windows boots, and I choose Linux, Grub correctly shows different kernel options. So it seems that using the linux.bin file to boot to the linux partition works fine.

Do I need special kernel parameters?????
Which?
Is EM64T processor compatible with AMD64 (during installation, no complaints from installation software occur)?

Anyone?

Kind regards,

Jerrie

---

### Post by arnieboy on 2007-01-11
try adding **acpi=off** in the single line of options for the root partition in /boot/grub/menu.lst

---

### Post by penvzila on 2007-01-11
Do not use the AMD64 install with an Intel chip.

---

### Post by egars on 2007-01-12
Hi All,

The cause of the trouble on my Dell Dimension 9200 was found in Grub's config file menu.lst.

Problem is that if root=/dev/sda9 in menu.lst, everything is fine. This works:

title           Ubuntu, kernel 2.6.17-10-server
root            (hd0,7)
kernel          /vmlinuz-2.6.17-10-server root=/dev/sda9 ro quiet splash
initrd          /initrd.img-2.6.17-10-server
quiet
savedefault
boot

However, after installation that line says: /dev/sde9. 

After booting all harddisk partitions are named "sde" instead of "sda".

Each time a kernel is updated, and menu.lst is updated (with sde) I must manually edit it and change sde into sda in the kernel parameters.

The installation procedure that I have used (Ubuntu 6.10 Server i386) is without any problems or special features. 

Why is it that Grub wants another name for the same harddrive?

PS: In my particular environment, Grub is installed in /dev/sde8 (which is mounted to /boot), instead of the master boot record. Maybe that has something to do with it.

Cheers,

Jerrie

---

