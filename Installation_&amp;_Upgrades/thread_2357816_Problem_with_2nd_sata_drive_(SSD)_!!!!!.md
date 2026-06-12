---
title: "Problem with 2nd sata drive (SSD) !!!!!"
date: 2017-04-06
forum: Installation &amp; Upgrades
---

### Post by xir2 on 2017-04-06
Hello guys and thank you for your time!
I face a problem and i would like your help.I have a laptop (Dell inspiron 15) and about a month ago i bought an SSD to speed it up a little. I removed the DVD drive and replaced it with my new SSD. The first hard drive(HDD) consist of two partitions (one windows ,one linux) and what i wanted to do was to clone the linux partition on my new SSD leaving windows alone. And so 

I cloned linux partition on the new SSD with clonezilla
I changed the UUID of the new partition because cloned partition had the same with the original
I edited fstab to point the new UUID and updated grub

My problem is that Grub2 detects all the partitions correct(even the new one on the SSD) but when i try to boot into the new partition  it shows me error like :

error: no such device with UUID .....
error: hd1 cannot get C/H/S values
error: need to load the kernel first


Any suggestion would be much appreciated..

---

### Post by oldfred on 2017-04-06
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by xir2 on 2017-04-07
Oldfred thx for your quick reply.
Here is the boot-repair summary report:


[http://paste.ubuntu.com/24332688/](http://paste.ubuntu.com/24332688/)

[http://paste.ubuntu.com/24332688/](http://paste.ubuntu.com/24332688/)

---

### Post by oldfred on 2017-04-07
It looks like UUID in grub menu have been changed to new install, including the one's for the first install. Or I assume you manually changed all UUIDs to new one. And I thought that should be enough to boot, but menu still has lots of device settings to hd0,3 that should be hd1,1.

It would probably be easiest to use Boot-Repair's advanced mode, and do a full uninstall/reinstall of grub2 and install boot loader into sdb.  It should give you choice to choose install on sdb and MBR on sdb. 
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

 
This is part of why I prefer a new clean install & copy /home, possibly some hardware settings from /etc, and list of installed apps that you export with dpkg. Also good way to know how to have good back up you can restore to new install.

You do need to house clean old kernels.
 [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 

I would also make sure you have boot flag on sda1 and Windows boot loader in sda. Windows 10 will turn its fast start up back on with updates and then grub will not boot it. You have to restore Windows boot loader. But with 2 drives you can keep a Windows boot loader on Windows drive and grub on Ubuntu drive, but when Windows breaks you can easily directly boot Windows and possibly f8 into repair console. Still best to have Windows repair disk or installer with repair console.

Will new SSD get transferred to new UEFI system in future? 
When I got my first SSD that was my plan, so I partitioned it with gpt which UEFI uses and included both the ESP - efi system partition for future use and a bios_grub flagged partition for my BIOS boot. Windows only boots from gpt with UEFI, but Ubuntu can use UEFI or BIOS if correct supporting partitions are on drive.

---

