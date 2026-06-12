---
title: "Booting Process"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by kr0b1t on 2010-02-21
[FONT=Arial]I just got a new laptop ( 2 days ago ), and installed Ubuntu 9.10 ( 64 bits ), but some of the things didn't work, so since I'm more familiar with Fedora, I installed Fedora 12 ( 64 bits ) on a different partition.  Here is were problems started.  Before Fedora, I was able to load grub and boot without a problem, after fedora, when booting I get a[/FONT][FONT=Courier New][FONT=Arial] [I]boot failure hard drive
[/I][/FONT]
Using the Ubuntu installation CD,I'm able to select the* [ Boot from primary hard drive ]*, see grub menu and boot without a problem.

I have re-installed grub using:

[/FONT]```
grub-install /dev/sda
```Still the same problem.

I have downloaded and run _[boot_info_script]("http://sourceforge.net/projects/bootinfoscript/") _ and found no error in my MBR or any partitions.

Partial Results:
```

Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


```I have even gone to the process of a complete re-install and still have the same problems.

I believe that the problem is not grub or the MBR.  So I'm think what happens before loading the MBR into mem to boot. POST is done without a problem -- at least there is not errors until selecting the HD as the booting device -- , how can a debug what is happening at booting time to be able to fix the problem?

Any ideas out there?

---

### Post by darkod on 2010-02-21
The part of the results file you posted doesn't show anything. Except that you do have grub2 on the MBR of the hdd.

Is the error still there?

Post the whole content of the results to see if grub.cfg is correct.

---

### Post by kr0b1t on 2010-02-21
Here it is:

```

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 2e2cb2d9-c443-475a-8b95-77700188c4b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2e2cb2d9-c443-475a-8b95-77700188c4b8
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=2e2cb2d9-c443-475a-8b95-77700188c4b8 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2e2cb2d9-c443-475a-8b95-77700188c4b8
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=2e2cb2d9-c443-475a-8b95-77700188c4b8 ro single
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

```

Since I'm able to load this configuration file once I boot from the CD, I'm assuming this is correct.

---

### Post by kansasnoob on 2010-02-21
We need to see the full output, not just bits and pieces.

---

### Post by kr0b1t on 2010-02-21
Hey, I found the problem.  Looking back at you asking for all the info, here is a disk information 

```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7add4962

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   107,523,044   104,448,997  83 Linux
/dev/sda3         107,523,045 1,225,888,019 1,118,364,975   5 Extended
/dev/sda5         107,523,108   115,523,414     8,000,307  82 Linux swap / Solaris
/dev/sda6    *    115,523,478   215,528,039   100,004,562  83 Linux
/dev/sda7    *    215,528,103   315,532,664   100,004,562  83 Linux
/dev/sda8         315,532,728   615,530,474   299,997,747  83 Linux
/dev/sda9         615,530,538   915,528,284   299,997,747  83 Linux
/dev/sda10        915,528,348 1,065,462,929   149,934,582  83 Linux
/dev/sda11      1,215,526,158 1,225,888,019    10,361,862  83 Linux
/dev/sda4       1,225,893,888 1,250,263,039    24,369,152  17 Hidden HPFS/NTFS


```

Notice that the first partition ( as was in the system before I installed Ubuntu ) is not set as bootable.,  So I deleted /dev/sda1 and /dev/sda2 and created a new partition re-installing Ubuntu on it.

[CODE=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7add4962

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   107,523,044   107,522,982  83 Linux
/dev/sda3         107,523,045 1,225,888,019 1,118,364,975   5 Extended
/dev/sda5         107,523,108   115,523,414     8,000,307  82 Linux swap / Solaris
/dev/sda6    *    115,523,478   215,528,039   100,004,562  83 Linux
/dev/sda7         215,528,103   315,532,664   100,004,562  83 Linux
/dev/sda8         315,532,728   615,530,474   299,997,747  83 Linux
/dev/sda9         615,530,538   915,528,284   299,997,747  83 Linux
/dev/sda10        915,528,348 1,215,526,094   299,997,747  83 Linux
/dev/sda11      1,215,526,158 1,225,888,019    10,361,862  83 Linux
/dev/sda4       1,225,893,888 1,250,263,039    24,369,152  17 Hidden HPFS/NTFS

[/CODE]

Even after the installation of Ubuntu in /dev/sda1, that partition is not toggled as bootable.

So I change the partition to bootable with fdisk, and now I can boot without a problem.  

The OS that I'm using right now is in /dev/sda6, grub is installed correctly and points to a correct partition.  I've never seen a problem with having to have a bootable partition in the first partition ( /dev/sda1 ) as bootable.

I will try to re-create this problem in a different environment.  What if a I want to have a swap partition as my first partition?

---

### Post by oldfred on 2010-02-21
One of your posting shows two bootable partitions, you can only have one. Linux does not required a bootable flag, but I just learned today from one of meierfra's  posts that some BIOS require at least one bootable flag on the drive.

---

### Post by meierfra. on 2010-02-21
> some BIOS require at least one bootable flag on the drive.
More precisely: Some Bios require a boot flag on a **primary** partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a  boot flag.

Those extra boot  flags on /dev/sda6 and /dev/sda7 are probably completely ignored and should not cause any problems

---

