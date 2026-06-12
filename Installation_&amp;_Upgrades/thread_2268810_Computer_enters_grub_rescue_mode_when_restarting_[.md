---
title: "Computer enters grub rescue mode when restarting [Ubuntu 14.10]"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by DaftGiraffe on 2015-03-11
I recently tried to install ubuntu to have my computer dual boot with the choices being either ubuntu or windows 7.
However, whenever I restart my computer, either restart from windows or ubuntu, it loads up and before the grub
menu appears it gives an error and puts me in 'rescue mode' for grub. When I shutdown the computer normally, or
enter grub rescue mode and then shut down, it loads up fine to the grub menu. I'm not very experience with linux
at all, what can I do to fix this?

The error says something like "no such device" and then a string of characters, numbers, and dashes. I installed
linux on a separate hard drive.

---

### Post by Bashing-om on 2015-03-11
jland98; Hi ! Welcome to the forum.

I will be the one to start this and get the preliminaries done, so we know what we are working with:
Boot into the install as best you can and
post back - Between code Tags - the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub
sudo grub-editenv list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
 all this jumbo is to show the hard drive's partitioning ( what is installed where), the unique identifiers assigned, parameters of grub, where grub is installed to, and if there was a problem when last ubuntu booted.

Then we sort this out and see what we are going to do,

[INDENT][INDENT][INDENT]it;s all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-11
Alright, here goes.

sudo fdisk -lu
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x498cd6a2


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28674047    14336000   27  Hidden NTFS WinRE
/dev/sda2   *    28674048    28878847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28878848  1465147119   718134136    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003929c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   721199797   360599867+   7  HPFS/NTFS/exFAT
/dev/sdd2       721201150  1953523711   616161281    5  Extended
/dev/sdd5       721201152  1945139199   611969024   83  Linux
/dev/sdd6      1945141248  1953523711     4191232   82  Linux swap / Solaris



```
sudo parted -l
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x498cd6a2


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28674047    14336000   27  Hidden NTFS WinRE
/dev/sda2   *    28674048    28878847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28878848  1465147119   718134136    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003929c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   721199797   360599867+   7  HPFS/NTFS/exFAT
/dev/sdd2       721201150  1953523711   616161281    5  Extended
/dev/sdd5       721201152  1945139199   611969024   83  Linux
/dev/sdd6      1945141248  1953523711     4191232   82  Linux swap / Solaris



```
sudo blkid
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x498cd6a2


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28674047    14336000   27  Hidden NTFS WinRE
/dev/sda2   *    28674048    28878847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28878848  1465147119   718134136    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003929c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   721199797   360599867+   7  HPFS/NTFS/exFAT
/dev/sdd2       721201150  1953523711   616161281    5  Extended
/dev/sdd5       721201152  1945139199   611969024   83  Linux
/dev/sdd6      1945141248  1953523711     4191232   82  Linux swap / Solaris



```
sudo debconf-show grub-pc
```
  grub-pc/chainload_from_menu.lst: true  grub-pc/timeout: 10
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/install_devices_failed: false
  grub2/linux_cmdline:
  grub-pc/hidden_timeout: true
  grub-pc/kopt_extracted: false
  grub-pc/install_devices_disks_changed:
  grub-pc/partition_description:
  grub-pc/postrm_purge_boot_grub: false
  grub2/device_map_regenerated:
  grub2/linux_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub-pc/install_devices_failed_upgrade: true
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3750528AS_9VP1AKZD
  grub-pc/disk_description:
  grub-pc/mixed_legacy_and_grub2: true



```
sudo grub-probe -t device /boot/grub
```
/dev/sdd5


```
sudo grub-probe -t fs_uuid /boot/grub
```
98fac20e-d5a1-4533-bf4f-53c2760240d4


```
sudo grub-editinv list
This command didn't show anything for me, it just ran to the next line, as if I had ran a command without typing in anything.

---

### Post by Bashing-om on 2015-03-11
jland98; Well;

So far so good, all looks proper to me. A no return from " sudo grub-editenv list " is a good thing, But, check your spelling it is -editenv vice 'inv'.

So, what is in sdd1 ? Is that just a data partition to be shared between Windows and ubuntu ?
Are you selecting in bios which operating system to boot ? Windows on the 1st hard drive (sda), and ubuntu on the other hard drive (sdd) ?
I am rather mystified why the device is assigned 'sdd' - the 4th device detected, rather than 'sdb' .

When you switch operating systems are you fully shutting down, rather than hibernating ?

Depending on how you are booting ( and what is in the /etc/fstab file) consider (RE)installing the bootcode to the MBR of 'sdd' .
For now let's verify the "fstab" file - File System TABle :
```

sudo blkid
cat /etc/fstab

```

cover our bases
[INDENT][INDENT]take a leap of faith
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-11
Alright, I rechecked the grub-editenv command, still nothing.

As far as I can tell, sda is my internal hard drive, which contains windows 7, and sdd is an external hard drive that I used
to put linux on. The external drive has some other data on it (backups of the computers we have), and ubuntu is partitioned
to have ~750 gigs of its terabyte capacity.

I'm not quite sure what is in sdd1, but it is possible that is the backups I noted above. When I start up my computer, it loads
a grub menu (correct me if its the wrong term). There's a few options, including Ubuntu and the Windows 7 (Loader).

When I swap my OS, I shut down my computer, I haven't tried hibernating, but I don't know where that option is in Ubuntu.

When I typed
```
sudo blkid
cat /etc/fstab
```
I got these results, I'm not sure what they mean.
```
/dev/sda1: LABEL="PQSERVICE" UUID="9070F69E70F689EC" TYPE="ntfs" /dev/sda2: LABEL="SYSTEM RESERVED" UUID="00FC9AF6FC9AE4E6" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="9A284E2B284E06AB" TYPE="ntfs" 
/dev/sr0: LABEL="Ubuntu 14.04.2 LTS amd64" TYPE="iso9660" 
/dev/sdd1: LABEL="Expansion Drive" UUID="7E3C3B123C3AC545" TYPE="ntfs" 
/dev/sdd5: UUID="98fac20e-d5a1-4533-bf4f-53c2760240d4" TYPE="ext4" 
/dev/sdd6: UUID="e7a1b7d5-88ee-4055-acb6-9ba64f759dc0" TYPE="swap" 
jared@jared-Aspire-X1301:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sde5 during installation
UUID=98fac20e-d5a1-4533-bf4f-53c2760240d4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=e7a1b7d5-88ee-4055-acb6-9ba64f759dc0 none            swap    sw              0       0

```

---

### Post by Bashing-om on 2015-03-11
jland98; Well; OK,

'sdd' as an external drive explains why it is picked up later (sdd).
As you can boot to a grub menu, boot code is installed properly to the MBR, not booting from grub to the operating system says a config file some where is hosed.
Let's try and boot this sucker, if it fails, maybe get some additional info to point us to where the failure occurs .
Boot to grub, and with the ubuntu kernel selected to boot, press the 'c' key for a command line:
issue terminal commands:
```

linux (hd4,msdos5)/vmlinuz root=UUID=98fac20e-d5a1-4533-bf4f-53c2760240d4 ro
initrd (hd4,msdos5)/initrd.img
boot

```
You will not be able to copy and paste, so do these commands s l o w l y and carefully  -> letter, space function perfect as given. Triple check prior to hitting that enter key. The system is dumb and will only do as told and will not protect you from an error .

what results ? Do you boot to the operating system? does grub scream and holler ? If there is other than a retun to prompt when the commands are entered, what does grub say ?

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-12
Ok, I threw those into the grub console, and I'm here with the results.

```
linux (hd4,msdos5)/vmlinuz root=UUID=98fac20e-d5a1-4533-bf4f-53c2760240d4 ro
```
This gave me an error that stated ```
hd4 cannot get C/H/S values
```
Not sure what it means, but I'll move on anyway.
```
initrd (hd4,msdos5)/initrd.img
```
This restarted the computer, or at least it appeared to (the BIOS ran through its circuit again), and to my surprise it
ended up at the grub menu, instead of the grub rescue terminal.

```
boot
```
This simply told me that I needed to load (a/the?) kernal first.

---

### Post by Bashing-om on 2015-03-12
jland98; Try try again.
> 
instead of the grub rescue terminal.
This simply told me that I needed to load (a/the?) kernal first.

Let's tell grub where it's files are, and grub where the kernel is:
from the grub rescue > prompt:
```

set prefix=(hd4,msdos5)/boot/grub
set root=(hd4,msdos5)
insmod linux
linux (hd4,msdos5)/vmlinuz root=/dev/sda5 ro
initrd (hd4,msdos5)/initrd.img
boot

```

Now do you boot, else what does grub scream and holler about ? 
If it screams and hollers, may have to go look and see if the files do exist .

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to boot a system like you 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-13
Alright, I'm back, but not much more to show.
The first 2 commands went through without any fuss or output to the terminal
The third one recieved the output

"error: hd4 cannot get C/H/S values"

The other three weren't able to be run, since I wasn't in the right terminal, and
all I got in return was unknown command.

---

### Post by Bashing-om on 2015-03-13
jland98; hummmm ..

At the most basic level it means that your Hard Drive cannot find (C)ylinder, (H)ead and (S)ector information.

Bios battery dying ? check: is the time clock in bios correct for date and time ?

Might be a good idea to run a file system check and see what results:
From the liveDVD - so the file system in not in use ! - booted to terminal:
```

sudo fdisk -lu ##verify that the hard drive is still seen as 'sdd' ##
sudo e2fsck -C0 -p -f -v /dev/sdd5

```
if errors: -y auto answers yes for fixes needing response see man e2fsck
in the event of error now run:
```

sudo e2fsck -f -y -v /dev/sdd5

```

[INDENT][INDENT]presently, not look'n good for the home team
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-13
Would the liveDVD be the disk I burned ubuntu to?
And do I load it from the Grub terminal?

---

### Post by Bashing-om on 2015-03-13
jland98; OH ;

Sorry, I sometime forget to relay the basics.
Yes, the liveDVD is the install medium you used. (desktop that is).

Set in bios to boot the DVD -> boot screen -> choose "try ubuntu"
Will take some time to decompress and load into ram .. give it some time .
Will arrive at the GUI desktop
Here at the desktop key combo ctl+alt+t will yield a terminal.

I honestly do not anticipate the problem to be here, - looks to be lower level - but just to make sure let's do the file system check.
very important to observe the output of 'fdisk' and point 'e2fsck' to the correct partition that 'linux' is installed to.
Perhaps (RE-)installing grub will resolve the C/H/S discontinuity ? Maybe check and make sure that the /etc/fstab - File System TABle - is correct for the partition info ?

I continue to think about this, and ponder what causes this error message.

[INDENT][INDENT]small step, little pokes 
[INDENT][INDENT][INDENT]see what we can learn
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-14
Thanks for helping out so far, I'm gonna try and boot it through the DVD now. As far as reinstall grub goes,
it seemed to be packaged with Ubuntu, I didn't install it separately.

In /etc there is a folder named fstab.d, I found nothing inside it. There was a text file named fstab, but I'm not
quite sure what it is saying.

Well I'll get back to you when I check the DVD.

---

### Post by DaftGiraffe on 2015-03-14
Ok, here we go. I looed though the output of the fdisk command, and Linux is said to be mounted to sdd5, and "Linux swap / Solaris" is mounted to sdd6.
I tried the e2fsck on both of these (not sure what to call them, partitions maybe?), and both times it returned

/dev/sddx is already mounted
e2fsck: Cannot continue, aborting

Where 'x' stands for 5 and 6.

There weren't any error message that needed a reply, it simply brought me back to the standard command line.

---

### Post by Bashing-om on 2015-03-14
jland98'; uoohhh,, easy there.

small steps, I say again that one can not run a file system check while the file system is in-use (mounted). So what one does is do the file system check from that liveDVD.
Boot the lieDVD to a terminal :
execute terminal commands:
```

sudo e2fsck -C0 -p -f -v /dev/sdd5

```
If there are errors reported by the above, then the following with the  -y auto answers yes for fixes needing response - see man e2fsck;
run this one:
```

sudo e2fsck -f -y -v /dev/sdd5

```
Reason for the re-do from this strange output :
> 
/dev/sddx is already mounted
e2fsck: Cannot continue, aborting

That :
a) you are running the command from the install
b) Windows - for some reason - has a lock on that partition ?????
c) the external hard drive is not connected when the command is ran, and sdd is interpreted as a different device (fdisk -lu)??? 
If ya want I double check the results; post them - Between Code Tags - ( preserves formatting, and promotes readability)
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

One can  not run a file system check on the 'swap' partition. That partition does not have any file system imposed on it.

I do not expect there to be a problem, just checking before proceeding  to look at the 'fstab' file.

Be aware I also can see where this issue might be a Window boot loader situation.
All we know presently is grub is not happy with /C/H/S which could be a number of reasons.

all in all
[INDENT][INDENT]an adventure in learning
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-14
I made sure that I booted through the disc this time, hit 'Try Ubuntu', loaded up the terminal, and put in:

```
sudo e2fsck -C0 -p -f -v /dev/sdd5
```

This is what I get why these are pasted into the terminal.

```
/dev/sdd5 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:~$ 

```

What would it mean if windows was keeping a lock on the partitions? It's loaded from the try ubuntu option.
And the hard drive is connected fine, so it seems that is the only possibility.

---

### Post by Bashing-om on 2015-03-15
jland98; WOW !

I truly do not know, however, let's see what we can find out:
boot the liveDVD to terminal:
What returns:
Verify again that we are looking at the 1 Tb external drive that is seen as 'sdd'
```

fdisk -lu

```
as in:
> 
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes

Now let's see if we can see what has a lock on that device:
```

mount
cat /etc/mtab
cat /proc/mounts

```
see if we can see the mount point(s) and get some idea of the why and where.


[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-15
"fdisk -lu" didn't give a response in the terminal, but when I added "sudo" before it, it gave me this:

```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x498cd6a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28674047    14336000   27  Hidden NTFS WinRE
/dev/sda2   *    28674048    28878847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28878848  1465147119   718134136    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003929c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   721199797   360599867+   7  HPFS/NTFS/exFAT
/dev/sdd2       721201150  1953523711   616161281    5  Extended
/dev/sdd5       721201152  1945139199   611969024   83  Linux
/dev/sdd6      1945141248  1953523711     4191232   82  Linux swap / Solaris

Disk /dev/sde: 16.0 GB, 16018046976 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              48    31285247    15642600    c  W95 FAT32 (LBA)


```

From what I can tell here, linux is under sdd5 (and sdd6?), which means it is part of the sdd external hard drive (1000gb).
The next three commands threw a bunch at me, which I can't decipher, so here it is.

Mount
```
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdd5 on /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sde1 on /media/ubuntu/Lexar type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdd1 on /media/ubuntu/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


```

cat /etc/mtab
```
/cow / overlayfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/999/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=ubuntu 0 0
/dev/sdd5 /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4 ext4 rw,nosuid,nodev,uhelper=udisks2 0 0
/dev/sde1 /media/ubuntu/Lexar vfat rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2 0 0
/dev/sdd1 /media/ubuntu/Expansion\040Drive fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0


```

cat /proc/mounts
```
rootfs / rootfs rw,size=1979092k,nr_inodes=494773 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1979108k,nr_inodes=494777,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=404716k,mode=755 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
/cow / overlayfs rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow 0 0
none /sys/fs/cgroup tmpfs rw,relatime,size=4k,mode=755 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /run/user tmpfs rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755 0 0
none /sys/fs/pstore pstore rw,relatime 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,name=systemd 0 0
gvfsd-fuse /run/user/999/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
/dev/sdd5 /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4 ext4 rw,nosuid,nodev,relatime,data=ordered 0 0
/dev/sde1 /media/ubuntu/Lexar vfat rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0
/dev/sdd1 /media/ubuntu/Expansion\040Drive fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0


```

Hopefully this will turn up with something.

---

### Post by Bashing-om on 2015-03-15
jland98; Welp !

Device sdd5 is mounted ! From where. not a clue . maybe you are activating it from the file manager by attempting to access the files ?
But it sure looks like ubuntu has that partition mounted.
3 ways we can UNmount the partition.
1) in the file manager right click and select "umont' or maybe as eject, or maybe listed as 'safely remove'
2) in GParted right click on the partition is the 'work' pane and select 'umount'
3) in terminal issue terminal command:
```

sudo umount /dev/sdd5

```
Now run the mount command, 
```

mount

```
and insure that
> 
/dev/sdd5 on /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4 type ext4 (rw,nosuid,nodev,uhelper=udisks2)

no entry exists for 'sdd5' .

-----------------------------
swap:
> 
From what I can tell here, linux is under sdd5 (and sdd6?), which means it is part of the sdd external hard drive (1000gb).

Device sdd6 is the swap partition for ubuntu.  Swap is additional space for ram to aid in the event that the system runs short of ram, it "pages" stuff of of ram to that swap space. It has no file system thus can not be checked .. it is just space. And yes it is a part of that 1000gb. it does take up space and is a dedicated partition to that purpose. BUT, it is of no direct concern to us at this time.

------------------------
we sure do need to know the why that :
> 
/dev/sdd5 on /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sde1 on /media/ubuntu/Lexar type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdd1 on /media/ubuntu/Expansion Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

these devices get mounted ... from where ?
The file manager ?

[INDENT][INDENT]what is going on here with partitions mounted in the liveDVD environment 
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-15
I didn't try to unmount it from the file manager, since I'm not 100% where to find it, unless its simply the expansion drive.

Gpart was unable to unmount it, saying:

"The partition could not be unmounted from the following mount points:
/
Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."

And in the terminal when I tried it unmount it, it said:

```
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

I think it was probably mounted when I was trying to access the files. I figured that to change settings for things it would be in the expansion drive,
rather than somewhere through the home folder or something.

---

### Post by Bashing-om on 2015-03-15
jland98; Hey !

Just looking for a cause of why 'sdd5' is in use ... and from where .. Very very unusual.
I too am now in a learning process and sorta groping my way through this darkness.

Let's try this to find out why the device is busy:
LiveDVD -> terminal command:
```

fuser -m /dev/sdd5

```
In this instance I do not know what all to expect in that return.. 
We should get back a PID(s) and then we investigate the PID, see what then we can find.
Related is why 'sdd1' and 'sde1' are also mounted, why and from where ???

I am still leaning in the direction that Windows has that lock on it ,, but I am no longer Windows literate - not touched Windows in years - and do not recall how to look and see from Windows, or how to release it if Windows does have that lock . Any one else with knowledge to guide and assist here ?

I can readily accept that this is the cause of the " hd4 cannot get C/H/S values " issue.


[INDENT][INDENT]nother step up
[INDENT][INDENT][INDENT]the curve of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-17
Ok, I may be able to answer some questions, but the fuser command returned no PIDs, it returned nothing at all.
I tried it with sudo as well, incase it just was hiding any output, no good.

The sde device is a 16gb flashdrive plugged in, I'm not sure what sde1 would represent, but I'm guessing its just
the current or total file storage on it.

sdd1 says it is mounted to HPFS/NTFS/exFAT. I tried googling this to find out what it might be. Other than some
kind of partition, I couldn't find anything I understood.

---

### Post by Bashing-om on 2015-03-17
jland98; Hummm ...

Totally mystified as to what is taking place that those devices appear as mounted and in use. WHY ?? from where ?

All I can hazard to guess is that you are booting from that external hard dive, rather then the liveDVD(USB) - That original medium you used to install ubuntu with.

Please clarify my thought process that you are in deed booting your computer from else than 'sdd' when looking at what is mounted.
We want nothing other than a liveDVD mounted and in use .
When  we have nothing else than a liveDVD OR a liveUSB mounted, then we can run file system checks, and try and see what problems exist.

Get a firm foundation
[INDENT][INDENT]then we look around
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-17
Ok, when I startup my computer, it first loads the bios, with two keys that I can press. Delete for bios options, f12 for boot menu.
I hit the boot menu and select the dvd option. It takes some time, but eventually loads up a menu with language options on the right, and
two buttons. "Try Ubuntu" and "Install Ubuntu". I've been hitting the former.

My only idea to what else is partitioned on the device is that the external harddrive sdd has backups for a few of our desktops/laptops.
When selecting how much data to partition off to ubuntu I selected about 750 ram, which was right near the amount that was open.

---

### Post by Bashing-om on 2015-03-17
jland98; Sheessshh ....

Yeah, with that "try ubuntu" option that has to be the liveDVD.

Here's the thinking:
the terminal command:
```

mount

```
relates that 'sdd5' , 'sdd1' and 'sde1' are mounted, and at least 'sdd5' is in use.

"fuser-m" does not return the PID of what is holding the file system.
So, let's take a different tact;
Let's venture into the hairy world of 'lsof' - list open files - see what it can tell us:
from that liveDVD, what returns:
```

lsof /dev/sdd5

```
In this struggle to comprehend, and remove that lock !

[INDENT][INDENT]still, just do not know
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-18
Although it doesn't seem to work as intended, the lsof command at least produced a result.

```
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.


```

When preceeded by sudo, it produced:

```
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/999/gvfs
      Output information may be incomplete.


```

I'm really not sure what mess we've gotten into.

---

### Post by Bashing-om on 2015-03-18
DaftGiraffe; Welp;

As is, I hate to say it, but I have no idea what is taking place.
Can you boot Windows, and from Windows see what Windows relates as to the state of the file system(S) ?

I do air my ignorance, in the hopes that others can advise.

[INDENT][INDENT]What to Do, OH, what to do
[/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-19
I'm not too sure how to do that, but I'll look around if need be.

For now I'm gonna try the steps in this thread and see if it can get me anywhere.
If nothing, it was probably worth trying.
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

---

### Post by DaftGiraffe on 2015-03-19
Ok, it seemed to work fine until it was restarted, and it came upon the grub rescue error again.
I did notice that when reinstalling grub, it installed the i386 version, which I believe is the 
32-bit version, and my computer is running on 64-bit ubuntu.

Ok, I'm just gonna try something new and reinstall ubuntu completely. Maybe that will solve something.

---

### Post by Bashing-om on 2015-03-19
DaftGiraffe; Hey;


To this time have you (RE-)installed ubuntu ?
Are we still working to find a fix ?
A (RE-)install of grub is what we are working toward. IF you used the existing mount point and KNOW which partition contains grub's boot files (sdd5.) Certainly worth a try .
a) partition sdd5
b) UUID of sdd5 : 98fac20e-d5a1-4533-bf4f-53c2760240d4
                            98fac20e-d5a1-4533-bf4f-53c2760240d4
                 UUID=98fac20e-d5a1-4533-bf4f-53c2760240d4
c) mountpoint - currently- of sdd5 : /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4

And It still blows me away where 'sdd5', 'sdd1' and 'sde1' are being mounted from ! There should be no reason that they are mounted booting the liveDVD. Therefore "something" has a lock on these device filesystems.

One cause could be that the file systems were open in Windows, and When terminating the Windows' session you hibernated rather than a complete shutdown. I say again ... look in Windows and see if you can find the cause. I am not Windows literate and thus can not advise the method to check from Windows.

Think'n; From ubuntu's liveDVD what results:
```

ls -al /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4

```
If that returns a meaningful output; 
```

sudo umount /media/ubuntu/98fac20e-d5a1-4533-bf4f-53c2760240d4

```
see if we can release that lock from the liveDVD .. doubtful, but worth a try and maybe get some additional info.

learn the cause
[INDENT][INDENT][INDENT]we fix the problem
[/INDENT][/INDENT][/INDENT]

---

### Post by DaftGiraffe on 2015-03-31
Sorry for the late reply. I haven't reinstalled it yet.
Since I believe it is having trouble with the partitions on the hard drive,
I am going to get a new one and see what I can do from there. I should
be able to get one in roughly half a week.

I was able to uninstall ubuntu and grub sucessfully though a windows
installation disk, so my computer starts as it had before I started
dual-booting.

---

### Post by Bashing-om on 2015-03-31
DaftGiraffe; Welp;

There is always that nuclear solution.
But to be real honest, I still look at this as a software/config issue.

Let us know how it goes - won't take but a few minutes to (RE-)install ubuntu and I bet have a stable system .

[INDENT][INDENT]what I think
[INDENT][INDENT]for what that is worth
[/INDENT][/INDENT][/INDENT][/INDENT]

---

