---
title: "install-mbr problem"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by saikumar_divvela on 2007-04-06
Hi,

I have a  problem with install-mbr command for the newly installed ubuntu6. 
I will give brief information of what i am doing.
We are giving our product with ubuntu 6 operating system in one CD. We are using SGS toolkit (provided by IBM)  for installing  ubuntu and then our product in IBM server with raid capabilities.

Using SGS toolkit first PS DOS is installed in the system and all the cd contents are moved to hard disk.  Now **initramfs image** is loaded into memory along with **vmlinuz (for kernel)** and  the **init** scripts load the required modules and a script,which does partitioning of hard disk, is called.
The partition details are like this.

Now system goes for restart and SGS toolkit now calls the initrd image with vmlinuz(for kernel 2.6.17).  The init  script loads all the required modules and calls another script.

This script creates file systems on the partitions which are created in previous stage.
Using debootstrap  i am installing ubuntu6  on the directory /mnt/root.
**debootstrap --unpack-tarball /mnt/DOS/basedebs.tar -edgy /mnt/root**
The configuration required for the debootstrap is available as part of initramfs image
After installing the ubuntu6 the following command is called

**install-mbr -v -e =13f -p 3 -i =n -t 54 /dev/sda**

and then the linux image  **linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb** is installed. This will create the vmlinuz and initrd images.
Now the command **lilo-v** is called. The required lilo.conf is copied to /etc directory as part of script.

lilo.conf contents are  

boot=/dev/sda3
root=/dev/sda6
install=/boot/boot.b
map=/boot/map
#serial=0,57600
prompt
timeout=30
default=Linux
other=/dev/sda1
        label=PC-DOS
        boot-as=0x80    # must be C:
image=/vmlinuz
        label=Linux
        initrd=/initrd.img
        append="acpi=on console=ttyS0,57600"
image=/vmlinuz.old
        optional
        label=Linux.old
        initrd=/initrd.img.old
        append="acpi=on console=ttyS0,57600"

 The required fstab is also copied to etc directory. The contents of /etc/fstab are

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda6       /       ext3    defaults,errors=remount-ro      0 1
/dev/sda3       /boot   ext2    defaults        0 2
/dev/sda2       /SuSE   ext3    defaults        0 2
/dev/sda1       /mnt/DOS        msdos   noauto  0 0
/dev/sda7       /var/lib        ext3    defaults        0 2
/dev/sda5       none    swap    sw      0 0
/dev/fd0        /floppy auto    rw,user,noauto  0 0
/dev/cdrom      /cdrom  auto    ro,user,noauto  0 0
proc    /proc   proc    defaults        0 0
usbdevfs        /proc/bus/usb   usbdevfs        defaults        0 0
#
tmpfs   /SuSE/tmp       tmpfs   defaults        0 0
tmpfs   /SuSE/dev/shm   tmpfs   defaults        0 0
proc    /SuSE/proc      proc    defaults        0 0
usbdevfs        /SuSE/proc/bus/usb      usbdevfs        defaults        0 0
#
### ADD YOUR OWN ENTRIES AFTER THIS LINE.  DO NOT DELETE THIS LINE. ###

After lilo is configured we are installing our product and then  system goes for restart. At this stage the system should boot up with the operating system i have installed.

For me the problem is the command  
install-mbr -v -e =13f -p 3 -i =n -t 54 /dev/sda 
is failing with error : **/dev/sda no such file or directory.**
Becuase of this when the system is restarted  it is loading only PC DOS and not able to pick the ubuntu 6 i have installed.
what is the use of the file **/usr/lib/debootstrap/devices.tar.gz**. Is this file related to the problem for not finding the hard disk 


Any  help on this is highly appreciated. 


Thanks & Regards
Sai

---

