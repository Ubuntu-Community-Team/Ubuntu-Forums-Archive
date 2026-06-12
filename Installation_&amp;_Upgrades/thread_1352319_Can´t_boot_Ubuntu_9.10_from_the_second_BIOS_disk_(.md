---
title: "Can´t boot Ubuntu 9.10 from the second BIOS disk (RAID1)"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Nyyr on 2009-12-11
Hi,

I have 3 disks, on the first one (boot) is Vista, the other ones are part of BIOS RAID1 disk (the second in BIOS boot sequence).

After installation device.map file contains:

(fd0)   /dev/fd0
(hd0)  /dev/sda
(hd1)  /dev/sdb
(hd2)  /dev/sdc

where /dev/sdc is the one with Vista, the first one in BIOS boot sequence.

When I extracted (dd if=......) MBR from the RAID disk (identified as /dev/mapper/isw_bgfhjjceei_Volume160) and used in EasyBCD (Vista boot menu editor) as bootloader for Ubuntu, my computer after loading this boot sector restarts.....

So I tried to change device.map to:

(fd0)   /dev/fd0
(hd0)  /dev/sdc
(hd1)  /dev/mapper/isw_bgfhjjceei_Volume160

and reinstall grub with:

grub --device-map=device.map

root (hd1,0)          <-----       RAID1 disk contains one (the first) primary partition (ext4) with /boot, the rest are logical partitions (/, /home, swap....)
setup (hd1)
quit

grub´s output:

root@ubuntu:/boot/grub# grub --device-map=device.map

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> quit
quit
root@ubuntu:/boot/grub#


In menu.lst I then replaced all occurences of (hd0,0) with (hd1,0)

But after restart the result is the same (PC reset).
If I change BIOS boot priority (RAID1 as the first), Ubuntu boots fine...

I had CentOS 5.4 on the RAID1 disk and I had no problems installing and booting it.....
(well, CentOS offered to install GRUB onto the boot sector of /boot partition and Ubuntu always installs GRUB into MBR regardless of my selection during install)

Any ideas?

P.S.: I do not want to boot Vista with Ubuntu as I have Vista´s disk encrypted with TrueCrypt.....

---

### Post by lemming465 on 2009-12-12
> Ubuntu always installs GRUB into MBR regardless of my selection during install
That's odd.  If I go for the *advanced* grub options on that last install screen I can successfully direct grub elsewhere.  I always do so for test installs to spare partitions, for example.
> I do not want to boot Vista with Ubuntu as I have Vista´s disk encrypted with TrueCrypt
I'm not familiar with truecrypt boots; if that requires using the MBR rather than just chainloading to the secondary boot sectors, I can understand your reluctance.  I'm curious though; the truecrypt documentation suggests to me that chainloading might suffice.  You can safely test this by having a windows entry in your non-MBR Grub boot menu.

Does your BIOS use F12 or something to pick boot devices?  Can you get to both OS's that way?

---

