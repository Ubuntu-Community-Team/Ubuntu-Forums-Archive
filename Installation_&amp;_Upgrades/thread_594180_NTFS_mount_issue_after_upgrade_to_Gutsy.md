---
title: "NTFS mount issue after upgrade to Gutsy"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by ColinuxB on 2007-10-27
Hi

I have a problem mounting NTFS drives. I get the following from a mount -s

mount: /dev/sda4 already mounted or /media/sda4 busy
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sdb1 (New Volume)
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sdb1 (New Volume)


My fstab file looks like this:

<Beginning>

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=60d7c57b-329e-4a36-8afa-796989891ba3 / ext3 nouser,defaults,errors=remount-ro,data=writeback,noatime,auto,rw,dev,exec,suid 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=1100bf9a-f982-4329-abcd-48f1ab9621cd none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0


/dev/sda4 /media/sda4 vfat iocharset=utf8,umask=000,uid=0,gid=0,auto,rw,nouser 0 0
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdc1   /media/sdc1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdc2   /media/sdc2   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb1   /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0

UUID=AC0C7ACD0C7A9256 /media/windows auto nouser,atime,auto,rw,dev,exec,suid 0 0

<End>

fdisk -l gives

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7f400c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       10199    81923436    7  HPFS/NTFS
/dev/sdc2           10200       19457    74364885    7  HPFS/NT


Thus far, I've booted into the windows partition and run a chkdsk on all the NTFS drives.
I've ensured that the relevant ntfs packages are loaded.
As per other posts I've uninstalled and purged evms.

Thoughts?

---

### Post by taurus on 2007-10-27
You also _need_ to shutdown Windows cleanly so don't do the hibernation or standby stuff.

---

### Post by ColinuxB on 2007-10-27
Can confirm that Windows was shut down gracefully before each test.

---

### Post by PmDematagoda on 2007-10-27
I've had a similar problem, I solved it by creating a folder in the /media folder. Then I mounted the device as follows:-

```
sudo ntfs-3g  /dev/locationofdevice /media/nameoffolder -o rw
```

Then the device is mounted in the folder that was created and everything is there.

---

### Post by ColinuxB on 2007-10-28
Tried this - no success.

```


sudo ntfs-3g  /dev/sdb1 /media/windows -o rw


```

Output:

fuse: mount failed: Device or resource busy
FUSE: mount point creation failed
Unmounting /dev/sdb1 (New Volume)

??

---

### Post by taurus on 2007-10-28
What is the error message when you run this command from a terminal?

```
sudo mount -t ntfs /dev/sda1 /media/sda1
```

---

### Post by ColinuxB on 2007-10-28
Here is it:

> 
sudo mount -t ntfs /dev/sda1 /media/sda1
[sudo] password for colin:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0




I've tried the force option - no joy.
Note that sda1 is NOT a USB drive. It's a SATA drive.

---

### Post by szaka on 2007-10-28
> **ColinuxB said:**
> 
```


sudo ntfs-3g  /dev/sdb1 /media/windows -o rw


```

Output:

fuse: mount failed: Device or resource busy
FUSE: mount point creation failed
Unmounting /dev/sdb1 (New Volume)

This means that /dev/sdb1 is either mounted already (you should notice this), or the device mapper, or something else in the kernel, is using/locked the device already, or it's a broken disk (less probably) or a kernel device driver bug (probably). 

Can you send your system logs? /var/log/dmesg, /var/log/daemon.log, /var/log/syslog

Please note that there were TWO problems originally: the unclean shutdown which you already solved and this other one which is completely unrelated. The NTFS-3G team is working only on the NTFS driver but your problem seems to be in a lower layer in the kernel.

Btw, I hope you're not running Windows concurrently which already locked the device ...

---

### Post by ColinuxB on 2007-10-29
Here you are - hope you can read these...

Note that I've updated my reply in my previous post.

---

### Post by rupierto on 2007-10-29
BTW I have similar problem.

Seems kernel proble: booting with older kernel solve the problem

---

### Post by szaka on 2007-10-29
@ColinuxB:

Make sure that /dev/sda1 is not mounted yet then type exactly what was suggested you earlier
```

mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

```
What's the exact output? Your "no joy" comment is unfortunately not useful and enough information to help you.

The other, /dev/sdb device is a Windews Dynamic DIsk (LDM) and it must be mounted differently. Here are some help: [http://www.mjmwired.net/kernel/Documentation/ldm.txt](http://www.mjmwired.net/kernel/Documentation/ldm.txt)

---

### Post by szaka on 2007-10-29
> **rupierto said:**
> BTW I have similar problem.

Seems kernel proble: booting with older kernel solve the problem
Do you mean the below error?
*fuse: mount failed: Device or resource busy*

What's the output of
```

egrep -i 'ntfs|ldm|sd' /var/log/dmesg

```

---

### Post by rupierto on 2007-10-29
Sorry. 
I'm at work, now. 
I'll control the output this afternoon (6-7 hour to wait, I live in Italy) and post sooner as possible.

Thanks

---

### Post by jonssoni on 2007-10-29
[http://ubuntuforums.org/showthread.php?p=3660801#post3660801](http://ubuntuforums.org/showthread.php?p=3660801#post3660801)

I've got that kind of problems...

---

### Post by szaka on 2007-10-29
> **jonssoni said:**
> [http://ubuntuforums.org/showthread.php?p=3660801#post3660801](http://ubuntuforums.org/showthread.php?p=3660801#post3660801)

I've got that kind of problems...
Kernel, SATA bug. Totally irrelevant to any file system. 
Please submit an Ubuntu bug report for the kernel.

---

### Post by ColinuxB on 2007-10-30
Here's the output from the forced mounting

command:
mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda1 ()

(Sorry about the "no luck" comment. As a developer of 20 years standing I should've known better...)

Confirmed that the drive was not previously mounted.

I've checked what previous posters alluded to - yes, if I revert back to kernel subversion 20 (from 22) everything works.

Hence I suspect your thoughts that it is a kernel issue is spot on.

Thanks to szaka (and others)

I'm not familiar with raising bugs - can somebody run with this one?

---

### Post by zuccamonna on 2007-10-30
i've found that: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/151099](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/151099)
probably it's what we're speaking about...

now in gutsy there's not kernel previous 2.6.22-14 so i dont know how come back to 2.6.20 without compile it.

bye

---

### Post by rupierto on 2007-10-30
@ szaka

I think you're right.

My fault: my hdd is FAT formatted (not NTFS) 

I've got 3 hdd:
hda1: win2k
hda5: docs
hdb1: ubuntu file system
hdb2: /home
hdb3: swap
sda1: an old IDE disk FAT formatted and connected to my mobo SATA slot with an adapter cable
Before upgrading it was named "sda1" and everything works fine.



Now, to be clear, this is the situation: 


-- kernel 2.6.22.14 --

No disk icon on the desktop
NO folder "sda1" in /dev
Empty folder "sda1" in /media

A: ntfs-config: NO writing activated

etc/fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=5fd9b4c9-b0f4-403b-a736-d448b54839a8 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb2 :
UUID=6e13c9d9-afb8-4023-a4ec-f6327c469bec /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=6A68315B6831276B /media/hda1 ntfs umask=222,utf8 0 1
# Entry for /dev/hda5 :
UUID=C65847B55847A353 /media/hda5 ntfs umask=222,utf8 0 1
# Entry for /dev/hdb3 :
UUID=cc4d8188-3e2c-49ce-b84b-d2cb9c17f8c9 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
# Entry for /dev/sda1 :
UUID=4462-131B /media/sda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

```

-----------------

B: ntfs-config: writing activated

etc/fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=5fd9b4c9-b0f4-403b-a736-d448b54839a8 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb2 :
UUID=6e13c9d9-afb8-4023-a4ec-f6327c469bec /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=6A68315B6831276B /media/hda1 ntfs-3g defaults,locale=it_IT.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=C65847B55847A353 /media/hda5 ntfs-3g defaults,locale=it_IT.UTF-8 0 1
# Entry for /dev/hdb3 :
UUID=cc4d8188-3e2c-49ce-b84b-d2cb9c17f8c9 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=4462-131B /media/sda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

```

-----------------
egrep -i 'ntfs|ldm|sd' /var/log/dmesg

gives:
```

[    0.000000] ACPI: RSDP signature @ 0xC00F6B80 checksum 0
[    0.000000] ACPI: RSDP 000F6B80, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 48E8 (r1 NVIDIA AWRDACPI     1000 MSFT  100000D)
[   15.974441] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.138669] ACPI: EC: Look up EC in DSDT

```

-------------------
kernel 2.6.20.16

A: ntfs-config: NO writing activated

"sda1" disk mounted (disk icon is on the desktop)
folder "sda1" in /dev
folder "sda1" in /media

etc/fstab
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=5fd9b4c9-b0f4-403b-a736-d448b54839a8 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb2 :
UUID=6e13c9d9-afb8-4023-a4ec-f6327c469bec /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=6A68315B6831276B /media/hda1 ntfs umask=222,utf8 0 1
# Entry for /dev/hda5 :
UUID=C65847B55847A353 /media/hda5 ntfs umask=222,utf8 0 1
# Entry for /dev/hdb3 :
UUID=cc4d8188-3e2c-49ce-b84b-d2cb9c17f8c9 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
# Entry for /dev/sda1 :
UUID=4462-131B /media/sda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

```

B: ntfs-config: writing activated

etc/fstab

.. absolutely the same as case "A"...


egrep -i 'ntfs|ldm|sd' /var/log/dmesg

gives:
```

[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b80
[    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[   14.909331] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.379188] SCSI device sda: 4124736 512-byte hdwr sectors (2112 MB)
[   31.380245] sda: Write Protect is off
[   31.380249] sda: Mode Sense: 00 3a 00 00
[   31.387187] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   31.387261] SCSI device sda: 4124736 512-byte hdwr sectors (2112 MB)
[   31.387273] sda: Write Protect is off
[   31.387275] sda: Mode Sense: 00 3a 00 00
[   31.387291] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   31.387295]  sda: sda1
[   31.465042] sd 0:0:0:0: Attached scsi disk sda
[   31.531633] sd 0:0:0:0: Attached scsi generic sg0 type 0

```

---

### Post by hantms on 2007-11-06
I have the same problem.  Believe me, it's an NTFS drive. :)   It worked fine before in Gutsy until some update.

I hope an update will fix it.

---

### Post by dawynn on 2007-11-12
Please let us know your IDE controller chip type.  (run 'lspci' and look for 'ide')

I'm chasing some issues that may be related to kernel modules left unavailable.

Cheers!

---

### Post by jameson737 on 2007-11-21
mount: /dev/sda4 already mounted or /media/sda4 busy
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.
______________________________________________________________

I don't know who in the hell ask linux user to choose "choice 1" which still ask linux 
user to go back to window when they face issues like this.

Force mount should have been applied by clicking a button or something like that.

Do anyone aspect a new computer user to type command line code?????

---

### Post by torgeir roerbag on 2007-12-19
I've had similar problems after reinstalling gutsy. The solution was simpel:
reboot in windows
in commandprompt type **chkdsk /f**
windows asks if it should scedule job, answer yes
reboot into windows and the check wil be performed.
after that you should be able to reboot into gutsy and you'll notice your windows ntfs partitions mounted and write-enabeled.

good luck (wich has nothing to do with it, but enyway)

---

### Post by hanniph on 2007-12-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/151099](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/151099) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I solved it by removing all **evms** packages

---

### Post by zettai on 2008-01-17
> **hanniph said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/151099](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/151099) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I solved it by removing all **evms** packages

Thank you hanniph!!!!

This worked for me too!!!!

---

