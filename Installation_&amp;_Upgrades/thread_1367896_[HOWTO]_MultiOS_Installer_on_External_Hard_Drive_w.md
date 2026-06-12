---
title: "[HOWTO] MultiOS Installer on External Hard Drive with Grub2"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by magic_ninja on 2009-12-30
[CENTER]**[SIZE="3"]_Create an external hard drive with multiple OS installers_[/SIZE]**[/CENTER]

**_[SIZE="2"]Preface:[/SIZE]_**
I created this guide after spending quite a while googling and getting help on irc, when I realized that there wasn't really a howto on this.  This particular guide goes for Windows 7 Installer and Ubuntu 9.10 installers on the same disk.  This guide assumes you have basic knowledge of how to partition your hard drive with your selected program, and that you are capable of using the appropriate letters/identifiers for your disk in windows and linux.  **YOU HAVE BEEN WARNED!**

**_[SIZE="2"]Materials You Need:[/SIZE]_**

External Hard drive with at least 30 GB of free space
Partitioning Program - I like Acronis Disk director if your in windows, but GParted should work fine, and as you need at least an Ubuntu Live booting method, you will have to boot into Ubuntu by one way or another anyway.

**Windows 7 ISO of your choice **- I used the ultimate x64 bit version myself
**Ubuntu ISO of your choice**
**Bootable ubuntu 9.10 flash drive or cd **- if you don't have Ubuntu installed
**A way to mount the Windows7 ISO in windows (this is native in linux)**

*Remember with the OS installers, you can put 32 bit and 64 bit version installers on the hard drive (the beauty of this).*

**_[SIZE="3"]The Steps[/SIZE]_**

**_[SIZE="2"]Partitioning the Hard Drive:[/SIZE]_**

**Warning:** you will want to erase the entire disk for the first step so back up your data.  If you have the space you can copy it back over afterwards.  Here is how I partitioned my 200GB external drive.

Label - /boot - 2-5 GB+ - ext3 or ext4
This depends on how many linux ISO installers you will use, and how big they are.  I do need to go into some depth on this partition though.  Not all ISOs can be booted with GRUB2, it has to be supported by the ISO (so this is mostly linux ISOS at the moment).

Label - WindowsInstallerx64 - 10GB - NTFS
This of course is your windows installer, you can create other partitions for 32 bit and 64 bit versions or however you want to do this.

Label - Swap - 512 MB - swapfs

Label - Storage - NTFS/EXT3
Whatever is leftover and this is where you will copy your data you backed up back to.

**_[SIZE="2"]Setting up the Installer Files:[/SIZE]_**

Get the windows7 and ubuntu isos copied to the proper directories
Just copy the ubuntu iso or isos over to the /boot/iso directory (create the ISO directory if needed)
*For Linux:*
```

sudo mkdir /media/boot1
sudo mount <boot partition dev name here> /media/boot1
sudo mkdir /media/boot1/boot
sudo mkdir /media/boot1/boot/iso
cp <path to ubuntu iso>/<ubuntu iso name>.iso /media/boot1/iso

```
Copy over the files from the Win7 iso to the root of the WindowsInstallerx64 directory.  Mount your isos under windows and copy the files or follow the linux directions below.
*For Linux:*
```

sudo mkdir /media/win7install
sudo mount <device name for winows 7 installer> /media/win7install
sudo mount -o loop <path to iso>/<win7iso name>.iso /media/cdrom
cp -fr /media/cdrom/* /media/win7install/

```
**PLEASE MAKE SURE YOU DO NOT HAVE A CDROM/DVDROM MOUNTED WHEN YOU RUN THE ABOVE COMMANDS.**

**_[SIZE="2"]Make NTFS Partition Bootable[/SIZE]_**

Boot into windows
Start-->Run-->type cmd-->press ENTER
Find the drive letter for your WindowsInstallerx64 partition ( for instance H: )
```

H: <press enter>(where H: is YOUR drive letter)
cd boot
bootsect.exe /nt60 H:

```

**_[SIZE="2"]Set Up Grub[/SIZE]_**

Reboot into the Ubuntu LIVE ISO
Mount the boot partition
```

sudo mkdir /media/boot1
sudo mount <boot partition device name> /media/boot1

```
Install grub2 and Create grub.cfg
```

sudo grub-install --root-directory=/media/boot1 <your device id here>
	if this command is successful
sudo gedit /media/boot1/boot/grub/grub.cfg

```

Save grub.cfg as soon as you make it.  This is the trickiest part of the whole thing now.  You will have to check over the grub.cfg and make your changes from the template I provide you below.  Use your preferred method to get the UUID.  You will need this so the hard drive will be bootable on other computers.  You will have to use your UUID's in the grub.cfg.  Use this program to get the UUID's and copy and paste them:
```

palimpsest

```OR```
sudo ls /dev/disk/by-uuid
```
grub.cfg template
```
# Timeout for menu
set timeout=10
# Set default boot entry as Entry 0
set default=0
# Entry 0 - WINDOWS7INSTALL
menuentry "Windows 7 Installer-64bit" {
    search --set --fs-uuid <your UUID here>
    chainloader +1
}
# Entry 1 - UBUNTU64INSTALL
menuentry "Ubuntu Live 9.10 64bit" {
 loopback loop /boot/iso/<ubuntu iso filename here>.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/<ubuntu iso filename here>.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}
```

***This is version 1.0 of the guide.  Let me know the problems you have and I will do the best to address them (please PM me letting me know if you found an error).  I hope this helps someone and saves them the time it took for me to set this up.  You can damage your system with this if you mess up the drive letters/system ids.  If you have problems booting from your hard drive and the grub menu loads make sure your file names/paths/uuids are properly set up.***

---

### Post by magic_ninja on 2009-12-31
fixed a couple bugs in this, now i need some opinions from you guys, come on and help me!

---

### Post by Bob1nz on 2010-02-15
Hi AWESOME guide so far
What i am trying to achieve (and it looks like this guide will do the trick nicely) is to have my external portable hdd setup so that i can boot from it and choose which windows installer to install and also have some other live utility disks ie ubcd and the likes.
however im up to the part in the guide where i am partitioning the hdd for my windows iso files and from what i can gather they need a seperate partition for each version for example 1 for vista pro x64 one for vista pro x32 1 for xp home 1 for xp pro ect ect
im just wondering as its not stated in the guide whether the partitions should or need to be primary to be booted as there seems to be a limit of 4 primary partitions.
is there any way around this?
do they all have to be in seperate partitions?

sorry if these seem like dumb questions but i have been trying for months to get something like this to work as it would save me having to carry around a cd case when i go out doing repairs ect

---

### Post by magic_ninja on 2010-02-16
Hi glad to see someone is using the guide.  Well I know that windows7 does not need to be on a primary partition, however your vista installs may need to be.  If it were me I would try one version of vista on the 1st partition, another on the 2nd partition, win7 on the 3rd, and whatever you need for linux or what have you on the others, you will have to, however, adapt this tutorial with the extra steps and drive letters.  Just create a primary partition (you can only hold 3 on a drive, so use an extended/logical for linux).  Here is what you will need to repeat from a cmd promp in windows for each windows drive.

```
H: <press enter>(where H: is YOUR drive letter)
cd boot
bootsect.exe /nt60 H:
```

Let me know if it works.

Also for you live utilities why not just make sure you have enough room on your /boot partition and use grub to load the isos (you will have to get isos that support it of course).

I do not know if this works for xp though, let me know if it does and I'll ammend the guide.

---

### Post by magic_ninja on 2010-04-18
lets get some feedback on this guys.

---

