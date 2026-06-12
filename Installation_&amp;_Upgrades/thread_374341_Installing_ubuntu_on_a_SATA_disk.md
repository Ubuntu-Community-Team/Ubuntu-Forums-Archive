---
title: "Installing ubuntu on a SATA disk?"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by jinkl on 2007-03-02
I've installed Ubuntu 6.10 on one of my SATA disks (sda):

/dev/hde: IDE3 master (hde) - 203.9 GB Maxtor 6b200P0
**/dev/sda: SCSI1 (0,0,0) (sda) - 160 GB ATA WDC WD1600JD-55H**
/dev/sdb: SCSI2 (0,0,0) (sda) - 160 GB ATA WDC WD1600JD-55H

The installation went fine, but when I'm trying to boot it, I get an error saying "*Can't open operating system*".

The bios boot sequence is set up too boot like this:
WDC WD1600JD-(TM)
WDC WD1600JD-(QM)

Both sda and sdb are clean. hde got some data on it, but no operating system or anything. Just tell me if there is any other information you need.

I'm sorry if this has been posted before, but I faild to find any thread that helped me with my problem. 

Regards,
Jinkl

edit: Is it more likely to work if I install it on my IDE drive?

---

### Post by pixeldotz on 2007-03-02
have you tried making the other drives master instead of the ide one?

i have a laptop with ubunttu installed on it's sata hdd with no problems.

try installing again, maybe grub didn't install correctly. grub should install to hd0 and automatically pick up any operating systems in your pc/laptop regardless of type (windows or linux).


try disconnecting all the drives except theone ubuntu is installed on and see if that works.

a bit more information migt help us to help you.

---

