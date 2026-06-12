---
title: "Can't boot anymore"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tim1 on 2009-08-22
After the recent updates I cannot boot anymore.

When I select Ubuntu in GRUB and press enter I get some message about "invalid executable type".

Am I the only one here?

---

### Post by VMC on 2009-08-22
boot livecd output "sudo fdisk -l" and "sudo blkid". Also output the grub boot string for the Ubuntu your trying to boot.

---

### Post by tim1 on 2009-08-22
fdisk -l
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16       12684   101763742+   7  HPFS/NTFS
/dev/sda3           12685       30402   142313146    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6           12685       14223    12361954+  83  Linux
/dev/sda7           14224       30074   127323126   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8086 MB, 8086618112 bytes
37 heads, 13 sectors/track, 32836 cylinders
Units = cylinders of 481 * 512 = 246272 bytes
Disk identifier: 0x000cc80e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       32837     7897087+   c  W95 FAT32 (LBA)

```


blkid

```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="07D8-0208" TYPE="vfat" 
/dev/sda2: UUID="F62CB6232CB5DEB5" LABEL="OS" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="82B9-FD10" TYPE="vfat" 
/dev/sda6: UUID="e98b32ed-cc4b-4377-95a1-ac0bba254feb" TYPE="ext4" 
/dev/sda7: UUID="8b05aa5d-dc7f-437e-aef5-dc8c19b7befa" TYPE="ext4" 
/dev/sdb1: LABEL="STORE N GO" UUID="CFF6-231B" TYPE="vfat" 
```


the relevant part of menu.lst

```
title		Ubuntu karmic (development branch), kernel 2.6.31-6-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.31-6-generic root=UUID=e98b32ed-cc4b-4377-95a1-ac0bba254feb ro quiet splash 
initrd		/boot/initrd.img-2.6.31-6-generic
quiet
```


This looks pretty normal to me, I guess it had something to do with the last update of the kernel and the image itself is somehow broken.

---

### Post by ajgreeny on 2009-08-22
Try the previous kernel from the grub menu, assuming you didn't uninstall it already.  If you can get that running, purge the newer kernel, make sure it has gone from /var/cache/apt/archives and then reinstall it.  If the package you downloaded the first time was corrupt in some way, it will now be downloaded again, hopefully with better luck.

I agree everything in the grub menu stanza for ubuntu looks right to me too, except you must have edited the second line to read as **root (hd0,5)** as ubuntu now uses the UUIDs by default, as far as I can remember.  That should not affect the booting possibilities, however.  I have done the same on my system, as occasionally the UUID read wrongly, or something, and booting just stopped at the phrase "Starting up" or whatever it says, and never moved to the "loading- please wait" part. Changing to the **root (hd#,#)** system seems to stop that happening.

---

### Post by tim1 on 2009-08-22
Unfortunately I don't have an old kernel, so I cannot boot Ubuntu at all, except from USB.

---

### Post by tim1 on 2009-08-22
I reinstalled an older kernel by booting over USB and chrooting in my karmic install. This didn't help either, so I'm guessing this isn't a problem with the kernel but rather with grub itself.

I going to reinstall grub and see if this helps.

EDIT:

Well, reinstalling GRUB didn't fix it either. I think I'll have to do a reinstall with alpha4

---

### Post by VMC on 2009-08-22
> **tim1 said:**
> I reinstalled an older kernel by booting over USB and chrooting in my karmic install. This didn't help either, so I'm guessing this isn't a problem with the kernel but rather with grub itself.

I going to reinstall grub and see if this helps.

EDIT:

Well, reinstalling GRUB didn't fix it either. I think I'll have to do a reinstall with alpha4

I'm curious, are you sure your running grub and not grub2? If grub2 output "/boot/grub/grub.cfg".

---

### Post by ranch hand on 2009-08-22
That sure looks like a grub-legacy menu.

Is 9.10 installed on 2 partitions or is  the other partiton Jaunty?

---

### Post by Kokopelli on 2009-08-22
I am having a similar problem immediately after upgrading the kernel to 2.6.31-6-generic.  In my case I have both kernels still installed but neither will boot.

This was a fresh install on a second drive, with grub2 installed on the second drive.  I suspect in my case the problem had to do with the rewriting of grub.cfg with the new kernel.  When I did the initial install the drive was the primary (and only) drive in the laptop.  I then moved it to the Ultrabay and booted from the ultrabay if present.  This worked fine until Karmic decided to rewrite grub.cfg at a guess.

Snippet from grub.cfg

```


### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-6-generic" {
	set root=
	linux	/boot/vmlinuz-2.6.31-6-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-6-generic
}
menuentry "Ubuntu, Linux 2.6.31-6-generic (recovery mode)" {
	set root=
	linux	/boot/vmlinuz-2.6.31-6-generic root=/dev/sdb1 ro single 
	initrd	/boot/initrd.img-2.6.31-6-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic" {
	set root=
	linux	/boot/vmlinuz-2.6.31-5-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic (recovery mode)" {
	set root=
	linux	/boot/vmlinuz-2.6.31-5-generic root=/dev/sdb1 ro single 
	initrd	/boot/initrd.img-2.6.31-5-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set d8e82c32e82c1174
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0c0f-4294
	drivemap -s (hd0) ${root}
	chainloader +1
}


```

I tried setting root to (hd1,1) in grub.cfg as well as by editing the command line from grub itself but it did not help.

---

### Post by VMC on 2009-08-22
Your "set root=" is blank. You need to populate it.

---

### Post by Kokopelli on 2009-08-22
As I said, I tried setting root to (hd1,1) but this did not work either.

I posted the grub.cfg as Karmic set it, but I did try setting it to what should be the appropriate value for sdb1...

---

### Post by VMC on 2009-08-23
> **Kokopelli said:**
> As I said, I tried setting root to (hd1,1) but this did not work either.

I posted the grub.cfg as Karmic set it, but I did try seting it to what should be the appropriate value for sdb1...

Post output of:
```
sudo fdisk -l
```

---

### Post by Kokopelli on 2009-08-23
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe11595f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19660   148629568+   7  HPFS/NTFS
/dev/sda2           19661       20673     7658280   12  Compaq diagnostics

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e49b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24328   195414628+  83  Linux
/dev/sdb2           24329       25301     7815622+   5  Extended
/dev/sdb5           24329       25301     7815591   82  Linux swap / Solaris


```

---

### Post by Kokopelli on 2009-08-23
I fixed my problem.  It seems that the missing search lines were the important factor.

```

menuentry "Ubuntu, Linux 2.6.31-6-generic" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7ad3592b-ddb0-4a11-9f41-02b8975c3ce8
	linux	/boot/vmlinuz-2.6.31-6-generic root=UUID=7ad3592b-ddb0-4a11-9f41-02b8975c3ce8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-6-generic
}
menuentry "Ubuntu, Linux 2.6.31-6-generic (recovery mode)" {
	set root=(hd0,1)
        search --no-floppy --fs-uuid --set 7ad3592b-ddb0-4a11-9f41-02b8975c3ce8
	linux	/boot/vmlinuz-2.6.31-6-generic root=UUID=7ad3592b-ddb0-4a11-9f41-02b8975c3ce8 ro single 
	initrd	/boot/initrd.img-2.6.31-6-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic" {
	set root=(hd1,1)
        search --no-floppy --fs-uuid --set 7ad3592b-ddb0-4a11-9f41-02b8975c3ce8
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=7ad3592b-ddb0-4a11-9f41-02b8975c3ce8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic (recovery mode)" {
	set root=(hd1,1)
        search --no-floppy --fs-uuid --set 7ad3592b-ddb0-4a11-9f41-02b8975c3ce8
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=7ad3592b-ddb0-4a11-9f41-02b8975c3ce8 ro single 
	initrd	/boot/initrd.img-2.6.31-5-generic
}

```

I switched the linux lines to use root=uuid=<UUID> because the actual location of the disk will vary based on what system I have it plugged into.  This did not make a difference in booting though.  Interestingly enough what drive I point the "root=(hd0,1)" line to does not appear to make a difference either.  In order to debug I set one kernel to "(hd1,1)" and the other to "(hd0,1)". Both work as long as I have the search line in there.

Since the search lines were missing entirely and root was not set properly I would guess this is a problem with grub-mkconfig.  Regardless I will check my grub.cfg prior to rebooting after an update going forward.

---

