---
title: "Boot stops at grub prompt?"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by matt! on 2010-07-05
Hi,

I am running 10.04 which I got to by upgrading 9.10 using the system update funciton. 9.10 was installed using wubi within windows.

today, i installed the latest updates that ubuntu prompted me with. now, the machine does not boot properly. i choose ubuntu at the boot chooser, then it sits at a grub prompt. (i can still boot into windows fine)

i have updated my wubildr file to the version that is mentioned in a lot of posts. no change

i have booted from a 10.04 live cd and ran the boot info script. there seems to be an issue, but i have no idea how to proceed.

any help appreciated.

thanks,
matt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c31a8732-9e97-4842-8e97-653b54f607b9   ext4                                     
/dev/sda1        E4F47978F4794DB4                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=10 
default=C:\wubildr.mbr 
[operating systems] 
C:\wubildr.mbr = "Ubuntu" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 


```

---

### Post by matt! on 2010-07-05
also:
```
ubuntu@ubuntu:~$ dmesg | tail
[  740.206151] EXT4-fs (loop1): INFO: recovery required on readonly filesystem
[  740.206160] EXT4-fs (loop1): write access unavailable, cannot proceed

```

---

### Post by matt! on 2010-07-05
With the help of this thread: [http://www.uluga.ubuntuforums.org/showthread.php?t=1521340](http://www.uluga.ubuntuforums.org/showthread.php?t=1521340)

I can boot the machine. rebooting meets the same problem, so there is some larger fix necessary.

```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```

---

### Post by matt! on 2010-07-05
```
sudo grub-install /dev/sda1
sudo update-grub

```
then rebooting

fixed it.

---

### Post by bcbc on 2010-07-05
> **matt! said:**
> ```
sudo grub-install /dev/sda1
sudo update-grub

```
then rebooting

fixed it.

This seems unlikely. The first command installs grub to the windows partition boot sector which will break windows. Also, 'grub-install' doesn't allow you to do this, unless you force it.

Your first couple of posts indicated that there were errors on the wubi virtual disk file system. Usually you'd need to run an fsck on it to fix it.

---

### Post by matt! on 2010-07-05
Well, I definitely didn't do anything like that myself - the only things that I did are listed in this thread.

Though I did notice during the manual boot that it got past the point it had failed at previously and it said on-screen that some recovery/repair had been done on the disk. But then after that it would still no longer boot. It took the update-grub to get things back and working.

The only difference I can see during the now successful boot procedure is that there's a second kernel choice in the GNU GRUB menu.

Anyway, it works for me and perhaps the information in this thread will be useful to somebody in the future. :)

matt

---

### Post by ajgreeny on 2010-07-05
And can you still boot into windows if you choose to?

---

### Post by matt! on 2010-07-05
Yes, I have just done so to confirm.

---

### Post by bcbc on 2010-07-05
> **matt! said:**
> Yes, I have just done so to confirm.

Then you didn't install grub to /dev/sda1. By the way this is what happens if you try...
```
$ sudo grub-install /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

The only reason I mention it is that by saying that you did xxx and that it solved your problem, you run the risk that someone else tries it. It will break your windows if you force grub to install itself to it. Guaranteed.

Edit: it's a pity that the Lucid Upgrade didn't have the same safeguards - the forums are littered with examples where grub was installed to the windows partition and the resulting problems. There is a fix in progress now to correct this (imo that's closing the stable door after the horse has bolted)... [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by matt! on 2010-07-05
Well, I've just issued the commands for a second time to prove my point and the state of my system remains unchanged - working/booting into Windows and Ubuntu (installed via wubi). Perhaps something you are thinking should have happened has not happened?

To that end, here is the output of my commands:
```
matt@ubuntu:~$ sudo grub-install /dev/sda1
[sudo] password for matt: 
Installation finished. No error reported.
matt@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found Windows NT/2000/XP on /dev/sda1
done
matt@ubuntu:~$
```

---

### Post by bcbc on 2010-07-05
> **matt! said:**
> Well, I've just issued the commands for a second time to prove my point and the state of my system remains unchanged - working/booting into Windows and Ubuntu (installed via wubi). Perhaps something you are thinking should have happened has not happened?

To that end, here is the output of my commands:
```
matt@ubuntu:~$ sudo grub-install /dev/sda1
[sudo] password for matt: 
Installation finished. No error reported.
matt@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found Windows NT/2000/XP on /dev/sda1
done
matt@ubuntu:~$
```
I stand corrected... :redface: 

I feel a learning moment coming on. :)

---

### Post by bcbc on 2010-07-05
From my standard ubuntu install, the command fails as I've shown previously. But from my wubi install it works (at least it doesn't give any error, and as you say, windows still boots correctly.

It doesn't explain why wubi users who upgraded to lucid damaged their windows boot sectors unless a) the upgrade used a different method to install the bootloader or b) the grub-install process has been changed since.

I've just checked windows and it updated the c:\wubildr file. If you recall, with 9.10 you had to manually replace this file to address a bug, so I wonder if this is a recent update to grub to get around this.

---

### Post by matt! on 2010-07-05
I have no idea :)

Glad you're seeing the same thing as I am. 

That'll be all from me unless I have any important information to add.

---

### Post by bcbc on 2010-07-05
> **matt! said:**
> I have no idea :)

Glad you're seeing the same thing as I am. 

That'll be all from me unless I have any important information to add.

OK thanks for the info - as you can see it helps spread the info.

By the way I tracked down the change in package lupin-support that explains the 'new behaviour'. Unfortunately the fix wasn't 'passed along' either verbally or in an update, as wubi installs are still failing for the old wubildr bug. 

> lupin (0.26) karmic; urgency=low

  * Divert grub-install and replace it with a wrapper that upgrades wubildr
    if running in a loop-mounted installation (LP: #460192).

 -- Colin Watson <cjwatson@ubuntu.com>  Mon, 26 Oct 2009 11:46:07 +0000


---

