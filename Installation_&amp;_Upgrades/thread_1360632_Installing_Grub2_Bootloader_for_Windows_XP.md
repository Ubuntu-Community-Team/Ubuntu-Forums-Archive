---
title: "Installing Grub2 Bootloader for Windows XP"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by BCollar on 2009-12-21
Hello all,

I am currently trying to restore my computer to Windows XP.  

My computer came with a 'restore cd' and not a Windows XP 'setup cd'. 

I ran the restore cd which erased all partitions and installed restore files, however, because the Ubuntu 9.10 I had previously installed changed the Master Boot Record- it will not boot windows. 

I re-installed Ubuntu but I am getting:

Grub> file not found.
grub rescue>

However none of the Grub2 commands work.

 have both 9.10 and 9.04 live cds.

I tried making a Mbrfix boot SD card.  But I couldn't get to a working prompt.

I tried reinstalling Ubuntu,  but I got the same error.

There seems to be several ways to reinstall Grub2.  But not specifically for my need.

Ideally I would like to install/reinstall Grub2 Boot Loader without installing Ubuntu on any partitions-  

Is this possible?  I am also willing to explore other options.

---

### Post by darkod on 2009-12-21
Boot with the 9.10 ubuntu cd, Try Ubuntu option.
In terminal execute:
sudo fdisk -l

That will show you your partitions. Depending how you installed ubuntu you will have one larger linux partition (probably /dev/sda5) and one smaller linux swap partition (probably /dev/sda6).

Then in terminal reinstall grub2 with:
sudo mount /dev/sda5 /mnt (change /dev/sda5 depending on the fdisk results)
sudo grub-install --root-directory=/mnt/ /dev/sda

That should do it.

---

### Post by BCollar on 2009-12-21
I think there is a mistake somewhere, probably mine.  This is what I tried in Terminal:


ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc64ad79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12161    97683201    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt ntfs
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda ntfs
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specified by
--root-directory, and uses grub-setup to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$

---

### Post by hariks0 on 2009-12-21
The below link may solve your problem.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by darkod on 2009-12-21
[COLOR=Red]Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc64ad79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12161    97683201    7  HPFS/NTFS[/COLOR] 

You said you reinstalled ubuntu. You don't have ubuntu here at all, at least not as full install. Did you use wubi?
You see you only have one partition on the whole drive, and that's ntfs. There was no need to continue with the commands since you don't even have linux partition.
I don't know what you did but you do not have ubuntu here. Maybe wubi inside windows.

---

### Post by BCollar on 2009-12-21
this isn't quite solved yet-

---

### Post by SecretCode on 2009-12-21
> **BCollar said:**
> I am currently trying to restore my computer to Windows XP.
Do you really want to reinstall grub2? Don't you instead want to restore the windows bootloader?

> **BCollar said:**
> I tried making a Mbrfix boot SD card.  But I couldn't get to a working prompt.
Since you don't have a windows setup disc you need another way of restoring the NTLDR MBR. What exactly did you try here? And do you mean USB? I wasn't aware most systems could boot from an SD card.

eta: n/m, I see you fixed it

---

### Post by SecretCode on 2009-12-21
> **BCollar said:**
> Thank you all for your responses, Hariks0's link to thread 1014708 provided **an easy solution-  and it worked**.  I now have have a functioning boot.  Which leads me to another issue i'll bring up in another thread.

What was your solution? Do you have grub2 working on this system which only has one partition?

---

### Post by BCollar on 2009-12-21
Now that NTFS is the only partition and the computer is equipped with a Grub v.1.97 bootloader (installed from the (9.10 Karmic cd)  what can I do?
It boots to an SH prompt.  But when I command "boot" it says "no kernel installed."  

Is there a way to get the bootloader to boot Windows XP without installing it in a Linux environment?

---

### Post by BCollar on 2009-12-21
insert the Ubuntu live cd > install 'Mbr' from the package manager > in terminal type **sudo install-mbr /dev/sda ** (sda or drive designation) > restart!

---

