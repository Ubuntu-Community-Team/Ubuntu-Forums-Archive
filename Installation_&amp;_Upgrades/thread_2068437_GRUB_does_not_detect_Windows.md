---
title: "GRUB does not detect Windows"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by ArcaneWater on 2012-10-09
I have finally installed ubuntu on my second drive i change my d drive to took 8gb for swap and formated d disc(sda4 to ext4), now when i start computer in grub is shows me only ubuntu and windows 7 is not shown. So how should i fix thath problem to i will be able to choose between them at grub.

Another thing is after i press F12 for boot menu at startup i choose windows boot manager and i get into Windows 7.

I runed command sudo fdisk -l and here is log: [http://pastebin.com/Cgv1igHc](http://pastebin.com/Cgv1igHc)

> ARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Thanks for help!

---

### Post by darkod on 2012-10-09
That disk has gpt table. Are you using UEFI boot? If you do, you should have installed ubuntu in UEFI mode, not the standard mode.

If windows is on the same disk it's probably UEFI since win7 can't work on gpt without uefi.

---

### Post by ArcaneWater on 2012-10-09
Yes probably cause i have Windows 7 its uefi, right now i am going to install Windows 7 again and format both disc. Are there any guides how to make partitions in w7 first to they are fine for ubuntu setup later?

---

### Post by Mark Phelps on 2012-10-09
IF you're asking about creating partitions for Ubuntu -- NO.  I'm not aware that Win7 will let you format partitions as Ext4.

---

### Post by oldfred on 2012-10-09
If Windows is in UEFI, and you installed Ubuntu in BIOS, you can use Boot-Repair to convert Ubuntu to UEFI boot.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If reinstalling, you just need to be consistent. Both Windows & Ubuntu have to be either UEFI/gpt or BIOS/MBR. Both installs should offer either as a choice with 64bit versions. Ubuntu's liveCD will install in the mode it is booted into either UEFI or BIOS/AHCI/legacy or whatever.

With BIOS/MBR you have the 4 primary partition limit or Ubuntu then has to be in logical partitions, with gpt all partitions are primary so the only limit is 128 partitions :) .

---

### Post by ArcaneWater on 2012-10-09
> **Mark Phelps said:**
> IF you're asking about creating partitions for Ubuntu -- NO.  I'm not aware that Win7 will let you format partitions as Ext4.

No i am asking how should i divide my disc 1tb big in gparted to prepari it for Windows and Ubuntu, i use quit a lot windows definitly more then Ubuntu right now. But i will be probably using them same amount of time once i start with it.

---

### Post by oldfred on 2012-10-09
It makes a big difference if UEFI or BIOS as that determines how you create partitions and what partitions are required.

Windows has to have gpt partitioning if booting in UEFI and will not boot from gpt with BIOS.  Ubuntu can boot from gpt or MBR partitioning whether BIOS or UEFI.

If UEFI with Windows:
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by ArcaneWater on 2012-10-09
> **oldfred said:**
> It makes a big difference if UEFI or BIOS as that determines how you create partitions and what partitions are required.

Windows has to have gpt partitioning if booting in UEFI and will not boot from gpt with BIOS.  Ubuntu can boot from gpt or MBR partitioning whether BIOS or UEFI.

If UEFI with Windows:
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)I have new computer it was made on 2012 it have new i5 with ivy bridge. So how can i check if i have UEFI or BIOS? Also how should i then format and create partions for Windows and for ubuntu in gparted?

---

### Post by YannBuntu on 2012-10-09
> **ArcaneWater said:**
> So how can i check if i have UEFI or BIOS? Also how should i then format and create partions for Windows and for ubuntu in gparted?

UEFI doc: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2012-10-09
Just post this from liveCD or USB. If first partition is FAT32 and efi/boot then you are in UEFI mode.

sudo parted /dev/sda unit s print

---

