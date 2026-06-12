---
title: "Help cleaning up disk drive/installations"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2020-04-03
Over the years I routinely upgrade/update my Ubuntu/Windows installation. Lately I have noticed an accumulation of kernals and related that I would like to remove (see below). I only want to keep Ubuntu and win10. What is a safe way to clean the rest of this up?


Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-45-generic
Found initrd image: /boot/initrd.img-5.3.0-45-generic
Found linux image: /boot/vmlinuz-5.3.0-42-generic
Found initrd image: /boot/initrd.img-5.3.0-42-generic
Found linux image: /boot/vmlinuz-5.3.0-40-generic
Found initrd image: /boot/initrd.img-5.3.0-40-generic
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found Windows Recovery Environment on /dev/sda1
Found Windows 10 on /dev/sda2
Found Windows 7 on /dev/sda3
Found Ubuntu 14.04.1 LTS - KODIbuntu (14.04) on /dev/sda6
Found linux image: /boot/vmlinuz-5.3.0-45-generic
Found initrd image: /boot/initrd.img-5.3.0-45-generic
Found linux image: /boot/vmlinuz-5.3.0-42-generic
Found initrd image: /boot/initrd.img-5.3.0-42-generic
Found linux image: /boot/vmlinuz-5.3.0-40-generic
Found initrd image: /boot/initrd.img-5.3.0-40-generic
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment on /dev/sda1
Found Windows 10 on /dev/sda2
Found Windows 7 on /dev/sda3
Found Ubuntu 14.04.1 LTS - KODIbuntu (14.04) on /dev/sda6
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment on /dev/sda1
Found Windows 10 on /dev/sda2
Found Windows 7 on /dev/sda3
Found Ubuntu 14.04.1 LTS - KODIbuntu (14.04) on /dev/sda6

---

### Post by SeijiSensei on 2020-04-03
```

sudo apt remove linux*4.* linux*5.3.0-40*

```

---

### Post by TheFu on 2020-04-03
Don't think apt deals with globbing.  Apt-get does, however.
On 16.04 and later, using 
```
sudo apt upgrade && sudo apt autoclean
```
should remove older kernels automatically.  Think it keeps 2 or 3 kernels.

---

### Post by Impavidus on 2020-04-04
Not autoclean, but autoremove:```
sudo apt autoremove --purge
```
autoclean will remove old packages from cache (which is useful too).

I see a lot of duplicates in the list you posted. Strange, unless something went wrong when you pasted it on the forum. update-grub will simply list all installed systems it detects. The package manager can remove old kernels in Ubuntu, but if you want to get rid of Windows 7 on sda3 and the 14.04 system on sda6, you have to delete those OSs.

---

### Post by michael351 on 2020-04-04
Is there a way to remove the older windows OS (win 7)?

---

### Post by TheFu on 2020-04-04
impavidus is correct.  autoremove.  It was late when I posted. Sorry.

```
sudo apt update && sudo apt upgrade
sudo apt autoremove && sudo apt autoclean

```
Are my weekly patching commands. About once a month, I'll swap *sudo apt upgrade* for **sudo apt dist-upgrade**
Many of my systems use LVM which forces a separate, small, /boot/ partition.  Letting /boot/ get full causes some bad things to happen which are best proactively avoided.

To remove Windows, just format the partitions it uses.  Be certain to backup any data you might want to keep first.

---

### Post by oldfred on 2020-04-04
New installs of Windows often use an existing install's boot partition for its boot files & then adds older install to BCD.
Check which Windows partition has boot files.
Windows uses boot flag to know which partition to boot from. Grub looks for boot files.

Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by michael351 on 2020-04-04
A bunch is now cleaned up - thanks. This is what's left:

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  35653631  35651584    17G 27 Hidden NTFS WinRE
/dev/sda2  *     35653632  35858431    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda3        35858432 202442555 166584124  79.4G  7 HPFS/NTFS/exFAT
/dev/sda4       202442750 488396799 285954050 136.4G  f W95 Ext'd (LBA)
/dev/sda5       276912468 380232780 103320313  49.3G  7 HPFS/NTFS/exFAT
/dev/sda6       380233728 483876863 103643136  49.4G 83 Linux
/dev/sda7       483887104 488396799   4509696   2.2G 82 Linux swap / Solaris
/dev/sda8       202442752 276912127  74469376  35.5G 83 Linux


Not sure which one is my Ubuntu system (vs. old Ubuntu) or which is Win10. (/dev/sdb is my data disk and for backups - so I should be able to recover)

---

