---
title: "Unable to open /dev/sda/ and more."
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by Evelus on 2011-08-12
Hey there!

After attempting to install Ubuntu 11.04 (both 86 and 64) from a disc, I get the following errors on the 'Ubuntu 11.04' (underneath: dots) screen.

```

unable to open /dev/sda/
unable to open /dev/sdb/

```
and eventually...
```
No init found. try passing init= bootarg.
```
After which I am thrown into 'BusyBox' (initramfs) ash.

CPU: Intel Core i7 2600K
HDDs: 2x Western Digital Caviar Black 1TB on AHCI (tried IDE and a RAID0 array)
GFX: HD Radeon 6970 2GB
RAM: 4GB (2x2) Kingston HyperX Genesis 1600Mhz @ 1333Mhz

The 86 disc lets me try ubuntu, and even begin installing it... but fails at the part where it must install a bootloader. I'm guessing that my drives either don't exist as SDA/SDB, or haven't been set up correctly. Does anyone know what I could try? :) I will give you any other information you need! 

Thanks.

---

### Post by Lampi on 2011-08-12
Could it be a grub issue? inside the busybox you can check the command line grub used with:

cat /proc/cmdline

---

### Post by Evelus on 2011-08-12
(This is a clean install by the way, completely blank Hard Disks)

After entering:
```
cat /proc/cmdline/
```
I get the error:
```
cat: can't open '/proc/cmdline': No such file or directory
```

:-( Is there any specific setting for my SATA configuration that needs to be addressed?

---

### Post by Lampi on 2011-08-12
> **Evelus said:**
> After entering:
```
cat /proc/cmdline/
```
I get the error:
```
cat: can't open '/proc/cmdline': No such file or directory
```


it's cat /proc/cmdline (no trayling " / " )

you can also try cat /proc/partitions to get a list of partitions the bootloader recogniced


> **Evelus said:**
> 
Is there any specific setting for my SATA configuration that needs to be addressed?

As long as you have the SATA controller enabled in your mainboard BIOS I don't think so - what can change is the name of the device node (eg /dev/sdb instead of /dev/sda)

---

### Post by Evelus on 2011-08-12
No matter what I try, I still get 'not found' for both of those things. I'm determined to get this working!

---

### Post by Evelus on 2011-08-13
*Cheeky bump; I desparately need a computer!*

---

### Post by unholy1 on 2011-09-09
Any luck? I have the same problem trying to install 64-bit 11.04 on an IBM Lenovo W500...

---

### Post by fdrake on 2011-09-09
have you tried with the 32bit instead?

---

### Post by unholy1 on 2011-09-09
Not yet. I'd prefer to use 64-bit if possible (the laptop currently has 64-bit Windows 7 on it).

---

### Post by unholy1 on 2011-09-10
My guess is that it's something to do with the "Intel Rapid Storage Technology" which is configured in RAID 0 for the two HDs. I'll try using the IRST utility to reset the disks to Non-RAID and then hopefully I can install Ubuntu with its own software RAID. I'll post back with the results.

---

