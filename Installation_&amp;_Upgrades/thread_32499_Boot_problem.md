---
title: "Boot problem"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by TheDude on 2005-05-08
I recently did a clean install of Hoary in after deciding to get rid of xp completly.  After the initial reboot during the install, my computer said that there was some sort of boot failure and that it was trying to read from the floppy (there was nothing in there).  I went into the bios and made sure that it wasn't set to boot from the floppy, but I still got the same error message.  I decided to try and reformat and try to install again, but when I rebooted with my Windows xp disc in the cd drive, it booted up Hoary and let me finish the install.  Now everytime I reboot, I have to have the windows xp disc in or it gives me that same error message.  It's not really a problem since everything is running fine, it's just a little inconvenient to always have to have that disc in my cd drive.  Anyone know what could be causing this?

---

### Post by bigbangbigbigbang on 2005-05-08
Try running (from ubuntu, as root or with sudo) grub-install /dev/hda

---

### Post by kosmic on 2005-05-08
Please go to your bios and post where the information of the drives, for example what the first drive to boot, the 2nd, the 3rd and so on.

Then please write what is the exact error message that the boot gives to you when you boot the computer without any cd in the drive.

Thanks

---

### Post by TheDude on 2005-05-08
[QUOTE=bigbangbigbigbang]Try running (from ubuntu, as root or with sudo) grub-install /dev/hda[/QUOTE]

tried and got this:

/dev/hda: Not found or not a block device.

---

### Post by TheDude on 2005-05-08
[QUOTE=kosmic]Please go to your bios and post where the information of the drives, for example what the first drive to boot, the 2nd, the 3rd and so on.

Then please write what is the exact error message that the boot gives to you when you boot the computer without any cd in the drive.

Thanks[/QUOTE]

bios info, boot options:
first boot device: ATAPI cdrom
second: floppy
third: FLOPTICAL
fourth: 1st IDE HD

error message:

Boot Failure
Insert BOOT diskette in A:
Press any key when ready_

I tried removing the floppy from the boot options completely and I get this:

Boot Failure
Reboot and Select proper Boot device
or INsert Boot Media in selected Boot device
Press any key when ready

---

### Post by bigbangbigbigbang on 2005-05-08
[QUOTE=TheDude]tried and got this:

/dev/hda: Not found or not a block device.[/QUOTE]

Then it seems that your HD is not primary master. Do cat /etc/fstab and see what the device name is. (/dev/hdb, hdc or whatever). Then rerun grub-install on that device, but WITHOUT the partition number.

---

### Post by TheDude on 2005-05-08
[QUOTE=bigbangbigbigbang]Then it seems that your HD is not primary master. Do cat /etc/fstab and see what the device name is. (/dev/hdb, hdc or whatever). Then rerun grub-install on that device, but WITHOUT the partition number.[/QUOTE]

not sure that I did that correctly, but I still get this:


Boot Failure
Reboot and Select proper Boot device
or INsert Boot Media in selected Boot device
Press any key when ready

---

### Post by bigbangbigbigbang on 2005-05-08
what is the device name in /etc/fstab?

---

### Post by TheDude on 2005-05-08
[QUOTE=bigbangbigbigbang]what is the device name in /etc/fstab?[/QUOTE]

/dev/hde1

---

### Post by bigbangbigbigbang on 2005-05-08
how many harddisks have you got? Could you see in the Bios, what devices are there on wich IDE controller?

---

### Post by TheDude on 2005-05-08
[QUOTE=bigbangbigbigbang]how many harddisks have you got? Could you see in the Bios, what devices are there on wich IDE controller?[/QUOTE]

I have 2 harddisks but it's only recognized one

---

### Post by bigbangbigbigbang on 2005-05-09
if your bios recognizes only one HD then probably you will have to open up your box and make sure that they are connected to the right IDE controllers and have been properly jumpered.
I would connect one HD to the first controller as master (hda) and the second as slave on the second controller (hdd)
You also have to make sure that your boot sequence in the bios is configured accordingly. You have to include the same HD that you installed grub on in the boot sequence.
But be careful, because if you change the controller where you connect your harddrives, their device names will change too. That means that you will have to edit /etc/fstab and /boot/grub/menu.lst so that they correspond to your effective connections.
Otherwise you will have to reinstall in order to be able to boot after making these changes

---

### Post by kosmic on 2005-05-09
bios info, boot options:
 first boot device: ATAPI cdrom
 second: floppy
 third: FLOPTICAL
 fourth: 1st IDE HD


ok just a guess, but go to your bios and change like this

First boot device : 1st IDE HD
second: ATAPI cdrom
Third: N/A
Fourth: N/A

go to your ubuntu system and type grub-install, and see if it works

---

### Post by TheDude on 2005-05-11
[QUOTE=kosmic]bios info, boot options:
 first boot device: ATAPI cdrom
 second: floppy
 third: FLOPTICAL
 fourth: 1st IDE HD


ok just a guess, but go to your bios and change like this

First boot device : 1st IDE HD
second: ATAPI cdrom
Third: N/A
Fourth: N/A

go to your ubuntu system and type grub-install, and see if it works[/QUOTE]

ok, when I do grub-install it says this 
> ~$ grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

not sure what to do

---

### Post by bigbangbigbigbang on 2005-05-12
[QUOTE=TheDude]ok, when I do grub-install it says this 


not sure what to do[/QUOTE]

you have to run grub-install /dev/hda, hdb, hdc, hdd, hde, ... whatever.
At first you have to find out, which one that HD is, that appears as "1st IDE HD" in your Bios in the boot sequence. You have to install grub onto that device.

1st HD on 1st controller (primary master): /dev/hda
2nd HD on 1st controller (primary slave): /dev/hdb
1st HD on 2nd controller (secondary master): /dev/hdc
2nd HD on 2nd controller (secondary slave): /dev/hdd
1st HD on 3rd controller (tertiary master): /dev/hde
2nd HD on 3rd controller (tertiary slave): /dev/hdf

So you have to tell grub-install with a device name as parameter, where it should install itself. And this device (HD) must be included in the boot sequence in your bios.

---

### Post by TheDude on 2005-05-13
[QUOTE=bigbangbigbigbang]you have to run grub-install /dev/hda, hdb, hdc, hdd, hde, ... whatever.
At first you have to find out, which one that HD is, that appears as "1st IDE HD" in your Bios in the boot sequence. You have to install grub onto that device.

1st HD on 1st controller (primary master): /dev/hda
2nd HD on 1st controller (primary slave): /dev/hdb
1st HD on 2nd controller (secondary master): /dev/hdc
2nd HD on 2nd controller (secondary slave): /dev/hdd
1st HD on 3rd controller (tertiary master): /dev/hde
2nd HD on 3rd controller (tertiary slave): /dev/hdf

So you have to tell grub-install with a device name as parameter, where it should install itself. And this device (HD) must be included in the boot sequence in your bios.[/QUOTE]

ok, so it's the 1st HD on the 1st controller, but it wont work when I do grub-install /dev/hda ](*,) 

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

---

### Post by bigbangbigbigbang on 2005-05-15
[QUOTE=TheDude]ok, so it's the 1st HD on the 1st controller, but it wont work when I do grub-install /dev/hda ](*,) 

What is exactly the error message?

---

### Post by TheDude on 2005-05-15
[QUOTE=bigbangbigbigbang][QUOTE=TheDude]ok, so it's the 1st HD on the 1st controller, but it wont work when I do grub-install /dev/hda ](*,) 

What is exactly the error message?[/QUOTE]

when i try with /dev/hda i get this:

 grub-install /dev/hda
/dev/hda: Not found or not a block device.

when i try with /dev/hde1 u get this:

grub-install /dev/hde1
rm: cannot remove `/boot/grub/stage1': Permission denied

---

### Post by ssam on 2005-05-15
try

sudo grub-install /dev/hde

to get full privileges, it will ask for your user password

---

### Post by TheDude on 2005-05-16
[QUOTE=ssam]try

sudo grub-install /dev/hde

to get full privileges, it will ask for your user password[/QUOTE]

tried that and got this:

Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hde
(hd1)   /dev/hdf

---

