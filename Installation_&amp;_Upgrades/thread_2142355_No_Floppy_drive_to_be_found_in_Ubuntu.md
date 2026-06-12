---
title: "No Floppy drive to be found in Ubuntu"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by lrichard on 2013-05-05
Good afternoon!

I need some help with this floppy issue.

The commands output:
> lrichard@d600:/$ sudo modprobe  floppyFATAL: Error inserting floppy (/lib/modules/3.0.0-32-generic/kernel/drivers/block/floppy.ko): No such device
lrichard@d600:/$ dmesg | grep floppy
[44859.480072] floppy0: no floppy controllers found
lrichard@d600:/$ modinfo floppy
filename:       /lib/modules/3.0.0-32-generic/kernel/drivers/block/floppy.ko
alias:          block-major-2-*
license:        GPL
author:         Alain L. Knaff
srcversion:     6BD7D154603E5F90A2F2316
alias:          acpi*:PNP0700:*
alias:          pnp:dPNP0700*
depends:        
vermagic:       3.0.0-32-generic SMP mod_unload modversions 686 
parm:           floppy:charp
parm:           FLOPPY_IRQ:int
parm:           FLOPPY_DMA:int
lrichard@d600:/$ cd /dev/
lrichard@d600:/dev$ ls -ahl fd*
lrwxrwxrwx 1 root root 13 2013-05-05 04:38 fd -> /proc/self/fd


---

### Post by oldfred on 2013-05-06
Do you have floppy enabled in BIOS?

 [http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
[http://ubuntuforums.org/showthread.php?p=11244050#post11244050](http://ubuntuforums.org/showthread.php?p=11244050#post11244050) post #2 coffeecat
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

---

### Post by lrichard on 2013-05-11
> **oldfred said:**
> Do you have floppy enabled in BIOS?
I don't have shuch option.

> **oldfred said:**
> udisks --mount /dev/fd0
ls /dev/fd*

The result of these commands:
> lrichard@d600:~$ udisks --mount /dev/fd0
Cannot stat device file /dev/fd0: No such file or directory
lrichard@d600:~$ ls /dev/fd*
0  1  2  3


This is a floppy drive, which is on the spot of the CD drive, from the Ubuntu was installed. So in one time only one drive can I have. I found [here]("http://files.myopera.com/paddy2k/albums/517373/IMG_0331%20(Medium).jpg") a picture of it.

---

### Post by oldfred on 2013-05-11
It is not even seeing your floppy?

I included a floppy drive when I built this system in 2006 and maybe have used it a couple of times.

fred@fred-Precise:~$ ls /dev/fd*
/dev/fd0

It should show drive, like mine does. If BIOS does not report that drive is there that may be an issue. If it is removeable, make sure it is plugged in and do a full reboot from total power down.

---

