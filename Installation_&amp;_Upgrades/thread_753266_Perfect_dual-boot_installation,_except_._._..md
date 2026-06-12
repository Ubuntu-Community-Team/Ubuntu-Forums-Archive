---
title: "Perfect dual-boot installation, except . . ."
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2008-04-12
I love my new Ubuntu, except 3 problems:


**Resume via keyboard doesn't work**
Suspend/resume/hibernate works fine, except Ubuntu will not resume with keyboard press. Works fine by pressing power button. I found a fix in the forums bit it only works **once**. Is there a permanent fix for this?


**NTFS read/write reliability**
I intend to create all my work files on an NTFS partition to be shared with Windows. Linux distributions' official statement is that they cannot write **reliably **on NTFS partitions. NTFS is proprietary and Microsoft is not sharing their technology? Phukers! What are peoples' experience writing to NTFS from Ubuntu?

Also Ubuntu disregards Win2k/XP NTFS **security settings,** AND allows protected directories to be deleted with a single key press! This is very important. Any solution?


**Dual booting via boot.ini**
I used the dd command, as described in countless threads, to create bootsect.lnx, and placed a corresponding line in boot.ini:

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
c:\bootsect.lnx="Ubuntu 7.10 Linux"

but it doesn't work, Grub hangs on boot after printing "GRUB" and a blinking cursor. Windows is on hd0,0 and Ubuntu on hd1,1. I boot just fine through the BIOS boot menu by selecting the 2nd hd as the boot-first device. How does one make boot.ini work?



**Fixed: date/time problem**
At first Ubuntu kept changing the system date/time every time I booted (GMT+/- local time), but that is fixed now, after some fiddling. Thanks Mr Ubuntu :)

---

### Post by logos34 on 2008-04-12
> **Rebelli0us said:**
> 
**NTFS read/write reliability**
I intend to create all my work files on an NTFS partition to be shared with Windows. Linux distributions' official statement is that they cannot write **reliably **on NTFS partitions. NTFS is proprietary and Microsoft is not sharing their technology? Phukers! What are peoples' experience writing to NTFS from Ubuntu?

It's a non-issue.  The NTFS-3G driver is rock-solid.  Look around in the forums--you won't find many complaints.  I used it for two years without a single problem. 

> 
**Dual booting via boot.ini**
I used the dd command, as described in countless threads, to create bootsect.lnx, and placed a corresponding line in boot.ini:

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
c:\bootsect.lnx="Ubuntu 7.10 Linux"

but it doesn't work, Grub hangs on boot after printing "GRUB" and a blinking cursor. Windows is on hd0,0 and Ubuntu on hd1,1. I boot just fine through the BIOS boot menu by selecting the 2nd hd as the boot-first device. How does one make boot.ini work?

Try writing grub to the bootsector of your root partition:

> sudo grub

> find /boot/grub/stage1
(enter output in the next command)  
> root (hd?,?)
> setup (hd?**[COLOR="Red"],?[/COLOR]**) --> this puts it on the partition in red--i.e. root--rather than the MBR)
> quit


Rerun the dd routine 

sudo dd if=/dev/sdb2 of=bootsect.lnx bs=512 count=1
(replace 'sdb2' with your linux root)

and move new bootsect.lnx file to C: drive.  

Alternatively you could try [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html").  Or use grub to dual boot (but I'm sure your have your reasons for not doing so).

---

