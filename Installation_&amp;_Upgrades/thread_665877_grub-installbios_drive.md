---
title: "grub-install/bios drive"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by vdhagen on 2008-01-12
Problem:
grub-install /dev/sdd
reports
/dev/sdd does not have any corresponding BIOS drive.

Background:
My  BIOS allows to boot from any SATA disk. I.e. the device numbering when I boot from CD or HDD may differ. I installed ubuntu 7.04 (and windows XP) on a HDD disconnecting all other HDDs. After reconnecting the other drives GRUB was now in the in the MBR of harddisk3 (which becomes harddisk0 when I boot from it). GRUB allowed ubuntu and windows to start. Then, windows destroyed grub. I tried super-grub-disk (manual mode). Unfortunately, grub now was installed in harddisk0 (destroying another MBR).

I can boot the installed ubuntu with the super-grub-disk. As far as I found out the SATA disk I want to boot from is /dev/sdd. But when I enter
grub-install /dev/sdd
I get the message:
/dev/sdd does not have any corresponding BIOS drive.

What now?

Of course, I could disconnect all other drives again.... But there must be an easier way.

Any helpful suggestions?

Oskar

---

### Post by logos34 on 2008-01-12
boot from the ubuntu live cd and in a terminal run

sudo fdisk -l

Post it.

> GRUB allowed ubuntu and windows to start. Then, windows destroyed grub. I tried super-grub-disk (manual mode). Unfortunately, grub now was installed in harddisk0 (destroying another MBR).

So grub was the last to overwrite thje mbr, but it won't let you boot ubuntu?  Does the error appear after you select ubuntu to boot, or does grub fail to load?

---

### Post by vdhagen on 2008-01-12
live cd ubuntu sudo fdisk -l reports;
[FONT="Courier New"]
Disk /dev/sda: ...
Disk /dev/sdb: ...
Disk /dev/sdc: ...
Disk /dev/sdd: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2897    23270121    7  HPFS/NTFS
/dev/sdd2            2898       30401   220925880    f  W95 Ext'd (LBA)
/dev/sdd5            2898        5767    23053243+   7  HPFS/NTFS
/dev/sdd6            5768       25135   155573428+   b  W95 FAT32
/dev/sdd7           25136       26441    10490413+  82  Linux swap / Solaris
/dev/sdd8           26442       30401    31808668+  83  Linux
[/FONT]
Booting from sdd (with GRUB in MBR of sdd) allowed booting windows from sdd1 (as (hd0,0)) and ubuntu from sdd8 (as (hd0,8 )). The super-grub-disk installed grub in sda (destroying my W2K boot configuration, still allowing me to boot - a completely different - windows because (hd0,0) is now sda.)

How do I install GRUB on sdd (as hd0) without disconnecting all other harddrives?

---

### Post by logos34 on 2008-01-13
> **vdhagen said:**
> Booting from sdd (with GRUB in MBR of sdd) allowed booting windows from sdd1 (as (hd0,0)) and ubuntu from sdd8 (as (hd0,8 )). The super-grub-disk installed grub in sda (destroying my W2K boot configuration, still allowing me to boot - a completely different - windows because (hd0,0) is now sda.)

How do I install GRUB on sdd (as hd0) without disconnecting all other harddrives?  

maybe I'm missing something, but it sounds like the only thing required here is to change the bios boot order.  But just to be sure reinstall grub.

try this:

Go into the Bios and set the hard disk boot priority as:
1. sdd (ubuntu and windows xp? disk, the one shown in fdisk above)
2. sda (win2k disk)
3. sdb 
4. sdc 

Boot the ubuntu live cd and [reinstall Grub to the sdd MBR using this method instead]("http://ubuntuforums.org/showthread.php?t=224351"). i.e.,

sudo grub

find /boot/grub/stage1
root (hdx,y)  
setup (hdx) 
quit

Reboot and you should see grub on sdd appear.

As long as menu.lst still has (hd0,0) for windows on sdd1 and (hd0,7) for ubuntu on sdd8, then you should be good to go. If you get an error selecting either, you can change the 'root' lines by pressing 'e' key on the highlighted entry.  Edit, then 'enter' to save and 'b' to boot.  Once in ubuntu make the changes permanent:

gksudo gedit /boot/grub/menu.lst

-restore the windows bootloader to sda (win2k disk) either with a windows install cd (-->recovery console>command '**fixmbr**') or a win98 boot floppy (>**fdisk /mbr**)

--add win2k entry to bottom of menu.lst if you want to be able to boot it from Grub. ([like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")).

*for the latter you may have to edit /boot/grub/menu.lst.  sdd should be (hd0) and sda (hd1).

(forgive me if I've misunderstood anything--it's been a long day)

---

### Post by vdhagen on 2008-01-13
> **logos34 said:**
> maybe I'm missing something, but it sounds like the only thing required here is to change the bios boot order.  But just to be sure reinstall grub.

Thanks. Sorry that it didn't occur to me. I changed the bios boot order just to install grub and then changed it back. Now GRUB (on sdd) allows to boot ubuntu and windows again.

There remains just the curiosity why "grub-install /dev/sdd" didn't work and what "/dev/sdd does not have any corresponding BIOS drive" means.

Thanks.
Oskar

P.S. Obviously (hd0,7) is correct - and much easier because I don't have to worry about smilies.

---

### Post by logos34 on 2008-01-13
> **vdhagen said:**
> There remains just the curiosity why "grub-install /dev/sdd" didn't work and what "/dev/sdd does not have any corresponding BIOS drive" means.

Yeah, I wish I could figure that one out.  

> P.S. Obviously (hd0,7) is correct - and much easier because I don't have to worry about smilies.

Those smilies bug me to no end!

Anyway, glad it's working now.  Enjoy. And mark as 'Solved' (>thread tools).

---

### Post by adrian15 on 2008-01-16
> **vdhagen said:**
> There remains just the curiosity why "grub-install /dev/sdd" didn't work and what "/dev/sdd does not have any corresponding BIOS drive" means.

It means that /boot/grub/device.map has not a line like:

(hd3)   /dev/sdd

You can substitue (hd3) with whatever you want to.

You can also override device.map settings with the device command.

device (hd3) /dev/sdd

Didn't you find useful the super grub disk's liveswap feature in your situtation?

adrian15

---

### Post by spindle on 2008-07-11
You can also allow grub-install to re-build your device.map by adding --recheck to your grub-install command.

---

