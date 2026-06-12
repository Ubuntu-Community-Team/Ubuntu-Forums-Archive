---
title: "Problems with new kernel."
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by Portaro on 2013-08-24
I have a strange problem with the last kernel - linux-generic - for some reason only kernel 3.2.0.25 works the others dont boot.

I have this kernels on the system -
> dpkg --list | grep linux-image
rc  linux-image-3.8.0-19-generic                                3.8.0-19.30                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-23-generic                                3.8.0-23.34                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-25-generic                                3.8.0-25.37                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-26-generic                                3.8.0-26.38                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-29-generic                                3.8.0-29.42                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-19-generic                          3.8.0-19.30                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-23-generic                          3.8.0-23.34                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-25-generic                          3.8.0-25.37                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-26-generic                          3.8.0-26.38                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-27-generic                          3.8.0-27.40                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-29-generic                          3.8.0-29.42                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.8.0.29.47                                i386         Generic Linux kernel image


My system is a 32 bits, with 1.5GB ram, Xubuntu 13.04.

If i try choose boot with 3.8.0-29 the boot stops on a black screen.
If i try 3.8.0-26 appear a text with error on /sbin/blkid -o udev -p /dev/sda

My /dev/sda dont have problems the disk partition dont have problems works fine with 3.8.0-25 kernel.

IN other kernel boot types after launch appear 
"INitial ramdisk" and stops in this message.

I dont understand why i have a differente messages of error and freezings with distinct kernels.


At this moment i update grub, and use grub customizer to put the kernel 3.8.0-25 to default boot entry type. Works fine.

Thanks:popcorn:

---

### Post by Portaro on 2013-08-27
i use 
**sudo parted -l**
[sudo] password for joao: 
Modelo: ATA Maxtor 6Y120L0 (scsi)
Disco /dev/sda: 123GB
Tamanho de sector (lógico / físico): 512B/512B
Tabela de Partições: msdos


Número  Início  Final   Tamanho  Tipo      Sistema de ficheiros  Sinalizadores
 1      1049kB  4000MB  3999MB   primary   linux-swap(v1)
 2      4000MB  42,0GB  38,0GB   primary   ext4                  boot
 3      42,0GB  123GB   80,9GB   extended
 5      42,0GB  123GB   80,9GB   logical   ext4


I dont understand the problem , i dont have any other os on the pc, the partitions are ok but with any other kernel i have this problem dont boot because /sbin/blkid dont mount sda properly

---

### Post by Portaro on 2013-08-27
I have this config on /etc/default/grub is this correct?

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1280x1024"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Portaro on 2013-08-27
Much bad news 

sudo fdisk /dev/sda2 -l

Disco /dev/sda2: 38.0 GB, 38000000000 bytes
255 cabeças, 63 setores/trilhas, 4619 cilindros, total de 74218750 setores
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 512 bytes
Tamanho da E/S (mínimo/ideal): 512 bytes / 512 bytes
Identificador do disco: 0x00000000

O disco /dev/sda2 não contém uma tabela de partições válida
( the disk dont containing a valid partition )

SO i need reinstall other time an os. 
I dislike this.

---

### Post by Portaro on 2013-08-27
$ sudo blkid 
/dev/sda1: UUID="94d532e9-7773-4702-81b8-e66fb81bd694" TYPE="swap" 
/dev/sda2: UUID="bd632a49-f3d0-4e86-a05e-aa950abea715" TYPE="ext4" 
/dev/sda5: UUID="125c6461-29cc-4d1a-a7cb-aca5632e32e5" TYPE="ext4" 
/dev/sdb1: LABEL="seagate" UUID="21c532aa-ac36-4275-a900-6bdf2b36bf79" TYPE="ext4" 
/dev/sdc1: LABEL="Elements" UUID="52C2D361C2D347BD" TYPE="ntfs"

---

### Post by Portaro on 2013-08-27
What a frust day.

I search here and raring 3.8.0.25 dont appear 3.8.0-25-generic
[http://packages.ubuntu.com/search?suite=raring&arch=i386&keywords=linux-image](http://packages.ubuntu.com/search?suite=raring&arch=i386&keywords=linux-image)

SO how i have this kernel eheh

---

### Post by Bashing-om on 2013-08-27
Portaro; Hello;

I tend to think (re-)installing is a good thing to do because:
> 
/dev/sda1: UUID="94d532e9-7773-4702-81b8-e66fb81bd694" TYPE="swap" 

device "sda1" is normally associated as the "root" partition and 
"swap" is usually in a partition of "sda5 or higher".

It is a thought that grub is looking for the boot code in the invalid place ??
I would think I would want my partitions in the customary order.

also grub:
the last config line should read as:
> 
GRUB_CMDLINE_LINUX=""

also in grub:
> 
GRUB_GFXMODE="1280x1024"

are you certain and sure that both your graphics card and your monitor support this high of a resolution:
the default entry is:
> 
#GRUB_GFXMODE=640x480
 note that it is commented (#) out and thus not processed.
What is not also known is what changes have been made to other grub configuration files and if custom files have been made.

[INDENT][INDENT]this is just my opinion, for what it is worth
[/INDENT][/INDENT]

---

### Post by Portaro on 2013-08-28
Yeah at this moment i need to reinstall the distro the boot parameters losts and i definitevely lost my only connection kernel and i need reinstall all.
I always readapt grub because my pc in some cases when i change theme plymouth the config of default grub i need change if not the plymouth appear is the text or without image.
Th problem is not in partition because i use fsck and nothing error give to me.
I dont have any idea about the original cause of problem is very strange.

---

### Post by Bashing-om on 2013-08-29
Portaro;

In my opinion and experience ( I have broke my system several times, learning ), (Re-)installing to get a clean working environment is often a good thing. Grub as you know can be as complicated of a process as you make it.
Here are three of my favorite guides:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
There are many others.

As grub determines what kernel gets loaded and from where.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by Portaro on 2013-09-04
yes you are in reason and  i apreciate the help that you provide to me.

---

### Post by Bashing-om on 2013-09-04
Portaro; You are quite welcome.

After all this is open source and;
[INDENT][INDENT]we are all in this together
[/INDENT][/INDENT]

---

