---
title: "Cannot boot from hard drive after installation 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by tony-fury on 2010-09-05
I can boot and run the live CD "ubuntu-10.04.1-desktop-amd64."
Verified checksum and is ok
When I install it via CD or after running in CD mode and installing from the desktop the system will not boot. 250gig SATA drive.
I can't for the life of me get it to boot after installation.
It keeps dropping into 'initramfs' 
I even tried installing "ubuntu-10.04.1-server-amd64" and get the same result.
Is it something to do with the SATA drive?
Any help would be appreciated
Thanks
Tony

Memory 4GiB
Processor AMD Athlon Processor LE-1660
NVIDIA 

> Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sde2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sde5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sde1        4b945eba-befc-4085-8b9b-22800cbde307   ext4                                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        3feb2661-e57f-4c2f-a04c-056bc820739d   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/4b945eba-befc-4085-8b9b-22800cbde307 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sde1/boot/grub/grub.cfg: ===========================


---

### Post by tony-fury on 2010-09-05
No winblows installed. hard drive setup for ubuntu only
bump..

---

### Post by Rubi1200 on 2010-09-05
Have you checked the settings in BIOS? You may need to set it to IDE (I seem to recall from another thread somewhere).

And why is the drive named sde? Normally it would be sda!?!

---

### Post by tony-fury on 2010-09-05
> **Rubi1200 said:**
> Have you checked the settings in BIOS? You may need to set it to IDE (I seem to recall from another thread somewhere).

And why is the drive named sde? Normally it would be sda!?!

I can only assume it named it to sde because it has 4 USB card readers that got named
/dev/sda:
/dev/sdb: 
/dev/sdc:
/dev/sdd:

I will give that a shot.. right now I'm trying an install to an external USB drive

Thanks
T

---

### Post by tony-fury on 2010-09-05
running into a brick wall now..
It wouldn't boot from external USB drive either after installation
Yes, set boot sequence prior to install to 
1 USB
2 CD ROM
3 Hard Disk

Tried setting to AHCI BIOS no luck, choices are AHCI or SATA
I have two on board controllers, IDE & SATA
of course the IDE is supporting the two CD/DVD ROM drives

Going out on a limb now and removing the front four USB card readers from the motherboard.
Seriously stumping the chump now...:confused:

---

### Post by Rubi1200 on 2010-09-05
Sorry, meant AHCI as the thing to change. By the way, what are the computer specs.?
Need to know about RAM and graphics.

Can you boot a LiveCD?

If yes, post the results of the bootscript linked to at the bottom of my post please.

---

### Post by tony-fury on 2010-09-05
> **Rubi1200 said:**
> Sorry, meant AHCI as the thing to change. By the way, what are the computer specs.?
Need to know about RAM and graphics.

Can you boot a LiveCD?

If yes, post the results of the bootscript linked to at the bottom of my post please.

AMD Athlon Processor LE-1660
4 GB RAM 2 x 2GB 
M3M78-VM motherboard built in NVIDIA graphics
I have a linksys PCI 10/100/1000 network card

Yes I can boot LiveCD

Ok, tried a 250 GB IDE drive I have laying around..
Installs and runs fine.. just booted up on it

The problem has to be with the motherboard and the SATA drive
Going to run on this IDE drive now
Thanks
Tony

---

