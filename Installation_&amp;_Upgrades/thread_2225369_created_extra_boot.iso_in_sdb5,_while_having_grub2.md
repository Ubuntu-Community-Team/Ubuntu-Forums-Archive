---
title: "created extra boot.iso in sdb5, while having grub2 on sdb2, now can't boot at all"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by rodrigo9 on 2014-05-21
Hi, 
So yesterday I had the brilliant idea of modifying my ubuntu partition "slightly" in order to be able to boot from my Windows 7 partition (both os's are installed in seperate hard drives actually). 

Anyways, I was more or less following [this guide]("http://www.neowin.net/forum/topic/784138-howto-boot-existing-ubuntu-partition-using-virtualbox-inside-windows/") and [this guide]("http://merx3.wordpress.com/2012/08/29/booting-an-existing-ubuntu-instalation-from-virtualbox-while-using-windows/") which both required me to create a boot.iso image file on my root directory (on ubuntu's side). Anyways, now I'm getting "error: file not found grub restore" and I can't boot in neither my windows or ubuntu.
This is message from my paste-repair:
[http://paste.ubuntu.com/7496385/](http://paste.ubuntu.com/7496385/)

> ...
sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 22338 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/grub on this drive.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________
...
sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Boot file info:      Grub2 (v1.97-1.98) in the file /boot.iso looks at 
                       sector 1 of the same hard drive for core.img. core.img 
                       is at this location and looks in partition 256 for .
    Operating System:  Ubuntu 12.04.4 LTS 
    Boot files:        /etc/fstab
...

This is probably a stupid question, but are my problems because there are two grub2's, one in sdb1 and the other in sdb5? 
And if so, can the solution be as easy as issuing this option
[IMG]http://i.imgur.com/W4l1PTE.png[/IMG]
in the Advance Boot Repair program?

I also thought about deleting that boot.iso file I made manually, but I'm quite worried that I'll further mess things up. 

p.s. I have tried using the Recommended Boot Repair function, but when I get to the part that tells me to copy and paste the following:
> sudo chroot "/mnt/boot-sav/sdb5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sdb5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sdb5" apt-get install -y --force-yes grub-pc

The first two commands run fine(?), but the third command never executes automatically:
> Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdevel-symdump-perl php-net-url efibootmgr secureboot-db libapreq2
  php-net-socket shim libbsd-resource-perl
Use 'apt-get autoremove' to remove them.
Instead, I must manually run that 3rd command (as in, I have to press "enter" for it to run)
I get a very similar output as the one immediately above, and well, now I'm here in these forums. 

Any help is appreciated!

---

### Post by oldfred on 2014-05-21
You do not install grub to partitions (PBR), especially with two drives. If only one drive and you insist on EasyBCD then you may have to install grub to PBR.
Computers only boot from MBR or first sector of a hard drive. With newer BIOS you can choose to boot either drive, so you want Windows boot loader in the MBR of the Windows drive and grub in the MBR of the Ubuntu drive.
Do not run auto fix with Boot-Repair as that installs grub to the MBR of all drives.

Use Boot-Repair advanced mode and choose Windows and reinstall a Windows boot loader to sda. Or use your Windows repair CD or flash drive and use that to fixMBR to restore Windows boot loader to sda.

Most desktops do not need the separte /boot. Some configured as servers with RAID or LVM may or some very old systems. I normally suggest a smaller / (root) of 20 or 25GB at beginning of drive and then rest of drive as /home or data partition(s).

Grub does not use boot flag. A few BIOS only let you boot if you have a boot flag on a primary partition. So we still suggest a boot flag just as we do not know if you have a BIOS that needs it, grub does not. But it should be on a primary partition. Move boot flag from sdb5 to sdb1, but it should not make any difference.

Your first link mention menu.lst which is grub legacy. You have grub2.
You should just be able to use grub2's boot loader in MBR, but I do not know virtual installs.

You now do not show a grub.cfg file? You may need to use Boot-Repair to reinstall grub or create new grub.cfg.

---

### Post by rodrigo9 on 2014-05-22
Hi oldfred! Thanks for the reply. I should mention that I can now boot into windows 7 just fine now, but still having issues with loading into ubuntu. I ended up deleting that boot.iso file I made. I will provide a new boot-info paste.

---

