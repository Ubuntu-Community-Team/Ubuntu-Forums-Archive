---
title: "GRUB only boots Windows, not Kubuntu"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Kvbx4 on 2012-01-07
I’m having a problem setting up my computer to dual-boot Windows Vista and Kubuntu. I have Windows and the Windows bootloader installed on a 500 GB SATA drive (sda) and Kubuntu and GRUB on a 60 GB PATA drive (sdb). But no matter which hard drive I boot from, it boots into Windows. I tried chrooting into the Kubuntu system on sdb from the LiveCD and changing the following lines in /etc/default/grub to:
```
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
```When I ran update-grub, it identified the Kubuntu system on sdb and the Windows system on sda, but still only booted into Windows from either drive.

I also tried chrooting into Kubuntu, purging GRUB, and reinstalling it on sda over the Windows bootloader. That, however, made neither OS bootable--it just says "device not found:" followed by sdb's UUID and dumps me at a GRUB rescue prompt. When I run ls at the prompt, it only lists my Windows hard drive and its partition. So I restored the Windows bootloader on sda and reinstalled GRUB on sdb, and it's doing the same thing as before--booting into Windows no matter what. How can I fix this so that I can boot from sda into Windows and boot from sdb into Kubuntu?


My system configuration (this is a homebuilt computer):

sda is a 500 GB SATA drive plugged into SATA 1 and designated by the BIOS as the 3rd master.
sdb is a 60 GB PATA drive plugged into the PATA port and designated by the BIOS as the 2rd master.
My CD/DVD drive is plugged into SATA 3 and is designated by the BIOS as the 3rd slave.


Output of fdisk -l (from LiveCD):
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5be96505

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders, total 117187500 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008da8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   109180927    54589440   83  Linux
/dev/sdb2       109182974   117184511     4000769    5  Extended
/dev/sdb5       109182976   117184511     4000768   82  Linux swap / Solaris
```
My /etc/default/grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```Any help is greatly appreciated.

---

### Post by darkod on 2012-01-07
If the ls can't see the small disk it doesn't look like it can recognize it at least for boot purposes. Are you sure it allows you to boot from sdb?

The problem seems to be it's not recognized to boot from so it keeps booting from sda. With board with SATA and IDE I'm not sure if they give priority to the SATA disks for boot although you should be allowed to select where you want to boot from.

---

### Post by Kvbx4 on 2012-01-07
Yes, both disks show up on the boot devices menu when I hit esc. The way I want to set it up is so that if I just turn it on it'll boot straight into Windows, but I can boot into Kubuntu if I hit esc and select its drive.

---

