---
title: "Gutsy hangs &quot;running local boot scripts&quot;"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by chiefnerdnc on 2008-05-18
Hi,
I just installed Gutsy on an Averatec 3225 laptop and the boot hangs after "Running Local boot scripts (/etc/rc.local). Any ideas? I can ping the machine so it must be running. I'm trying to break from windows and this is my path out...if i can get a gui
Thanks,

---

### Post by Pumalite on 2008-05-18
Run in recovery mode and check your UUID's
Check blkid againt /etc/fstab and /boot/grub/menu.lst
Post:
blkid
cat /etc/fstab
cat /boot/grub/menu.lst

---

### Post by chiefnerdnc on 2008-05-18
Thanks for the info. I can run all 3 but what am i looking for? I'm pretty sure my problem is the VIA video drivers aren't loaded.
Can you give a new guy a hint?
Thanks,

---

### Post by Pumalite on 2008-05-18
If you think it's video; try
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver.

---

### Post by chiefnerdnc on 2008-05-19
Here is one command
login as: k7
k7@192.168.7.102's password:
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Mon May 19 17:57:43 2008
k7@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for k7:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080519175957
k7@ubuntu:~$ blkid
k7@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d935b70b-8116-41ca-946c-4cbedd930cfb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
k7@ubuntu:~$
k7@ubuntu:~$ ubuntu:~$ cat /etc/fstab
-bash: ubuntu:~$: command not found
k7@ubuntu:~$ # /etc/fstab: static file system information.
k7@ubuntu:~$ #
k7@ubuntu:~$ # <file system> <mount point>   <type>  <options>       <dump>  <pass>
k7@ubuntu:~$ proc            /proc           proc    defaults        0       0
-bash: proc: command not found
k7@ubuntu:~$ # /dev/sda1
k7@ubuntu:~$ UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad /               ext3    relatime,errors=remount-ro 0       1
-bash: /: is a directory
k7@ubuntu:~$ # /dev/sda5
k7@ubuntu:~$ UUID=d935b70b-8116-41ca-946c-4cbedd930cfb none            swap    sw              0       0
-bash: none: command not found
k7@ubuntu:~$ /dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-bash: /dev/scd1: No such file or directory
k7@ubuntu:~$ /dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
-bash: /dev/scd0: Permission denied
k7@ubuntu:~$ k7@ubuntu:~$
-bash: k7@ubuntu:~$: command not found
k7@ubuntu:~$ k7@ubuntu:~$
-bash: k7@ubuntu:~$: command not found
k7@ubuntu:~$


Here is the other

---

### Post by chiefnerdnc on 2008-05-19
here is the other

login as: k7
k7@192.168.7.102's password:
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Mon May 19 17:57:43 2008
k7@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for k7:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080519175957
k7@ubuntu:~$ blkid
k7@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d935b70b-8116-41ca-946c-4cbedd930cfb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
k7@ubuntu:~$
k7@ubuntu:~$ ubuntu:~$ cat /etc/fstab
-bash: ubuntu:~$: command not found
k7@ubuntu:~$ # /etc/fstab: static file system information.
k7@ubuntu:~$ #
k7@ubuntu:~$ # <file system> <mount point>   <type>  <options>       <dump>  <pass>
k7@ubuntu:~$ proc            /proc           proc    defaults        0       0
-bash: proc: command not found
k7@ubuntu:~$ # /dev/sda1
k7@ubuntu:~$ UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad /               ext3    relatime,errors=remount-ro 0       1
-bash: /: is a directory
k7@ubuntu:~$ # /dev/sda5
k7@ubuntu:~$ UUID=d935b70b-8116-41ca-946c-4cbedd930cfb none            swap    sw              0       0
-bash: none: command not found
k7@ubuntu:~$ /dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-bash: /dev/scd1: No such file or directory
k7@ubuntu:~$ /dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
-bash: /dev/scd0: Permission denied
k7@ubuntu:~$ k7@ubuntu:~$
-bash: k7@ubuntu:~$: command not found
k7@ubuntu:~$ k7@ubuntu:~$
-bash: k7@ubuntu:~$: command not found
k7@ubuntu:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=cfd4e499-6d03-4daa-bc1e-0238a90a9dad ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
k7@ubuntu:~$

---

### Post by Pumalite on 2008-05-19
Try:
sudo blkid

---

### Post by chiefnerdnc on 2008-05-19
How do you run the VESA Video Driver?

---

### Post by Pumalite on 2008-05-19
After the command; accept most defaults, choose vesa as the driver. Then: startx

---

### Post by chiefnerdnc on 2008-05-19
Here is the BLKID

login as: k7
k7@192.168.7.102's password:
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Mon May 19 17:58:19 2008 from 192.168.7.101
k7@ubuntu:~$ sudo blkid
/dev/sda1: UUID="cfd4e499-6d03-4daa-bc1e-0238a90a9dad" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="d935b70b-8116-41ca-946c-4cbedd930cfb"
k7@ubuntu:~$


On choosing the vesa driver, i only get a yes or no then about 6 questions about the keyboard. What step am i missing?
Thanks,

---

### Post by Pumalite on 2008-05-19
Your UUID's seem OK. On the question of configuring your xserver; refer to my previous post. You might ckeck your UUID's your self.
Post:
sudo fdisk -l

---

### Post by chiefnerdnc on 2008-05-19
here is the fdisk -l

login as: k7
k7@192.168.7.102's password:
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Mon May 19 17:58:19 2008 from 192.168.7.101
k7@ubuntu:~$ sudo blkid
/dev/sda1: UUID="cfd4e499-6d03-4daa-bc1e-0238a90a9dad" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="d935b70b-8116-41ca-946c-4cbedd930cfb"
k7@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005695e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
k7@ubuntu:~$
k7@ubuntu:~$

---

### Post by Pumalite on 2008-05-19
Try:
sudo aptitude install ubuntu-desktop

---

### Post by chiefnerdnc on 2008-05-19
Hi,
ran that and rebooted: here is the output

login as: k7
k7@192.168.7.102's password:
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Mon May 19 18:25:57 2008 from 192.168.7.101
k7@ubuntu:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been automatically kept back:
  libhal1 xserver-xorg-video-intel
The following packages have been kept back:
  apparmor apparmor-utils apport apport-gtk bsdutils capplets-data
  compiz-fusion-plugins-main evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-plugins
  foomatic-filters friendly-recovery gdm gksu gnome-about
  gnome-control-center gnome-desktop-data gnome-panel gnome-panel-data
  gnome-settings-daemon gnome-system-monitor gstreamer0.10-plugins-good
  gtk2-engines-pixbuf gvfs gvfs-backends gvfs-fuse hal jockey-common
  jockey-gtk libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libgdata-google1.2-1
  libgdata1.2-1 libglib2.0-0 libgnome-desktop-2 libgnome-window-settings1
  libgphoto2-2 libgphoto2-port0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgvfscommon0 libhal-storage1 libldap-2.4-2 libnautilus-extension1
  libpanel-applet2-0 libspeex1 libtotem-plparser10 lshw mount nautilus
  nautilus-data openssl python-apport python-problem-report python-virtkey
  ssh-askpass-gnome ssl-cert sudo transmission-common transmission-gtk
  update-manager update-manager-core util-linux util-linux-locales
  xulrunner-1.9 xulrunner-1.9-gnome-support
0 packages upgraded, 0 newly installed, 0 to remove and 78 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
k7@ubuntu:~$ startx
Broadcast message from root@ubuntu
        (unknown) at 18:53 ...

The system is going down for reboot NOW!
Control-Alt-Delete pressed

Still no desktop after reboot. Got another trick?


By the way...Thanks For help

---

### Post by Pumalite on 2008-05-19
sudo aptitude update
sudo aptitude upgrade

---

### Post by chiefnerdnc on 2008-05-19
Ok, That downloaded and installed a long list of "hardy" files. Rebooted at the end and still don't have a GUI. I'm acutually SSHing in from my windows box. 
What's the next trick?

---

### Post by Pumalite on 2008-05-20
Run again:
sudo aptitude install ubuntu-desktop
Post the out put.
Post:
lshw

---

### Post by chiefnerdnc on 2008-05-20
Here is the first:

login as: k7
k7@192.168.7.102's password:
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Tue May 20 17:58:32 2008
k7@ubuntu:~$ sudo aptitude install ubuntu-desktop
[sudo] password for k7:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  ssl-cert
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
k7@ubuntu:~$


And the second:

mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts fid vid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 979MiB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: VT8378 [S3 UniChrome] Integrated Video
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
        *-network:0
             description: Wireless interface
             product: RT2500 802.11g Cardbus/mini-PCI
             vendor: RaLink
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wmaster0
             version: 01
             serial: 00:0c:76:ca:c5:e6
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: IC25N040ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO2O
                serial: MRG254KBCSS04P
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005695e
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: cfd4e499-6d03-4daa-bc1e-0238a90a9dad
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-18 10:26:47 filesystem=ext3 modified=2008-05-20 17:58:59 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-05-20 17:57:44 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SBW242B
                vendor: QSI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/dvd2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UX52
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:40:45:19:1b:96
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.7.102 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
k7@ubuntu:~$

---

### Post by Pumalite on 2008-05-20
Here is your problem:
*-display UNCLAIMED
description: VGA compatible controller
product: VT8378 [S3 UniChrome] Integrated Video
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
configuration: latency=32 mingnt=2

The kernel does not recognize your display and does nor load the module.

---

### Post by chiefnerdnc on 2008-05-20
Gee, most Kernels i know are nice guys  :) How do i get him to play nice?

---

### Post by Pumalite on 2008-05-20
Try a different version of Ubuntu and if that doesn't work; a different distro. You might end up being incompatible with Linux in general or Ubuntu in particular.

---

### Post by chiefnerdnc on 2008-05-20
Thank you for trying. It was a good learning experience.

---

