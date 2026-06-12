---
title: "cannot dual boot"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by ikki_72 on 2012-12-30
i installed ubuntu 12.04 on a second hard disk

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af68f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   147914751    73956352   83  Linux
/dev/sda2       147916798   156301311     4192257    5  Extended
/dev/sda5       147916800   156301311     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dad98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   156297215    78045184    7  HPFS/NTFS/exFAT

```

after setting on bios to boot to second hard disk, i ran
```
$ sudo os-prober
$ sudo upgrade-grub
```

after changed hiden grub to timeot 5 second, i'm able to select windows 8 but it only get to windows loading and then it restarts 

directly booting first hard disk to boot windows 8 successfully boots into windows.

below is my windows menuentry done by os-prober

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 8 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 38A0A8BFA0A884CA
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
``` 

when i tried to change it, **sudo update-grub** changed it back to above entries 

had i missed any step?

---

### Post by ikki_72 on 2012-12-31
i tried editing /etc/grub.d/40_custom
 
```
#!/bin/sh -e
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Windows 8 to GRUB 2 menu"
cat << EOF
menuentry "Windows 8" {
set root=(hd0,1)
chainloader (hd0,1)+1
}
EOF
```

got some error when updating grub

```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sdb1
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 162
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
```

---

### Post by pavitrabalse on 2012-12-31
can we use 2 os system at the same time along with ubuntu????

---

### Post by adityamagadi on 2012-12-31
> **pavitrabalse said:**
> can we use 2 os system at the same time along with ubuntu????


yup thats pretty much possible !! and you are meaning to tell you wanna have totally 3 os's on your system??

---

### Post by sudodus on 2012-12-31
If it is a new system with Windows 8, you might succeed better with Ubuntu 12.10.

General tips:

Try the instructions in the following link to repair your system

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2/Installing[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")

In order to help we might need some more information about your system.

- Can you run the installed Ubuntu system at all?
- What computer is it? cpu, ram, bios or equivalent?

---

### Post by oldfred on 2012-12-31
You said you installed Ubuntu to second drive, but it is showing Ubuntu as sda & Windows as sdb. If SATA drives that usually is port order as read by BIOS.

So if Windows is sdb, it will be hd1 if you have grub in sda. But realize whichever drive you boot from with grub will be hd0, then drives are in port order (normally). I find my flash drives sometimes are anywhere in the order, just to keep me on my toes on which drive is which.

The old, original instructions on adding an entry to 40_custom were actually from a command line where you echo the text into a file. Then most were copy and pasting the echo command also and it worked, but the newest grub does not work with those (incorrect) commands. So remove the echo, cat & EOF commands on any entry to 40_custom.

Some have reported issues chain loading to Windows 8. It seems to have to do with its hibernation. Best not to hibernate any dual booted system anyway.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by ikki_72 on 2012-12-31
> **sudodus said:**
> If it is a new system with Windows 8, you might succeed better with Ubuntu 12.10.

General tips:

Try the instructions in the following link to repair your system

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2/Installing[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")

In order to help we might need some more information about your system.

- Can you run the installed Ubuntu system at all?
- What computer is it? cpu, ram, bios or equivalent?

forgot to mention that my desktop is using mbr mode bios, not gpt

ubuntu is running ok when i choose to boot to second hdd (set it as first boot since bios cannot choose to boot to multiple hdd ordering)

CPU: AMD Athlon 64 X2 4600+
RAM: 4GB

a bit info on bios
```
# dmidecode 2.11
SMBIOS 2.5 present.
48 structures occupying 1721 bytes.
Table at 0x000FC060.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: MS-7309
        Version: V1.9
        Release Date: 08/31/2007
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 512 kB

$ sudo dmidecode -s bios-version
V1.9
```

ubuntu info

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

$ uname -r
3.2.0-29-generic
```

---

### Post by sudodus on 2013-01-01
I am multi-booting Ubuntu alongside with Windows XP (came with the computer) and Windows 8 developer's preview in a computer of similar age. And I use several drives, so my situation is quite similar. My experience is that the SATA drive with Windows XP can be moved (to another SATA port and number) but the drive with Windows 8 cannot be moved if you want to boot it. So you should keep it as the first one, /dev/sda or (hd0).

However it is possible that there are some extra features in the final Windows 8 version, that makes it hard to dual boot.
Ubuntu 12.10 was developed later than 12.04, and should be better managing Windows 8. So if no luck with 12.04, consider installing 12.10 to succeed with dual booting.

But don't skip 12.04 yet. I suggest you try according to the following tips. And look carefully at oldfred's tips and links.

You de-activate 30_osprober like this
```
sudo chmod ugo-x /etc/grub.d/30_os-prober ###
```
and re-activate it again with 
```
sudo chmod ugo+x /etc/grub.d/30_os-prober ###
```

> **ikki_72 said:**
> 
below is my windows menuentry done by os-prober

```
### originally from /etc/grub.d/30_os-prober ###
menuentry "Windows 8 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 38A0A8BFA0A884CA
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
``` 

1. Add this (as is after the 'exec tail' statements) to

[FONT="Courier New"][SIZE="3"]/etc/grub.d/40_custom[/SIZE][/FONT]

Make a backup copy after that

```
sudo cp /etc/grub.d/40_custom /etc/grub.d/40_custom0
```

Check that the backup copy is not executable!

and start tweaking it. I think that grub gets mixed up because you changed the wiring of the drives, so try to deactivate the drivemap command
```
#	drivemap -s (hd0) ${root}
```

First make temporary tests 'live' at boot time in the grub menu (click 'e' to enter edit mode). You can also click 'c' to enter simple commands. For example

***ls***

will show you which drives there are, and help you identify which (drive,partition) is the windows one at boot time.

And when you have found what works to boot Windows, write that into

[FONT="Courier New"][SIZE="3"]/etc/grub.d/40_custom[/SIZE][/FONT]

*Edit*: ... and run ```
update-grub
```

---

### Post by ikki_72 on 2013-01-01
the thing is, i could not boot from hard disk if it had been configured as 2nd hdd on bios.

any other workround? configure grub on win 8?

i need 12.04 for steam linux. the only reason i'm using ubuntu instead of debian.

---

### Post by sudodus on 2013-01-01
> **ikki_72 said:**
> the thing is, i could not boot from hard disk if it had been configured as 2nd hdd on bios.

any other workround? configure grub on win 8?

i need 12.04 for steam linux. the only reason i'm using ubuntu instead of debian.

Maybe this link will help

[[COLOR="red"]https://help.ubuntu.com/community/Grub2/Installing[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")

See for example the chapter about

Reinstalling GRUB 2 from a Working System

What you want to do is to install grub to the boot sector of the first HDD, /dev/sda (to the head of the drive, not to a partition). And you want it to point from there to /boot on the second drive, which should work if you swap the cables again so that the Windows drive is /dev/sdb, and run the following command
```
sudo grub-install /dev/sdX  # Example: sudo grub-install /dev/sd[COLOR="Red"]b[/COLOR]
```

Normally grub identifies the partition with its UUID, so that it will be found even after changing place and [COLOR="red"]x[/COLOR] in /dev/sd[COLOR="red"]x[/COLOR] for the drive.

---

### Post by ikki_72 on 2013-01-01
thanks for guiding me on solving this problem sudodus
that method definitely worked

after i ran 
```
sudo grub-install /dev/sdb
sudo update-grub
``` 

from within ubuntu, i set it to boot windows 8 hdd and grub shows
afterward i selected windows 8 and bam! it boots into windows 8 :D

---

### Post by sudodus on 2013-01-01
You are welcome :KS

---

