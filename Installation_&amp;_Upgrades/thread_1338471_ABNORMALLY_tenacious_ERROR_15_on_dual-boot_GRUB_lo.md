---
title: "ABNORMALLY tenacious ERROR 15 on dual-boot GRUB loader after power outage -- HELP!"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Max Nomad on 2009-11-26
Hello all,

Simple summary of the problem – I've been using a dual-boot Ubuntu-XP machine for a good while then the GRUB got corrupted after a brief power outage (and I didn't have a backup of the MBR or lst). The Windows side still loads fine – I'm trying to regain access to the Linux partition. 

Details:

About a year ago I installed Ubuntu 8.x and eventually updated it to 8.10 or 9.04 as a dual boot on a Dell box along with Windows XP. I thought I'd installed Linux on it's own partition but I recall choosing some option that looked like it merged things and made the Windows partition directly accessible through the /media folder (after booted up properly). Anyway, all seemed to be humming along well for many months until this past Monday morning when there was a brief power outage and this Linux box was still up at the time. After the power came back and I went to boot it up again it was giving me an Error 15: File Not Found. Eventually I tried several of the GRUB revival processes and also got Error 17 errors. That's when I noticed that the GRUB loader was GRUB4DOS which made me wonder if I had inadvertently done the “install Ubuntu inside of Windows” option that's available with Ubuntu 9.04 and up. 

Aside from variations of the typical grub fix commands:

grub
> root (hd0,1)
> setup (hd0)
> exit

I've also tried the latest SuperGrubDisk ad GrubRescueDisk – no luck so far and all result in either Error 15, Error 17, or even Error 6.

I've run both CHKDSK and Gparted to see if maybe there were some bad blocks that needed to be found and marked. CHKDSK took awhile on several tries but none have turned up anything significant. 

I've also tried seeing if I could possibly re-install Ubuntu without overwriting the /home folder and settings – no luck. Matter of fact, whether I tried the install from within the LiveCD or loaded it up through the Windows Autorun I'd eventually get an error just after I chose to have it make a Linux installation beside the last one. 

Bottom line – I can't boot into Linux but the Windows side loads just fine. Most of the important stuff I've already got backed up across several machines, to folders on the Windows side of the partition, and on thumb drives. The thing is, I can't risk losing that Windows partition, hence the long and tedious battle instead of just a full-on reinstall. 

After having read so many of these pleas for help, I'd learned enough to include some basic info to start so here it is:

Here's the output from Fdisk -lu

```
 
Disk /dev/sda: 160.0 GB, 160000000000 bytes

255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x41ab2316



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1              63       64259       32098+  de  Dell Utility

/dev/sda2   *       64260   312480314   156208027+   7  HPFS/NTFS



```

Here's the output from bootscript:

```

============================= Boot Info Summary: ======================



 => Syslinux is installed in the MBR of /dev/sda



sda1: _________________________________________________________________________



    File system:       vfat

    Boot sector type:  Dell Utility: Fat16

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   



sda2: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows XP

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows XP

    Boot files/dirs:   /menu.lst /ubuntu/winboot/menu.lst /boot.ini /ntldr 

                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr



=========================== Drive/Partition Info: ===========================



Drive: sda ___________________ _____________________________________________________



Disk /dev/sda: 160.0 GB, 160000000000 bytes

255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x41ab2316



Partition  Boot         Start           End          Size  Id System



/dev/sda1                  63        64,259        64,197  de Dell Utility

/dev/sda2    *         64,260   312,480,314   312,416,055   7 HPFS/NTFS





blkid -c /dev/null: ____________________________________________________________



/dev/loop0: TYPE="squashfs" 

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0C0C" TYPE="vfat" 

/dev/sda2: UUID="942CA1BE2CA19C2C" TYPE="ntfs" 



=============================== "mount" output: ======================



aufs on / type aufs (rw)

none on /proc type proc (rw,noexec,nosuid,nodev)

none on /sys type sysfs (rw,noexec,nosuid,nodev)

udev on /dev type tmpfs (rw,mode=0755)

/dev/sr0 on /cdrom type iso9660 (rw)

/dev/loop0 on /rofs type squashfs (rw)

none on /sys/fs/fuse/connections type fusectl (rw)

none on /sys/kernel/debug type debugfs (rw)

none on /sys/kernel/security type securityfs (rw)

none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)

none on /dev/shm type tmpfs (rw,nosuid,nodev)

tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

none on /var/run type tmpfs (rw,nosuid,mode=0755)

none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)

none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

/dev/sda2 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)





================================ sda2/menu.lst: =========================



debug off

hiddenmenu

default 0

timeout 0

fallback 1



title find /ubuntu/disks/boot/grub/menu.lst

	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst

	configfile /ubuntu/disks/boot/grub/menu.lst



title find /ubuntu/install/boot/grub/menu.lst

	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

	configfile /ubuntu/install/boot/grub/menu.lst



title find /menu.lst

	find --set-root --ignore-floppies /menu.lst

	configfile /menu.lst



title find /boot/grub/menu.lst

	fallback 2

	find --set-root --ignore-floppies /boot/grub/menu.lst

	configfile /boot/grub/menu.lst



title find /grub/menu.lst

	fallback 3

	find --set-root --ignore-floppies /grub/menu.lst

	configfile /grub/menu.lst



title commandline

	commandline



title reboot

	reboot



title halt

	halt



======================== sda2/ubuntu/winboot/menu.lst: ====================



debug off

hiddenmenu

default 0

timeout 0

fallback 1



title find /ubuntu/disks/boot/grub/menu.lst

	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst

	configfile /ubuntu/disks/boot/grub/menu.lst



title find /ubuntu/install/boot/grub/menu.lst

	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

	configfile /ubuntu/install/boot/grub/menu.lst



title find /menu.lst

	find --set-root --ignore-floppies /menu.lst

	configfile /menu.lst



title find /boot/grub/menu.lst

	fallback 2

	find --set-root --ignore-floppies /boot/grub/menu.lst

	configfile /boot/grub/menu.lst



title find /grub/menu.lst

	fallback 3

	find --set-root --ignore-floppies /grub/menu.lst

	configfile /grub/menu.lst



title commandline

	commandline



title reboot

	reboot



title halt

	halt



================================ sda2/boot.ini:=========================



[boot loader]

timeout=40

default=c:\wubildr.mbr

[operating systems]

c:\wubildr.mbr="Ubuntu"

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect



=================== sda2: Location of files loaded by Grub: ===================





    .0GB: boot/grub/stage2

    .0GB: grub/stage2

    .0GB: menu.lst

```

Any and all help would be appreciated.  Thanks in advance!

---

### Post by Max Nomad on 2009-11-27
If it helps shed any light on the problem, while using Parted Grub4DOS I was able to learn that /dev/sda2 is FUSEBLK which explains the HDFS/NTFS that may have come up in the reports I pasted in the previous message.

---

### Post by oldfred on 2009-11-27
No you have a Wubi install and have to have the windows boot loader in the MBR. Your system boots windows and then you choose whether to start windows or the wubi install of Ubuntu.

You need to make sure you have correctly reinstalled the windows boot loader. I am not familiar with Wubi so I am not sure how to repair that.
If you have found that you like Ubuntu you may want to consider a true dual boot with Ubuntu installed in its own partition.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

