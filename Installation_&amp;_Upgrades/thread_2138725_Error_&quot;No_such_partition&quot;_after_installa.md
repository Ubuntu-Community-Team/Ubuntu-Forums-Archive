---
title: "Error &quot;No such partition&quot; after installation"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by tmms on 2013-04-25
Laptop Compaq Presario 2500 (quite vintage, manufactured in 2004).
HDD 160 GB, installed in 2009.
Running Windows XP SP3 without problems.

Installed Ubuntu 12.04 from live CD, requesting a dual-OS.
Requsted installer to left 140GB for Windows and create a 20GB partition for Ubuntu.
Installer reported installation successful.

After rebooting got the message:

    Error: no such partition
    Grub rescue > 


Tried Boot-Repair.

Got a message that repair was successful.

After rebooting got the above message again.

Repair report: [http://paste.ubuntu.com/5600203](http://paste.ubuntu.com/5600203)

The report contains several error messages, especially:

Error: Can't have a partition outside the disk!

The Windows partition, as well as the new Ubuntu partition are still present on the disk, but how to access them ?

Regards, TMMS

---

### Post by oldfred on 2013-04-25
Some old BIOS only boot from the first 137GB of a drive. Data can be past that point, but not any boot files. Line 277 shows Ubuntu & grub boot files beyond that point, so that may be the issue.
You can make XP a little smaller and put a /boot partition fully in the first 137GB or a / (root) partition of 10 to 20GB and the rest for /home or a NTFS shared data partition.

It does not look like you have a lot of data in your XP partition, so you can shrink it more. I tend to prefer smaller system partitions and separate data partitions ( or /home in Ubuntu). I started using data partitions when dual booting Ubuntu and still have my shared NTFS data partition even though I now do not boot XP anymore.
But do not make a NTFS partition so small that it has less than 30% free space. When down to 10% free it lsows to a crawl and is one of the main reasons users complain about Windows being slow.

The liveCD is oversize and the errors on outside partition look like they all are from CD.

---

### Post by tmms on 2013-04-26
Resized paritions to: Windows 120GB, Ubuntu 40 GB.
This way the border is below 130GB.

Installation went successful, but after rebooting got another error:

error: out of disk
Grub rescue >

The Boot-Repair report: [http://paste2.org/GfAzVKBm](http://paste2.org/GfAzVKBm)

Both Windows and Ubuntu partitions seem to be OK.  Just the loader...

Any ideas, anyone ?

---

### Post by oldfred on 2013-04-26
The entire partition with boot files in it must be inside the 137GB limit. 
You boot files are here - line 274 in BootInfo:
>  147.684684753 = 158.575222784  boot/grub/core.img                             1

 147.645515442 = 158.533165056  boot/grub/grub.cfg                             1
 147.705768585 = 158.597861376  boot/initrd.img-3.2.0-23-generic-pae           6
 147.732109070 = 158.626144256  boot/vmlinuz-3.2.0-23-generic-pae              3
 147.705768585 = 158.597861376  initrd.img                                     6
 147.732109070 = 158.626144256  vmlinuz                                        3
 



---

### Post by mörgæs on 2013-04-26
Slightly off-topic: If this is your hardware
[http://www.cnet.com/laptops/compaq-presario-2500-15/4505-3121_7-30834272.html](http://www.cnet.com/laptops/compaq-presario-2500-15/4505-3121_7-30834272.html)
you will be better off with something lighter than Ubuntu.

---

