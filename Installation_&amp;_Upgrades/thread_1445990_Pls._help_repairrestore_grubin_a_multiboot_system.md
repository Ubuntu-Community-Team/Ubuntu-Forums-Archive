---
title: "Pls. help repair/restore grubin a multiboot system"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by iClouseau88 on 2010-04-03
Hi everyone,

Hi,

I have a laptop with 250 GB SATA HD that has the following:

Win7 Pro installed first with sda1=system reserved partition, sda2=C: drive, sda5=separate software application programs to differentiate from Windows' Program Files. Ubuntu 9.10 was installed next (sda6=common swap partition for all Linux distros, sda7=Ubuntu root, sda8=Ubuntu home). Then Opensuse 11.2 was installed with sda12=root and sda13=home. Finally FedoraCore11 was installed with sda9=boot, sda10=root and sda11=home. Ubuntu and Suse have grub loader in their own root partitions.

Suse's grub menu controls all OS's. From this grub menu I can select Windows or any other Linuxes. Suse uses legacy grub because it was installed right after Ubuntu 9.10 which uses (legacy) grub.

Here is opensuse's grub menu:

# Modified by YaST2. Last modification on Wed Mar 31 11:49:28 EST 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 1
timeout 15
##YaST - generic_mbr
gfxmenu (hd0,11)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Debug -- openSUSE 11.2 - 2.6.31.12-0.2
root (hd0,11)
kernel /boot/vmlinuz-2.6.31.12-0.2-debug root=/dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090707FB2D00LJCT6UGB-part12 resume=/dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090707FB2D00LJCT6UGB-part6 splash=silent quiet showopts vga=0x317
initrd /boot/initrd-2.6.31.12-0.2-debug

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2 - 2.6.31.12-0.2
root (hd0,11)
kernel /boot/vmlinuz-2.6.31.12-0.2-default root=/dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090707FB2D00LJCT6UGB-part12 resume=/dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090707FB2D00LJCT6UGB-part6 splash=silent quiet showopts vga=0x317 acpi=off noapic
initrd /boot/initrd-2.6.31.12-0.2-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.12-0.2
root (hd0,11)
kernel /boot/vmlinuz-2.6.31.12-0.2-default root=/dev/disk/by-id/ata-Hitachi_HTS543225L9A300_090707FB2D00LJCT6UGB-part12 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
initrd /boot/initrd-2.6.31.12-0.2-default

###Don't change this comment - YaST2 identifier: Original name: Ubuntu 9.10, kernel 2.6.31-20-generic (/dev/sda7)###
title Ubuntu 9.10, kernel 2.6.31-20-generic (/dev/sda7)
rootnoverify (hd0,6)
chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title Windows 7_Professional_32-bit
rootnoverify (hd0,0)
chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
rootnoverify (hd0,1)
chainloader +1

###Add Fedora Core 11 to the GRUB menu###
title Fedora Core 11 on /dev/sda10 (root partition sda10)
configfile (hd0, /grub/grub.conf

$fdisk -l gives:

Device Boot Start End Blocks Id System
/dev/sda1 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 13 3200 25600000 7 HPFS/NTFS
/dev/sda3 * 3201 15332 97450290 5 Extended
/dev/sda5 3201 6387 25599546 7 HPFS/NTFS
/dev/sda6 6388 6514 1020096 82 Linux swap / Solaris
/dev/sda7 6515 7534 8193118+ 83 Linux
/dev/sda8 7535 8519 7911981 83 Linux
/dev/sda9 11560 11582 184716 83 Linux
/dev/sda10 11583 13390 14522728+ 83 Linux
/dev/sda11 13391 15332 15599083+ 83 Linux
/dev/sda12 8520 10057 12353953+ 83 Linux
/dev/sda13 10058 11559 12064783+ 83 Linux

My problem is that while trying to fix a problem upgrading Ubuntu 9.10 to 10.04 LTS beta1 which I eventually overcame, I misunderstood about grub and thought I would have to (re)install grub to Ubuntu because sudo gedit /etc/boot/grub/menu.lst gives a blank file (I found out much later this is because Ubuntu 10.10 uses grub2 which replaces grub's /etc/boot/grub/menu.lst with /etc/boot/grub/grub.cfg). Following a recent Ubuntuforums tutorial entitled"Grub/XP/Vista Boot Loader", I did the following commands to restore grub to Ubuntu:

sudo mkdir /media/sda7

sudo mount /dev/sda7 /media/sda7

Install grub to /dev/sda as (hd0):

sudo grub-install --root-directory=/media/sda7 /dev/sda

Then I only saw Ubuntu's grub menu. In a panic, I tried to reverse the above in order to install grub back to opensuse (sda12) hoping to get back to the way it was before:

sudo mkdir /media/sda12

sudo umount /dev/sda7 /media/sda7

sudo mount /dev/sda12 /media/sda12

sudo grub-install --root-directory=/media/sda12 /dev/sda12

Somehow I also messed up Windows' boot file and boot partition table. Now I am still trying to use Windows installation CD to repair Windows but it has taken several hours and am still waiting for screen response. I cannot boot into any Linux distro either.

I would very much appreciate your help restoring grub so that I can boot into Windows and any Linux distros.

:confused:

---

### Post by oldfred on 2010-04-03
You have a complex set up. I have three drives and 4 installs but all the linux one's so far are versions of Ubuntu. I run this script myself before and after changes just to make sure where things are at. Yours will be very long so be sure to use the code tags.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by iClouseau88 on 2010-04-03
Hi,

I currently cannot boot into my laptop because it's been taking many hours searching and searching for problems to do a startup repair! Hence, I cannot download and make use of the Boot Info script you gave.  Any other suggestions?

---

### Post by oldfred on 2010-04-03
The script is able to run from a liveCD and most linux systems as it uses the linux commands to create the report.

---

### Post by iClouseau88 on 2010-04-04
Hi,

Windows 7 is restored now but I still need to do a few cleanup, backing up and partitioning tasks before I can re-install Ubuntu and the other Linux distros. The restoration wiped out the penguins!

---

### Post by oldfred on 2010-04-04
Windows install usually does not remove the Ubuntu install but just the grub boot loader. You should be able to reinstall that.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

