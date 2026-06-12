---
title: "uninstall ubuntu"
date: 2006-03-26
forum: Installation &amp; Upgrades
---

### Post by yashoda on 2006-03-26
Hi!

Please help me.

I access the internet via dialup, and have had so many problems with ubuntu, relative to SUSE.

Please advise me how to uninstall ubuntu, i have it set up on a dual boot with Windows Xp.

Thanx.

yashoda

---

### Post by navilon on 2006-03-26
Under XP Go to:
Control Panel -> Advanced Tools -> Computer Management -> Disk Management
and delete the partition that ubuntu is installed on

---

### Post by donacheson on 2006-04-21
Will deleting the partion Ubuntu occupies also remove the dual boot loader?  If not, how can this be done?

I installed Breezy with no trouble (except having to puzzle out the partitioner) on a computer running an AMD Athlon and Win2K.  Except for the printer, all the hardware seems to work and the dual boot works just fine.  OpenOffice and Firefox behaved OK.  However, in exploring with the file manager and when trying to download updates, Ubundu proved very unstable - sometimes jumping back to login, other times freezing hard.  After about a dozen reboots this afternoon, I decided to call it quits.

TIA, Don

---

### Post by Jagot on 2006-04-21
Deleting the partition with Ubuntu will not get rid of Grub the boot-loader.  Grub will still exist in the MBR, so you will need to restore the MBR.

I'm not sure if this is available with Win2K, but with the Windows XP it is possible to boot from the installation disk and select R for repair.  You will come to a prompt at which you will need to type FIXMBR.  That will sort the problem.

I had a problem in that my computer was supplied with a disk image instead of an actual Windows installation disk so I instead used a FreeDos bootdisk.  This will however need a slightly different command (fdisk /mbr) but performs the same function.

---

### Post by donacheson on 2006-04-21
Thank you, Jagot.  That's what I  expected, but hoped, not.

Don

---

