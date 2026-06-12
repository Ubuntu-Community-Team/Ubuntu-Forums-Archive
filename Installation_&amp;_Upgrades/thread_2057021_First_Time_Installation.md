---
title: "First Time Installation"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by Newkastle on 2012-09-12
I am attempting to install unbuntu via CD ROM on a desktop PC.  I have tried with both the 32 and 64 bit versions and I get the same result.  After starting the PC, the ubuntu logo displays with the alternating white/red dots indicating "loading" for approximately 20 seconds.  The display then locks up showing an alternating white/black sort of test pattern, followed by the CD ROM drive winding down.  Any ideas?  Hardware issue?  :confused:

---

### Post by josephmills on 2012-09-12
Did you check the md5sum ? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by opensshd on 2012-09-12
No... sounds like you are trying to install 3.6 rc3 which did the same thing to me using the nouveau graphics driver.

What version do you have? What video card do you have? I guess nvidia?

---

### Post by Newkastle on 2012-09-12
> **opensshd said:**
> No... sounds like you are trying to install 3.6 rc3 which did the same thing to me using the nouveau graphics driver.

What version do you have? What video card do you have? I guess nvidia?

Yep, running an Nvidia 8800 GTX.  I downloaded the 32 and 63 bit versions of Ubuntu Desktop 12.04 LTS.  Did you have better luck with an older version?

---

### Post by opensshd on 2012-09-12
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)

I think this is what your experiencing?

---

### Post by opensshd on 2012-09-12
There are a number of possible remedies... alternate (non-graphical) install, boot graphics safe mode, then switching out nouveau for the proprietary driver that should now be current in the repo's.

Will subscribe to this thread :)

you basically want to 

sudo apt-get nvidia-current

sudo apt-get remove nouveau

*i think* :)

---

### Post by opensshd on 2012-09-12
Running a check on current version in the repo's gives me this:

sudo apt-cache policy nvidia-current
 
nvidia-current:
  Installed: 295.40-0ubuntu1.1
  Candidate: 295.40-0ubuntu1.1

I think you'll be alright with that ;)

---

### Post by oldfred on 2012-09-12
You probably need nomodeset to get it to boot the first time, then you can install the nVidia driver suggested by Ubuntu or manually as posted above.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by Newkastle on 2012-09-15
OK, so I got it to start the installation process using the method suggested above.  However, when I get to the installation screen that should allow me to pick the drive/partition to install on, the big window that should show the drive is blank.  The SATA drive is recognized in the BIOS, but I'm assuming it should show up during this part of the installation.  The drop down box labeled "Device for boot loader installation" says "/dev/sda" as the default.  Am I missing something?  I only have one drive installed in the PC.  Thanks again...

---

### Post by oldfred on 2012-09-15
From liveCD terminal  post this:

sudo parted /dev/sda unit s print

---

### Post by Newkastle on 2012-09-15
Model: ATA Maxtor 6Y120M0 (scsi)
Disk /dev/sda: 240121728s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number    Start   End        Size        Type    File system  Flags
 1        63s     240091424s 240091362s  primary ext3         boot

---

### Post by oldfred on 2012-09-15
You have one large ext3 partition. I would think installer should show it.

From liveCD use gparted. Does gparted show partition and does it have any colored icons for warnings or errors next to it? If so click on warning to see what it is.

---

### Post by Newkastle on 2012-09-15
Yes, GParted recognizes the partition and there aren't any errors.  Newb question, under status it says "Not Mounted", does this need to be mounted to work?

EDIT:  When clicking on the drive I get this error:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by opensshd on 2012-09-15
and from a terminal, can you paste the relevant errors from 

```
dmesg|tail
```

Check out info on fsck (file system check) or e2fsck (for ext2/3/4 fstypes).

```
man fsck
```

I'm not sure whats happening here, shows sda and sde, perhaps also post output of

```
sudo lshw -C disk -C volume
```

Might be more info here:

[http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-hdc3-373428/](http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-on-dev-hdc3-373428/)

---

### Post by Newkastle on 2012-09-16
ubuntu@ubuntu:~$ dmesg|tail
[  152.395380] QNX4 filesystem 0.2.3 registered.
[  300.856582] JBD: Journal too short (blocks 1-268).
[  300.856587] JBD: recovery failed
[  300.856591] EXT3-fs (sde1): error loading journal
[  301.008023] JBD: Journal too short (blocks 1-268).
[  301.008027] JBD: recovery failed
[  301.008030] EXT3-fs (sde1): error loading journal
[  902.228597] JBD: Journal too short (blocks 1-268).
[  902.228602] JBD: recovery failed
[  902.228606] EXT3-fs (sde1): error loading journal
ubuntu@ubuntu:~$ sudo lshw -C disk -C volume
  *-disk                  
       description: ATA Disk
       product: Maxtor 6Y120M0
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sde
       version: 0956
       serial: Y3N3M3QE
       size: 114GiB (122GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=6aec979e
     *-volume
          description: EXT3 volume
          vendor: Linux
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sde1
          version: 1.0
          serial: e0f139dd-1027-0000-a50b-806e6f6e6963
          size: 114GiB
          capacity: 114GiB
          capabilities: primary bootable journaled ext3 ext2 initialized
          configuration: filesystem=ext3 label=Newkastle state=clean

---

### Post by oldfred on 2012-09-16
See if a full filecheck works.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

