---
title: "Upgrade to 18.04 from 16.04. Not enough space in boot"
date: 2018-08-18
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2018-08-18
Dear Forum members,
When trying to upgrade to Ubuntu 18.04 from 16.04, the upgrade aborts with the following message "The upgrade has aborted. The upgrade needs a total of 123 M free space on disk '/boot'. Please free at least an additional 29,7 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove' and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs."

I have cleaned all old kernels (I usually have the version currently in use, plus one just in case. Now I have even cleaned that second one kernel, so I only have the one in use). I have run autoremove and autoclean. The dustbin is empty too (not sure if this helps at all). Since I'm not an expert, I'm reluctant to start playing with initramfs. Is there a way to get those 30M needed to upgrade?

Thanks

---

### Post by Dennis N on 2018-08-18
That's a tough situation. It appears the installer needs to put stuff in there before deleting any content that will not be needed post-install. I've seen the same error, but on the / partition. 

Clearly, there are these two fixes:

1) increase the size of **/boot** partition.
2) delete some content from **/boot**.

If neither is possible (or feasible), you would need a new install to upgrade the OS.

You could post the contents of **ls -l /boot** to get some forum input on any further steps for option 2. 
You could post your partition table to explore possibility of option 1. (**sudo parted -l** or a gparted screenshot.)

---

### Post by ubfan1 on 2018-08-18
Maybe you don't need a /boot partition, which was useful to move the kernels to the beginning of a disk when BIOS addressing was too limited to address a kernel further into the disk, or for encrypted logical volumes/raid.  A possible third fix is to copy everytihng in the /boot partition into the root's /boot directory (so the boot partition would need to be remounted somewhere else like /mnt/boot).  Then comment out the /etc/fstab line which mounts the /boot partitiony, and see if you can successfully boot.  Your space problem is then a root filesystem space, not some small partition filesystem.  If the remount fails on the running system, then just use a live media to mount the boot and root partitions for doing the copy.

---

### Post by Pablo W on 2018-08-18
> **Dennis N said:**
> That's a tough situation. It appears the installer needs to put stuff in there before deleting any content that will not be needed post-install. I've seen the same error, but on the / partition. 

Clearly, there are these two fixes:

1) increase the size of **/boot** partition.
2) delete some content from **/boot**.

If neither is possible (or feasible), you would need a new install to upgrade the OS.

You could post the contents of **ls -l /boot** to get some forum input on any further steps for option 2. 
You could post your partition table to explore possibility of option 1. (**sudo parted -l** or a gparted screenshot.)

Thank you, Dennis N. 
The contents of ls -l /boot are: 
```
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$  ls -l /boot
total 127446
-rw-r--r-- 1 root root  1251634 jul 12 20:58 abi-4.4.0-131-generic
-rw-r--r-- 1 root root  1251923 ago 10 08:20 abi-4.4.0-133-generic
-rw-r--r-- 1 root root   190566 jul 12 20:58 config-4.4.0-131-generic
-rw-r--r-- 1 root root   190587 ago 10 08:20 config-4.4.0-133-generic
drwxr-xr-x 5 root root     1024 ago 18 09:46 grub
-rw-r--r-- 1 root root 52203737 ago  4 10:47 initrd.img-4.4.0-131-generic
-rw-r--r-- 1 root root 52201178 ago 18 09:46 initrd.img-4.4.0-133-generic
drwx------ 2 root root    12288 jun 29  2014 lost+found
-rw-r--r-- 1 root root   182704 ene 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 ene 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 ene 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root      255 jul 12 20:58 retpoline-4.4.0-131-generic
-rw-r--r-- 1 root root      255 ago 10 08:20 retpoline-4.4.0-133-generic
-rw------- 1 root root  3900257 jul 12 20:58 System.map-4.4.0-131-generic
-rw------- 1 root root  3902569 ago 10 08:20 System.map-4.4.0-133-generic
-rw------- 1 root root  7156128 jul 12 20:58 vmlinuz-4.4.0-131-generic
-rw------- 1 root root  7159744 ago 10 08:20 vmlinuz-4.4.0-133-generic
```

And sudo parted -l looks like this:
```
Modelo: ATA TOSHIBA THNSNH25 (scsi)
Disco /dev/sda: 256GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: msdos
Disk Flags: 

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  256MB  255MB   primary   ext2                 arranque
 2      257MB   256GB  256GB   extended
 5      257MB   256GB  256GB   logical


Modelo: Asignador de dispositivos de Linux (linear) (dm)
Disco /dev/mapper/ubuntu--vg-swap_1: 8502MB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: loop
Disk Flags: 

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Banderas
 1      0,00B   8502MB  8502MB  linux-swap(v1)


Modelo: Asignador de dispositivos de Linux (linear) (dm)
Disco /dev/mapper/ubuntu--vg-root: 247GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: loop
Disk Flags: 

Numero  Inicio  Fin    Tamaño  Sistema de archivos  Banderas
 1      0,00B   247GB  247GB   ext4


Error: /dev/mapper/sda5_crypt: etiqueta de disco no reconocida
Modelo: Asignador de dispositivos de Linux (crypt) (dm)                   
Disco /dev/mapper/sda5_crypt: 256GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: unknown
Disk Flags: 
```

---

### Post by Dennis N on 2018-08-18
Your setup is lvm, and has encryption. Is that correct?  If so, my understanding is that you do need the boot partition when you use encryption.

My suggestion:
You have two kernels. You could purge the 4.4.0-131 kernel and recover some space. Question is, will that be enough to satisfy the Software updater? Try this with Synaptic Package manager, search for 4.4.0-131 and select all the 4.4.0-131 packages. Mark these for complete removal. Check how much space it reports will be recovered - it is given at the bottom. If you decide it is enough, then if you want to complete the removal, use the 'Apply' button on the toolbar.

As a test, I opened Synaptic, and selected the five 4.4.0-130 kernel packages on my ubuntu mate 16.04. Synaptic reports this will free 303 mB (see screen shot attatched, info bar at bottom of Synaptic window), which is more than your entire boot partition? So see what yours reports. 

Then try the upgrade again.

---

### Post by ubfan1 on 2018-08-18
Lots of the kernel associated packages put files outside of /boot.  Modules go to /lib/modules/..., headers to /usr/src..., etc.  Typically, a kernel's file in /boot will be less than 80M.

---

### Post by Pablo W on 2018-08-19
Thank you, Dennis and ubfan1.
I have applied Dennis's suggestion. Since I don't have synaptic, I did one of the few things I can manage through command line: purged all the 4.4.0-131 packages, which left 302 Mb of extra free space. In theory, I should be able to run the upgrade now. Before I do so, is there anything I could do to prevent this lack of space in boot (like making it bigger)? I do have encryption. Or maybe there's nothing I can do and I should just keep purging all but the current kernel regularly?

---

### Post by LHammonds on 2018-08-19
Your boot partition is only 255 MB.  My standard for server deployments is 512 MB.  This is more than sufficient to keep 3 kernels at one time (current+prior+new download).

I run the "apt autoremove" command via crontab on a regular basis which typically keeps the current kernel and the prior kernel.

If 255 MB is not enough to keep 2 kernels, you are going to need to do more than the simple "apt autoremove" command. Keep in mind that it is generally not a good idea to not have a prior kernel available.

I can show you the commands I used when I manually removed kernels myself (before autoremove worked the way I wanted).  I never automated these commands via script because I never wanted the scenario where the script mistakenly purged the wrong kernel.

First, I check which version is currently being used with this command.  You might have downloaded a new version but have not rebooted and are using the prior version. If you need to reboot to activate the current version, do so before continuing.
```
uname -a
```

Example output:
```

Linux srv-ubuntu 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 18 11:48:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Next, I would list the kernels in /boot (mine all started with "vm" as a prefix because I run in a virtual environment)
```

ls -l /boot/vm*

```

Example output:
```

-rw------- 1 root root 7104528 Jan  9  2018 /boot/vmlinuz-4.4.0-109-generic
-rw------- 1 root root 7110608 Jan 19  2018 /boot/vmlinuz-4.4.0-112-generic

```

Then I would remove the oldest kernel.  In this case, it is 4.4.0-109
```

sudo apt-get purge linux-image-4.4.0-109-generic

```

Next, I would find the matching headers:
```

ls -l /usr/src

```

Example output:
```

drwxr-xr-x 27 root root 4096 Jan 13  2018 linux-headers-4.4.0-109
drwxr-xr-x  7 root root 4096 Jan 13  2018 linux-headers-4.4.0-109-generic
drwxr-xr-x 27 root root 4096 Feb  2  2018 linux-headers-4.4.0-112
drwxr-xr-x  7 root root 4096 Feb  2  2018 linux-headers-4.4.0-112-generic

```

Then I would remove the matching headers with a command like this (note, you do not need to include "-generic" at this point):
```

sudo apt-get purge linux-headers-4.4.0-109

```

LHammonds

---

### Post by Pablo W on 2018-08-26
Thanks for your detailed explanation, LHammonds.

I see your point and I think that you are right: my boot partition is too small.
The first update after upgrading to 18.04 is again cancelled due to a lack of space in /boot 
Is there a way to increase its size without having to do a fresh install?

 ls -l /boot now looks like this:
```
pablowains@ATIV-BOOK-9PLUS-NP940X3G-K04US:~$ ls -l /boot
total 81294
-rw-r--r-- 1 root root  1537455 ago 10 14:22 abi-4.15.0-32-generic
-rw-r--r-- 1 root root   216860 ago 10 14:22 config-4.15.0-32-generic
drwxr-xr-x 5 root root     1024 ago 25 11:02 grub
-rw-r--r-- 1 root root 68280838 ago 25 11:03 initrd.img-4.15.0-32-generic
drwx------ 2 root root    12288 jun 29  2014 lost+found
-rw-r--r-- 1 root root   182704 ene 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 ene 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 ene 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root        0 ago 10 14:22 retpoline-4.15.0-32-generic
-rw------- 1 root root  4042389 ago 10 14:22 System.map-4.15.0-32-generic
-rw------- 1 root root  8265464 ago 10 14:35 vmlinuz-4.15.0-32-generic
```

---

