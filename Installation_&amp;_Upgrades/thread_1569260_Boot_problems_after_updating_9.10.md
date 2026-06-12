---
title: "Boot problems after updating 9.10"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by jimbr on 2010-09-06
I had a working Win7/9.10 system with Ubuntu installed under Wubi. A few days ago I ran the Updater and all appeared to go well but at the end the restart failed with error message of a long string of characters and the prompt "Grub rescue". Research indicated that Win 7 Recovery Disk would work - downloaded it and could not get it to boot - more reading and found boot repair software that did work ok for Windows. However when I select Ubuntu to boot the system dithers a bit and reverts to a restart.

Reading on the forum indicates the need to get disk info in order to receive help - here is the result on my system:

NB Ubuntu is in a the Ubuntu folder on sda3 and sdb is the USB Memstick that I have booted from.

Thanks in advance, Jim


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 298464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 298464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 298464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,147,775     3,145,728  12 Compaq diagnostics
/dev/sda2           3,147,776   244,320,255   241,172,480   7 HPFS/NTFS
/dev/sda3         244,320,256   467,421,183   223,100,928   7 HPFS/NTFS
/dev/sda4         467,421,184   488,394,751    20,973,568  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,687,679    15,679,616   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1f06deb5-d91b-494f-9667-ccb562c99335   ext4                                     
/dev/sda1        98FAD0B4FAD08FBC                       ntfs       RECOVERY                      
/dev/sda2        4AB2D34CB2D33AE1                       ntfs                                     
/dev/sda3        2C962C11962BD9DA                       ntfs                                     
/dev/sda4        507A2F3E7A2F1FE8                       ntfs       LG_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5568-7049                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by bcbc on 2010-09-06
Looks like you installed grub2 to every partition. That's an old 10.04 upgrade issue (user unfriendly). But good that you got win7 booting again.

In terms of why Ubuntu is not working... not sure. Bootinfoscript says that the root.disk isn't in good shape. You could try mounting it, or running fsck on it. (Before you do it's a good idea to back it up (\ubuntu\disks\root.disk)).

So from a live CD, you can mount the windows partition, then try mounting the root.disk. If that fails, run fsck on it (don't run fsck while it's mounted):
```
sudo mkdir -p /media/win
sudo mount /dev/sda3 /media/win

Then Either:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
Or:
sudo fsck /media/win/ubuntu/disks/root.disk

```

Hopefully that will get it booting again, otherwise, this may turn into a recovery mission. 
PS if you have a backup of root.disk from before the upgrade you can probably revert to it as well.

---

### Post by jimbr on 2010-09-07
Thanks for the reply and your suggestions - apologies for the slow response but I am juggling time with another project - followed your instructions but no change in the response to I select Ubuntu from the boot menu. I do not have the backup file you suggested.

I am very new to Ubuntu so would really appreciate any further suggestions. Thanks JB

---

### Post by bcbc on 2010-09-07
> **jimbr said:**
> Thanks for the reply and your suggestions - apologies for the slow response but I am juggling time with another project - followed your instructions but no change in the response to I select Ubuntu from the boot menu. I do not have the backup file you suggested.

I am very new to Ubuntu so would really appreciate any further suggestions. Thanks JB

What happened when you tried mounting or running fsck? you can cut and paste the output if it helps

---

### Post by jimbr on 2010-09-07
No obvious reaction from os!

ubuntu@ubuntu:~$ sudo mkdir -p /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/win
ubuntu@ubuntu:~$ sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
ubuntu@ubuntu:~$

---

### Post by bcbc on 2010-09-07
Make sure everything is still there:
```
nautilus /mnt 
```
look in /mnt/home/<user> to make sure your data is ok.

---

### Post by bcbc on 2010-09-07
Let's try chroot'ing into the wubi install and running update-grub. That seems to resolve wubi booting problems sometimes.

so, keep the root.disk mounted on /mnt as before:

run the following:
```
for i in dev proc sys dev/pts ; do sudo mount --bind /$i /mnt/$i; done
sudo chroot /mnt
update-grub
exit
for i in dev/pts dev proc sys; do sudo umount /mnt/$i; done
```

Unmount /mnt and /media/win and try and reboot into the wubi.
```
sudo umount /mnt
sudo umount /media/win
```

---

### Post by jimbr on 2010-09-07
This is what happened when I ran your code:

ubuntu@ubuntu:~$ for i in dev proc sys dev/pts ; do sudo mount --bind /$i /mnt/$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot stat `/media/win/ubuntu/disks/root.disk'.
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in host dev/pts dev proc sys; do sudo umount /mnt/$i; done
umount: /mnt/host: not mounted
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo umount /media/win
ubuntu@ubuntu:~$ 

Will try a reboot now and let you know

---

### Post by bcbc on 2010-09-07
> **jimbr said:**
> This is what happened when I ran your code:

ubuntu@ubuntu:~$ for i in dev proc sys dev/pts ; do sudo mount --bind /$i /mnt/$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot stat `/media/win/ubuntu/disks/root.disk'.
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in host dev/pts dev proc sys; do sudo umount /mnt/$i; done
umount: /mnt/host: not mounted
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo umount /media/win
ubuntu@ubuntu:~$ 

Will try a reboot now and let you know
Ok sorry I left an extra 'host' in that - will edit my post above. I am a bit concerned about the update-grub response. It didn't look like it generated anything. Which isn't a good sign. The grub-probe error seems to be happening lately with wubi, so I am not concerned about that, but it's the lack of any other messages that's worrying.

I'm also not going to be online much longer. But let me know what the response is and I'll give you one last thing to try.

PS: if it does fail, run the bootinfoscript again, so at least I can take a look at the contents of the root.disk grub.cfg and fstab etc.

---

### Post by jimbr on 2010-09-07
Must also go off line v soon - no change with reboot - still boots windows ok but ubuntu selection spends a bit of time doing something and then returns to the boot menu. Thanks for help so far - talk again soon. egards, JB

---

### Post by bcbc on 2010-09-07
So when you run 'update-grub' it runs some scripts in the /etc/grub.d/ directory. For wubi, the 10_lupin is important. e.g.
```
$ ls -l /mnt/etc/grub.d/
total 56
-rwxr-xr-x 1 root root 6423 2010-08-25 15:29 00_header
-rwxr-xr-x 1 root root 1481 2010-08-25 15:08 05_debian_theme
-rwxr-xr-x 1 root root 4757 2010-08-25 15:29 10_linux
**-rwxr-xr-x** 1 root root 4078 2010-03-23 02:14 **10_lupin**
-rwxr-xr-x 1 root root 4893 2010-08-25 15:29 20_linux_xen
-rwxr-xr-x 1 root root 1570 2010-07-05 01:38 20_memtest86+
-rwxr-xr-x 1 root root 6933 2010-08-25 15:29 30_os-prober
-rwxr-xr-x 1 root root  214 2010-07-01 13:53 40_custom
-rwxr-xr-x 1 root root   95 2010-08-25 15:29 41_custom
-rw-r--r-- 1 root root  483 2010-07-01 13:53 README
```

The file must exist and be executable.Then it will find the kernel(s) you have in the /boot directory. e.g.
```
$ ls -l /mnt/boot/
total 33756
-rw-r--r-- 1 root root   651618 2010-08-20 11:22 abi-2.6.32-24-generic
-rw-r--r-- 1 root root   115905 2010-08-20 11:22 config-2.6.32-24-generic
drwxr-xr-x 3 root root     4096 2010-09-06 22:16 grub
-rw-r--r-- 1 root root  9978191 2010-09-01 21:02 **initrd.img-2.6.32-24-generic**
-rw-r--r-- 1 root root   165084 2010-07-05 01:38 memtest86+.bin
-rw-r--r-- 1 root root   167264 2010-07-05 01:38 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  1689036 2010-08-20 11:22 System.map-2.6.32-24-generic
-rw-r--r-- 1 root root     1196 2010-08-20 11:24 vmcoreinfo-2.6.32-24-generic
-rw-r--r-- 1 root root  4034976 2010-08-20 11:22 **vmlinuz-2.6.32-24-generic**

```

When you ran update-grub it didn't report finding the kernels, so either the scripts aren't there (or aren't executable) or the kernels aren't there. Or possibly, some other problem. So let's figure out what state that is in. The bootinfoscript should report on what the grub.cfg looks like and the kernels. And that might indicate what the next step should be to try and resolve this.

---

### Post by jimbr on 2010-09-08
looks like you are correct - missing or not executable:

ubuntu@ubuntu:~$ ls -l /mnt/etc/grub.d/
ls: cannot access /mnt/etc/grub.d/: No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/boot/
ls: cannot access /mnt/boot/: No such file or directory
ubuntu@ubuntu:~$

---

### Post by bcbc on 2010-09-08
> **jimbr said:**
> looks like you are correct - missing or not executable:

ubuntu@ubuntu:~$ ls -l /mnt/etc/grub.d/
ls: cannot access /mnt/etc/grub.d/: No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/boot/
ls: cannot access /mnt/boot/: No such file or directory
ubuntu@ubuntu:~$

Just to be clear - you loop mounted your root.disk again under /mnt, right? Sorry if the question offends, but it pays to be certain ;) (because you will get this same error if you haven't done that as well).

---

### Post by jimbr on 2010-09-08
Hi again - no offense taken - I am really raw when it comes to Ubuntu - to the extent that I am not sure what you mean by loop mounting! This is what I have just tried:

ubuntu@ubuntu:~$ for i in dev proc sys dev/pts ; do sudo mount --bind /$i /mnt/$i; done
mount: mount point /mnt/dev does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/sys does not exist
mount: mount point /mnt/dev/pts does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/etc/grub.d/
ls: cannot access /mnt/etc/grub.d/: No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/boot/
ls: cannot access /mnt/boot/: No such file or directory

Doesn't seem to have helped

---

### Post by bcbc on 2010-09-08
> **jimbr said:**
> Hi again - no offense taken - I am really raw when it comes to Ubuntu - to the extent that I am not sure what you mean by loop mounting! This is what I have just tried:

ubuntu@ubuntu:~$ for i in dev proc sys dev/pts ; do sudo mount --bind /$i /mnt/$i; done
mount: mount point /mnt/dev does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/sys does not exist
mount: mount point /mnt/dev/pts does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/etc/grub.d/
ls: cannot access /mnt/etc/grub.d/: No such file or directory
ubuntu@ubuntu:~$ ls -l /mnt/boot/
ls: cannot access /mnt/boot/: No such file or directory

Doesn't seem to have helped

Try
```
sudo mkdir -p /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
ls -l /mnt/etc/grub.d
ls -l /mnt/boot
```
Post the results of the last two commands. No need to chroot at this time

---

### Post by jimbr on 2010-09-08
This looks a bit more useful:

ubuntu@ubuntu:~$ ls -l /mnt/etc/grub.d
total 44
-rwxr-xr-x 1 root root 4444 2010-04-29 07:08 00_header
-rwxr-xr-x 1 root root 1416 2010-04-29 06:45 05_debian_theme
-rwxr-xr-x 1 root root 4594 2010-04-29 07:08 10_linux
-rwxr-xr-x 1 root root 4078 2010-06-17 23:30 10_lupin
-rwxr-xr-x 1 root root  918 2010-03-23 09:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2010-04-29 07:08 30_os-prober
-rwxr-xr-x 1 root root  214 2009-10-24 00:44 40_custom
-rw-r--r-- 1 root root  483 2009-10-24 00:44 README
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 42676
-rw-r--r-- 1 root root  629853 2010-05-27 04:21 abi-2.6.31-22-generic
-rw-r--r-- 1 root root  640617 2010-06-04 01:56 abi-2.6.32-22-generic
-rw-r--r-- 1 root root  651618 2010-08-20 18:22 abi-2.6.32-24-generic
-rw-r--r-- 1 root root  111349 2010-05-27 04:21 config-2.6.31-22-generic
-rw-r--r-- 1 root root  115847 2010-06-04 01:56 config-2.6.32-22-generic
-rw-r--r-- 1 root root  115905 2010-08-20 18:22 config-2.6.32-24-generic
drwxr-xr-x 3 root root    4096 2010-09-07 18:56 grub
-rw-r--r-- 1 root root 7661698 2010-06-18 00:06 initrd.img-2.6.31-22-generic
-rw-r--r-- 1 root root 8271709 2010-06-18 06:42 initrd.img-2.6.32-22-generic
-rw-r--r-- 1 root root 8275569 2010-09-03 18:03 initrd.img-2.6.32-24-generic
-rw-r--r-- 1 root root  160280 2010-03-23 09:37 memtest86+.bin
-rw-r--r-- 1 root root 1668340 2010-05-27 04:21 System.map-2.6.31-22-generic
-rw-r--r-- 1 root root 1687378 2010-06-04 01:56 System.map-2.6.32-22-generic
-rw-r--r-- 1 root root 1689036 2010-08-20 18:22 System.map-2.6.32-24-generic
-rw-r--r-- 1 root root    1196 2010-05-27 04:23 vmcoreinfo-2.6.31-22-generic
-rw-r--r-- 1 root root    1196 2010-06-04 01:58 vmcoreinfo-2.6.32-22-generic
-rw-r--r-- 1 root root    1196 2010-08-20 18:24 vmcoreinfo-2.6.32-24-generic
-rw-r--r-- 1 root root 3900960 2010-05-27 04:21 vmlinuz-2.6.31-22-generic
-rw-r--r-- 1 root root 4030048 2010-06-04 01:56 vmlinuz-2.6.32-22-generic
-rw-r--r-- 1 root root 4034976 2010-08-20 18:22 vmlinuz-2.6.32-24-generic

---

### Post by bcbc on 2010-09-08
cat /mnt/boot/grub.cfg

what does it say (click on the # above to place it between [CODE[SIZE="1"] [/SIZE]] tags

---

### Post by jimbr on 2010-09-09
Sorry lost connection last night! Don't know what you mean "clicking on the # above ...".

Herewith output from a re-run of the commands you sent incl the latest one:

ubuntu@ubuntu:~$ ls -l /mnt/etc/grub.d
total 44
-rwxr-xr-x 1 root root 4444 2010-04-29 07:08 00_header
-rwxr-xr-x 1 root root 1416 2010-04-29 06:45 05_debian_theme
-rwxr-xr-x 1 root root 4594 2010-04-29 07:08 10_linux
-rwxr-xr-x 1 root root 4078 2010-06-17 23:30 10_lupin
-rwxr-xr-x 1 root root  918 2010-03-23 09:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2010-04-29 07:08 30_os-prober
-rwxr-xr-x 1 root root  214 2009-10-24 00:44 40_custom
-rw-r--r-- 1 root root  483 2009-10-24 00:44 README
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 42676
-rw-r--r-- 1 root root  629853 2010-05-27 04:21 abi-2.6.31-22-generic
-rw-r--r-- 1 root root  640617 2010-06-04 01:56 abi-2.6.32-22-generic
-rw-r--r-- 1 root root  651618 2010-08-20 18:22 abi-2.6.32-24-generic
-rw-r--r-- 1 root root  111349 2010-05-27 04:21 config-2.6.31-22-generic
-rw-r--r-- 1 root root  115847 2010-06-04 01:56 config-2.6.32-22-generic
-rw-r--r-- 1 root root  115905 2010-08-20 18:22 config-2.6.32-24-generic
drwxr-xr-x 3 root root    4096 2010-09-07 18:56 grub
-rw-r--r-- 1 root root 7661698 2010-06-18 00:06 initrd.img-2.6.31-22-generic
-rw-r--r-- 1 root root 8271709 2010-06-18 06:42 initrd.img-2.6.32-22-generic
-rw-r--r-- 1 root root 8275569 2010-09-03 18:03 initrd.img-2.6.32-24-generic
-rw-r--r-- 1 root root  160280 2010-03-23 09:37 memtest86+.bin
-rw-r--r-- 1 root root 1668340 2010-05-27 04:21 System.map-2.6.31-22-generic
-rw-r--r-- 1 root root 1687378 2010-06-04 01:56 System.map-2.6.32-22-generic
-rw-r--r-- 1 root root 1689036 2010-08-20 18:22 System.map-2.6.32-24-generic
-rw-r--r-- 1 root root    1196 2010-05-27 04:23 vmcoreinfo-2.6.31-22-generic
-rw-r--r-- 1 root root    1196 2010-06-04 01:58 vmcoreinfo-2.6.32-22-generic
-rw-r--r-- 1 root root    1196 2010-08-20 18:24 vmcoreinfo-2.6.32-24-generic
-rw-r--r-- 1 root root 3900960 2010-05-27 04:21 vmlinuz-2.6.31-22-generic
-rw-r--r-- 1 root root 4030048 2010-06-04 01:56 vmlinuz-2.6.32-22-generic
-rw-r--r-- 1 root root 4034976 2010-08-20 18:22 vmlinuz-2.6.32-24-generic
ubuntu@ubuntu:~$ cat /mnt/boot/grub.cfg
cat: /mnt/boot/grub.cfg: No such file or directory

---

### Post by bcbc on 2010-09-09
My mistake that should have been /mnt/boot/grub/grub.cfg

It might just be easier to rerun the bootinfoscript again.

---

### Post by jimbr on 2010-09-09
> **bcbc said:**
> My mistake that should have been /mnt/boot/grub/grub.cfg

It might just be easier to rerun the bootinfoscript again.

Herewith the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 298464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 298464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 298464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,147,775     3,145,728  12 Compaq diagnostics
/dev/sda2    *      3,147,776   244,320,255   241,172,480   7 HPFS/NTFS
/dev/sda3         244,320,256   467,421,183   223,100,928   7 HPFS/NTFS
/dev/sda4         467,421,184   488,394,751    20,973,568  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,687,679    15,679,616   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1f06deb5-d91b-494f-9667-ccb562c99335   ext4                                     
/dev/loop2       1f06deb5-d91b-494f-9667-ccb562c99335   ext4                                     
/dev/sda1        98FAD0B4FAD08FBC                       ntfs       RECOVERY                      
/dev/sda2        4AB2D34CB2D33AE1                       ntfs                                     
/dev/sda3        2C962C11962BD9DA                       ntfs                                     
/dev/sda4        507A2F3E7A2F1FE8                       ntfs       LG_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5568-7049                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /mnt                     ext4       (rw)
/dev/sda2        /media/4AB2D34CB2D33AE1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 2c962c11962bd9da
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 2c962c11962bd9da
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c962c11962bd9da
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c962c11962bd9da
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c962c11962bd9da
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c962c11962bd9da
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c962c11962bd9da
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c962c11962bd9da
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 98fad0b4fad08fbc
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4ab2d34cb2d33ae1
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


    .1GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
   3.4GB: boot/initrd.img-2.6.31-22-generic
   3.3GB: boot/initrd.img-2.6.32-22-generic
   3.4GB: boot/initrd.img-2.6.32-24-generic
   3.2GB: boot/vmlinuz-2.6.31-22-generic
   3.4GB: boot/vmlinuz-2.6.32-22-generic
   2.2GB: boot/vmlinuz-2.6.32-24-generic
   3.4GB: initrd.img
   3.3GB: initrd.img.old
   2.2GB: vmlinuz
   3.4GB: vmlinuz.old
=============================== StdErr Messages: ===============================

umount: /media/win: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

---

### Post by bcbc on 2010-09-09
> **jimbr said:**
> Herewith the results:

So that all looks good. And still when you try and boot Ubuntu you end up at a grub rescue prompt?

---

### Post by jimbr on 2010-09-10
No - apologies if that is what you thought - the grub rescue issue was solved before I logged this thread - the problem was, and still is, that I cannot boot Ubuntu - if I select Windows it boots correctly but if I select Ubuntu the system gets into a loop:

I get a brief flash of:

Try (hd0,0): NTFS5 No wubildr
Try (hd0,1): NTSF5:

followed by a black screen for a second or so
followed by a gray screen for another second or so
followed by the BIOS boot screen
followed by the screen that allows choice of booting Windows or Ubuntu

This loop goes on as long as I select Ubuntu and will correctly boot Windows if I select Windows.

I hope this is clearer and my apologies for any lack of clarity on my part. Regards, JB

---

### Post by bcbc on 2010-09-10
No it was clear, however before when you ran the bootinfoscript it couldn't loop mount the root.disk, and now it can. So it's worth checking it again.

Ok final thing to try:
Copy the root.disk and swap.disk to a safe place outside of the ubuntu folder. You can even move them (it's much quicker) just make sure they're not in there when you uninstall.

Now reinstall 10.04.1 (the latest version) of Wubi. This will uninstall the old version you have (and delete everything in the aforementioned \ubuntu folder). When you reinstall just pick the smallest size install (3GB).

DON'T reboot when it finishes, before you do, copy your backed up root.disk and swap.disk over the new ones. Then reboot.

I've done this a lot, and no guarantees but it works for me.

---

### Post by jimbr on 2010-09-10
> **bcbc said:**
> No it was clear, however before when you ran the bootinfoscript it couldn't loop mount the root.disk, and now it can. So it's worth checking it again.

Ok final thing to try:
Copy the root.disk and swap.disk to a safe place outside of the ubuntu folder. You can even move them (it's much quicker) just make sure they're not in there when you uninstall.

Now reinstall 10.04.1 (the latest version) of Wubi. This will uninstall the old version you have (and delete everything in the aforementioned \ubuntu folder). When you reinstall just pick the smallest size install (3GB).

DON'T reboot when it finishes, before you do, copy your backed up root.disk and swap.disk over the new ones. Then reboot.

I've done this a lot, and no guarantees but it works for me.

I have safeguarded the 2 files but am worried that I will do something fatal on the uninstall and the reinstall of wubi. Please would you list the steps for me. Thanks, JB

---

### Post by bcbc on 2010-09-10
Go to add/remove programs double click on Ubuntu. That will uninstall the old version.

Download the 10.04.1 .iso from [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and the wubi.exe from [here]("http://wubi-installer.org/"), place them in the same folder - right-click wubi.exe and choose run as administrator. Install to the same 'drive' as before, select the smallest installation size '3GB'. When the installation is done, it will offer to reboot now or later. Click on later. Copy over the root.disk and swap.disk from your backup. Reboot, select Ubuntu from the Windows boot manager. You should see your old grub menu.

---

