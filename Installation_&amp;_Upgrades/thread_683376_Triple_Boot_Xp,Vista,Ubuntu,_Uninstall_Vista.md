---
title: "Triple Boot Xp,Vista,Ubuntu, Uninstall Vista"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Ashpants on 2008-01-30
I successfully triple booted my computer one HD and 3 OS's

My original OS was XP, I installed Vista and then installed Ubuntu.
After playing with all three OS's I've decided I want to keep XP and Ubuntu.  What was I ever thinking Installing Vista?

When my computer starts It first goes to the Ubuntu Grub and I can select 3 Ubuntu options or Vista Loader.  If I pick the vista loader It will let me pick either XP or Vista.

This leads me to believe that when I installed Vista it took over the MBR.  I tried editing Ubuntu's menu.lst to boot the xp partition with no success.  This leads me to believe that Vista took over the MBR right?

I was thinking of using the xp cd to restore the MBR and fix all the boot paths. Then use the gparted on the ubuntu cd to fix the MBR for ubuntu.

I can't remeber if I let ubuntu take control of the MBR when I installed it.. I would guess i did since the ubuntu grub is the first thing I see when I boot.  Is there any way to check this?

Would this process with the xp and ubuntu cd's work?

I also want to backup my files just in case something haywire happens.  Want to know the best option for this since I am messing with the MBR.


sda1 is XP
sda2 is Vista

fdisk -l reveals:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x752e752e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30409   244254144+   7  HPFS/NTFS
/dev/sda2           30409       43157   102400000    7  HPFS/NTFS
/dev/sda3           43158       46804    29294527+  83  Linux
/dev/sda4           46805       48263    11719417+   5  Extended
/dev/sda5           46805       48263    11719386   82  Linux swap / Solaris


       
    In my menu.lst




## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d6119dda-e1bc-4d48-a5d6-8eeb92730662 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2008-01-30
Boot up the XP cd, press 'R' to enter recovery console and run **fixboot**.  

Reboot to grub, select XP.  If it works, open boot.ini (it's a hidden file, so you may have to type 'boot.ini' in the address bar) and remove the vista line.  Also remove from C: base directory

Boot (folder)
Boot.BAK
bootmgr
BOOTSECT.BAK

Or:

boot into ubuntu, edit boot.ini and remove folders and files from there (windows must be mounted with write access).

Then use gparted to delete vista partition.

---

