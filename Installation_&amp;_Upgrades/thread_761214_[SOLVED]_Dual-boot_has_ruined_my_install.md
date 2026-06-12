---
title: "[SOLVED] Dual-boot has ruined my install"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by fitzwell on 2008-04-21
Hi,
I was following these instructions [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) and some funky stuff happened: GParted stuck a 4GB unallocated partition before my main partition, and Grub has left me unable to boot my existing Ubuntu install, without kicking me to an Initramfs prompt.

I'm wondering if I can rescue my Linux install, either via the LiveCD or via Grub changes.  Here is the results of fdisk -l command run from the LiveCD:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028513

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         565       23520   184394070   83  Linux
/dev/sda2           23521       30047    52428127+   7  HPFS/NTFS
/dev/sda3           30048       30401     2843505    5  Extended
/dev/sda5           30048       30401     2843473+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

I would really appreciate any advice to resolve this.  Thanks.

---

### Post by logos34 on 2008-04-21
Try using Gparted to grow sda1 back to the front of the disk to take up the unallocated space (1-564).  Then reinstall grub to both the root partition AND the MBR:
> 
[B]sudo grub

> find /boot/grub/stage1[/B]
(should output 'hd0,0'.  Enter in next command).
[B]> root (hd0,0)
> setup (hd0)[/B]  [--> writes grub to mbr]
**> quit**

repeat with **setup (hd0[COLOR="Blue"],0[/COLOR])** [--> writes grub to bootsector of root partition, which may have been lopped off when grub shrank the beginning of sda1]

link:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by fitzwell on 2008-04-22
No dice.  I can't boot from the GParted CD, and the Grub commands still kick me to the initramfs prompt after reboot.  Shouldn't I be able to boot an existing partition from the Ubuntu LiveCD?  I really don't want to wipe the whole install.

---

### Post by logos34 on 2008-04-22
> **fitzwell said:**
> No dice.  I can't boot from the GParted CD, and the Grub commands still kick me to the initramfs prompt after reboot.  Shouldn't I be able to boot an existing partition from the Ubuntu LiveCD?  I really don't want to wipe the whole install.

Actually, I was talking about running those commands in a terminal on the ubuntu live cd, and using Gparted there (System>admin>partition editor).

The ubuntu live cd will only allow you the menu option 'Boot from first hard disk'.  But that's not going to help much if your root partition is messed up or grub stage1 on the disk's MBR can't find root. 

I'd try [Super Grub Disk]("http://supergrub.forjamari.linex.org/") next.

---

### Post by fitzwell on 2008-04-23
Yeah, I was running it off the Ubuntu CD.  Once I moved the Linux partition to the head of the drive, Grub was able to load it.  Now I've got to figure out how to rescue my XP partition, but at least I'm back in business.

Thanks for your help.

---

### Post by logos34 on 2008-04-23
> **fitzwell said:**
> Yeah, I was running it off the Ubuntu CD.  Once I moved the Linux partition to the head of the drive, Grub was able to load it.  Now I've got to figure out how to rescue my XP partition, but at least I'm back in business.

Thanks for your help.

For windows try booting the XP install CD, enter the Recovery Console (>'R'), and run

**chkdsk /r**

and/or

**fixboot**

---

