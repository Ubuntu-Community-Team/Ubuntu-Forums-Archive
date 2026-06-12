---
title: "upgrade 10.10 server to 11.04 server failed?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2011-04-30
I am running 2 Ubuntu servers, one as UEC frontend and the other as UEC node. I started, last night, the server upgrade on the frontend. As it promised to take several hours I left it alone to proceed through the night. This morning it was waiting on a prompt which, by virtue of hitting esc to relight the monitor, it continued upgrading packages. At some point subsequent to that it paused on a discrepancy between the eucalyptus.conf file the install wanted to save and the eucalyptus.conf file that existed. I reviewed the deltas and determined that the current, as it existed, would suffice. I received 3 more messages on the console:

Installing new version of config file /etc/init/eucalyptus-network.conf...
Installing new version of config file /etc/init/eucalyptus-conf...
eucalyptus start/running process 15290

Then no further console messages nor apparent disk or cpu activity
I can shell into the machine and see the following:
```

root      7077  6784  0 Apr29 tty1     00:00:33 /usr/bin/python /tmp/update-manager-0r8nH5/natty --mode=server --frontend=DistUpgradeViewText
root     18950  7077  0 Apr29 tty1     00:00:02 /usr/bin/python /tmp/update-manager-0r8nH5/natty --mode=server --frontend=DistUpgradeViewText

```
I am not sure why that second instance exists, but perhaps that is normal.
I believe it is off, if the upgrade was completed that I saw no indication of such or the machine did not reboot itself. In an attempt to determine if the upgrade was complete I issued lsb_release -a and it looked like the server is upgraded:
```
walt@cor9100:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

```

I do not, however, believe the process is completed as those two upgrade processes are still running and occasionally one shows up in a top command as "Natty"

I hesitate to reboot myself as I would expect the system to not successfully boot and then I'd be forced to do a fresh install, losing my customized settings for the second eth and eucalyptus frontend configs.

I looked at various logs and can not see an obvious error or any situation requiring remedial action. I can not believe this wasn't tested so I am at a loss to determine where this upgrade stands.

In case you are curious, this process was started via:

sudo do_release_upgrade.

Would anyone advise?

Thanks,

Walt

---

### Post by dino99 on 2011-04-30
only by curiosity, maybe:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

but if logs are clean you might be safe

---

### Post by wcorey on 2011-04-30
> **dino99 said:**
> only by curiosity, maybe:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

but if logs are clean you might be safe

Does that implicitly mean I should kill those two pids I referred to?

---

### Post by wcorey on 2011-04-30
> **dino99 said:**
> only by curiosity, maybe:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

but if logs are clean you might be safe

Does that implicitly mean I should kill those two pids I referred to?

I did another ps and found this guy, that I think is the motherlode:

```
root     10689 18950  0 08:25 pts/1    00:00:00 /usr/bin/dpkg --force-overwrite --status-fd 26 --configure libgdbm3 perl perl-modules bzip2 adduser cron initramfs-tools-bin libklibc klibc-utils busybox-initramfs cpio module-init-tools libpcre3 libglib2.0-0 libusb-0.1-4 libncursesw5 procps udev initramfs-tools dmsetup libdevmapper1.02.1 libfreetype6 libfuse2 gettext-base grub-common ucf grub-pc grub-gfxpayload-lists tzdata-java fuse-utils libck-connector0 libdbus-glib-1-2 libpolkit-gobject-1-0 xkb-data libxau6 libxdmcp6 libxcb1 libx11-data libx11-6 libexpat1 dbus consolekit hdparm libdevmapper-event1.02.1 readline-common libreadline6 lvm2 libdrm2 libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libpng12-0 libplymouth2 mountall plymouth ifupdown mime-support libsqlite3-0 python2.7 python2.6 libpython2.6 iso-codes python apt-utils python-apt-common python-apt python-support python-dbus language-selector-common python-openssl python-central python-twisted-bin python-pkg-resources python-zope.interface python-twisted-core python-twisted-web libffi5 libgirepository-1.0-1 gir1.2-glib-2.0 python-gobject libgpg-error0 libgcrypt11 libtasn1-3 libgnutls26 libkeyutils1 libkrb5support0 libk5crypto3 libkrb5-3 libgssapi-krb5-2 libidn11 libsasl2-2 libldap-2.4-2 openssl ca-certificates libcurl3-gnutls python-pycurl libaxis2c0 libcap2 librampart0 libwrap0 libedit2 openssh-client openssh-server libavahi-common-data libavahi-common3 libavahi-client3 libavahi-core7 libgeoip1 libxml2 libisc62 libdns69 libisccc60 libisccfg62 libbind9-60 liblwres60 bind9-host avahi-daemon avahi-utils eucalyptus-common python-m2crypto python-boto euca2ools gpgv gnupg python-image-store-proxy libgmp3c2 python-crypto python-pam libxapian22 python-xapian fontconfig-config libfontconfig1 libpixman-1-0 libxcb-render0 libxcb-shm0 libxrender1 libcairo2 python-cairo python-gobject-cairo command-not-found-data python-gdbm lsb-release command-not-found libnfnetlink0 iptables ufw python-gnupginterface update-manager-core python-yaml libsasl2-modules dnsutils isc-dhcp-common iproute isc-dhcp-client dhcp3-client netbase ntpdate libxext6 popularity-contest locales language-pack-en-base language-pack-en libatk1.0-data libatk1.0-0 libice6 x11proto-core-dev libice-dev libdatrie1 libthai-data libthai0 libxft2 fontconfig libpango1.0-0 libsm6 libjpeg62 libtiff4 libx11-xcb1 libxcomposite1 libxfixes3 libxcursor1 libxdamage1 libxi6 libxinerama1 libxrandr2 libxt6 wireless-crda linux-image-2.6.38-8-server libboost-iostreams1.42.0 libsigc++-2.0-0c2a libcwidget3 libept1 aptitude tasksel tasksel-data xtrans-dev keyboard-configuration kbd console-setup eject libmagic1 file iputils-ping libatm1 libnewt0.52 logrotate netcat-openbsd rsyslog sudo ureadahead vim-common vim-tiny vim-runtime vim whiptail ubuntu-minimal apparmor libapparmor1 libapparmor-perl apparmor-utils apt-transport-https bash-completion bsdmainutils busybox-static dmidecode ed friendly-recovery geoip-database groff-base info iputils-tracepath libcap-ng0 irqbalance libelf1 liburi-perl libhtml-parser-perl libhtml-tree-perl libdmraid1.0.0.rc16 dmraid libparted0debian1 libpci3 pciutils libpipeline1 libwww-perl libxmuu1 usbutils lshw ltrace man-db manpages memtest86+ mlocate mtr-tiny nano parted plymouth-theme-ubuntu-text ppp pppconfig psmisc rsync sgml-base tcpdump time wget ubuntu-standard uuid-runtime xauth openjdk-6-jre-lib java-common libcups2 liblcms1 libnspr4 libnss3 libnss3-1d openjdk-6-jre-headless default-jre-headless ant ant-optional icedtea-6-jre-cacao libnspr4-0d libapr1 libaprutil1 libaprutil1-ldap libaprutil1-dbd-sqlite3 apache2.2-bin apache2-utils apache2.2-common apache2-mpm-worker apache2 apt-mirror python-chardet python-debian apt-xapian-index bittornado python-bittorrent bittorrent libgmpxx4ldbl libppl7 libppl-c2 libcloog-ppl0 libelfg0 libmpfr4 libmpc2 cpp-4.5 cpp gcc-4.4-base cpp-4.4 libpython2.7 libasound2 libgif4 libogg0 libflac8 libvorbis0a libvorbisenc2 libsndfile1 libxcb-atom1 libxtst6 libpulse0 libgtk2.0-common libjasper1 libgdk-pixbuf2.0-0 shared-mime-info libgtk2.0-0 libaccess-bridge-java-jni openjdk-6-jre default-jre libaccess-bridge-java openjdk-6-jdk

```

---

### Post by wcorey on 2011-04-30
This is grim. Upgrade in place does not (or did not) successfully work.

I cut a CD and installed from it. The install from CD went fine and at reboot time all I received was a fast blinking on the console. The system will not boot, will not even start boot. I am re-installing as we all know from web-dude vs, sales-guy we have to install 3 times.

I, honestly, did not think I would need a running commentary on this but, I am on my 3rd try to install this and I have zero hope this will work. It is looking a lot like 11.04 Natty was not completely done cooking before they released it. Specifically, I have RAID1 configured on a Dell XPS 8100. This posed no problem for prior versions but, I think this is an issue with 11.04. In this last attempt I removed the RAID array through bios and recreated it. This shouldn't have mattered. In attempt 1 I selected use entire disk and install LVM. In attempt 2 I said use entire disk (no and install lvm).In both attempts I did notice something I hadn't noticed in earlier installs of previous versions of Ubuntu, it referred to installing on volume whatever (Mirror), specifically the mirror part I don't remember. I concluded, perhaps wrongly, that perhaps the install program was seeing the mirrored half of the raid volume not the 2 physical volumes as a single volume. I thought if I recreate the entire thing from scratch it would have a clean surface to install against. 

Now I am on installation try #4. Here is a warning I saw before which may be pertinent, partd was unable to reread the partition table on /dev/mapper/stuff)Volume0 (no such file or directory). The volume 0 is the RAID volume I created through bios. This means Linux won't know anything about the modifications you made. That would be the changes IT just made. Well this sucks!!!! BTW, 10.10 installed just fine. 

I did a backup and displayed the Partition disks screen

Unallocated physical volumes:
* none

Volume Groups
* cor9100  <- that is the name of the server
Uses physical volume:           /dev/dm-2       (749859MB)
- provides logical volume       root            (749895MB)
- provides logical volume       swap_1          (6434MB)

So this screen seems to be seeing it OK, One would hope it actually read it instead of guessing.

so I will press continue then select Finish.
On the second screen for Partition disks

LVM VG cor9100 LV root - 743.5GB Linux device-mapper (linear)
#1    743.5GB    ext4
LVM VG cor9100 LV swap_1-6.4GB Linux device-mapper (linear)
#1     6.4GB   F  swap  swap

Serial ATA RAID isw_blahblah_Volume0 (mirror - 750.2 GB Linux device-mapper (mirror)
#1   primary  254MB F ext2 /boot
#5   logical  749.9GB K lvm

After selecting Finish partitioning and write changes to disk I get a red screen saying no root file system.

So I muffed around and defined #1 above as / (root). It used to be in previous releases when it did the formatting it took maybe 20 seconds, certainly long enough for you to see the screen title was formatting disk. Now it just zips though in about 1/2 sec.

Now it is "Installing the base system"...of course it has been here 3 times before in this odyssey. Oh, in the previous attempt, after I deleted and recreated the RAID volume it, at one screen, warned that it was seeing files from a previous install and they might cause problems...Wait...I recreated the volume, how is it seeing things from a previous install??

It could just be me wishful thinking but it seems like the disk IO is louder than it was before. 

Nope...no joy...just the fast blinking cursor....Maybe it was grub didn't install correctly. That was the last step when it said it was installing to sda master boot record. So, short of someone having a solution, Monday I will bring my 10.10 disk home from work and reinstall it.

---

### Post by wcorey on 2011-04-30
Come to think of it, this is erringly similar to another thread I opened trying to install, that aforementioned 10.10 server, on the Dell Power Edge T410 at work. It installed just fine but upon reboot, I just got the fast blinking cursor and no bootup or error about not being able to boot up. Note: on the T410 there is no raid. 

This looks an awful lot like a bug.

---

### Post by wcorey on 2011-04-30
I found this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/745960](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/745960)

---

### Post by wcorey on 2011-04-30
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for dbh.
 => Syslinux is installed in the MBR of /dev/sdf
 => Grub 2 is installed in the MBR of /dev/mapper/isw_cdbgicafgh_Volume0 and 
    looks on the same drive in partition #1 for dbh.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

isw_cdbgicafgh_Volume01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cdbgicafgh_Volume02: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_cdbgicafgh_Volume05: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758 1,465,143,295 1,464,641,538   5 Extended
/dev/sda5             501,760 1,465,143,295 1,464,641,536  8e Linux LVM


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4022 MB, 4022337536 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             62     7,849,447     7,849,386   c W95 FAT32 (LBA)


Drive: isw_cdbgicafgh_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_cdbgicafgh_Volume0: 750.2 GB, 750153502720 bytes
255 heads, 63 sectors/track, 91200 cylinders, total 1465143560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cdbgicafgh_Volume01   *          2,048       499,711       497,664  83 Linux
/dev/mapper/isw_cdbgicafgh_Volume02            501,758 1,465,143,295 1,464,641,538   5 Extended
/dev/mapper/isw_cdbgicafgh_Volume05            501,760 1,465,143,295 1,464,641,536  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e6919f2c-a855-4f4d-8cc3-21be66621881   ext3                                     
/dev/mapper/isw_cdbgicafgh_Volume0p1 iKlz25-f5ef-0fsB-hY1b-ecrq-DeJP-wK6PXs LVM2_member                               
/dev/mapper/isw_cdbgicafgh_Volume0p5 FLnB73-oYYS-asW7-Zcy4-Qgu6-gSxX-BblZZM LVM2_member                               
/dev/mapper/isw_cdbgicafgh_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdf1        D749-9833                              vfat                                     
/dev/sdf: PTTYPE="dos" 
/dev/sdg                                                isw_raid_member                               
error: /dev/mapper/isw_cdbgicafgh_Volume01: No such file or directory
error: /dev/mapper/isw_cdbgicafgh_Volume02: No such file or directory
error: /dev/mapper/isw_cdbgicafgh_Volume05: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cdbgicafgh_Volume0
isw_cdbgicafgh_Volume0p1
isw_cdbgicafgh_Volume0p5

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdf1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdf1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sdf1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  aa c5 77 00 e3 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 33 98 49 d7 20  20 20 20 20 20 20 20 20  |..)3.I.         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 de 0b 16 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on isw_cdbgicafgh_Volume01


Unknown BootLoader  on isw_cdbgicafgh_Volume02


Unknown BootLoader  on isw_cdbgicafgh_Volume05



=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/mapper/isw_cdbgicafgh_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cdbgicafgh_Volume01: No such file or directory
hexdump: /dev/mapper/isw_cdbgicafgh_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cdbgicafgh_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cdbgicafgh_Volume05: No such file or directory
hexdump: /dev/mapper/isw_cdbgicafgh_Volume05: No such file or directory
```

Not sure what  to do with this.

---

### Post by ronparent on 2011-05-01
Rubi1200 asked that I look at this thread and offer suggestions. I admit I am not familiar with LVM but that doesn't appear to be the problem.

I note two problems but one big discrepancy - a list of the links shows one convention, the Results.txt list of partitions shows another? 
ie
> control
isw_cdbgicafgh_Volume0
isw_cdbgicafgh_Volume0p1
isw_cdbgicafgh_Volume0p5
In other words there is no filesystem associated with 'isw_cdbgicafgh_Volume01', it is associated with 'isw_cdbgicafgh_Volume0p1'. In effect, from a live cd, you should be able to mount the latter but the former doesn't exist.

I can't imagine how this came about. I thought dmraid dropped the naming convention that appended a 'p' to the partition designation after a short trial. Is it possible that the partition tags with a 'p' were written to the disks meta data with a transitory version of dmraid? In any case it appears you are installed to 'isw_cdbgicafgh_Volume0p1' (at least from the system you ran the script for the results.txt). 
_____________________________________________________

After mulling your situation over this is what I concluded. Dmraid merely discovers the partition tags written to disk meta data -  so the tags were written there when partitioned and are incompatible with 11.04. I think perhaps you need to repartition with gparted with an 11.04 live cd and verify that the convention appending a 'p' to the partition tags is not used. Also for the second problem I started with, for a fakeraid you need to install the grub boot loader to '/dev/mapper/isw_cdbgicafgh_Volume0' not sda. You do currently have a grub bootloader at that location but it is looking in the wrong partition notation for the grub.

I hope this helps. Let us know what you find.

---

### Post by wcorey on 2011-05-01
Thank you for looking into that Ron.

I am, once again, perplexed. I must have tried to install that seven times. I ended up removing the 2 drives from RAID in the bios and tried installing software raid. I am not sure that went correctly either but at least it boots now. As for remnants from an earlier release, I did remove the raid configuration, and reset it to raid0 (to try that), I changed the name from Array0 to Volume0 (which is where it is where you see it) and back to Array0). I've deleted in the install program partitions etc and redefined them. I would have thought any and all of those actions would remove remnants of prior versions. Is it possible it is a bug in the install program? When I dropped 10.10 UEC server in it installed flawlessly AND booted. These issues are unique to 11.04. Again, initially that RAID volume was called Array0, the Volume0 (without the p) was done post trying to install 11.04. While I am sensitive to issue creep, when I did try the software raid in the install process I did get a new screen asking effectively how I wanted the ram disk created, targeted to just the drivers it needed or the full install, where the full install might be too large to get loaded. Would that, or the previous absence of that, have any bearing on this issue?

Thanks,

Walt

---

### Post by ronparent on 2011-05-01
Just note that turning off the raid doesn't erase the meta data on the drives. If you are not going to use the fakeraid you should also erase the raid meta data.
ie
> sudo dmraid -rE /dev/sda
etc for each drive

Uninstalling dmraid accomplishes much the same thing except that the meta data remains on the HD and will likely haunt you in the future when the drive history is a vague memory!

---

### Post by wcorey on 2011-05-01
My point was that when I initially tried to install 11.04 the raid was called Array0. It was changed to Volume0 when, on my Nth attempt I changed from RAID1 to RAID0 and the bios changed the name from Array0 to Volume0. So anything resembling Volume0 was a product of my, perhaps, 5th attempt. This is when I found the reference to the bootinfoscript and produced the output you refer to. Consequently, doesn't it seem likely to you then that that suffix of 'p' was put there by the installer I did find a reference after your prior post on dmraid in its changelog that a typo was fixed. It didn't say what. Again, this worked fine in 10.10. Let me ask you something, are you just a superuser type or do you work in the code for raid soft or hard? The other thing, by way of trying to determine where the problem lives, last night, just for S & G, I installed Fedora 13 on it as firmware raid1. It not only installed cleanly, it booted. U10.10 installs cleanly and booted.  So is there any reason I should doubt this is a bug in the U 11.04 installer/dmraid component? I suppose I could bring the install disk for 10.10 home from work tomorrow, reinstall it and do another bootinfo. If there is no reference to Volume0p, I think we've found the smoking gun...right?

And, again, thanks for your insight on this. Clearly this is not an area of Linux I am, um, well versed in.
Walt

---

### Post by ronparent on 2011-05-02
> doesn't it seem likely to you then that that suffix of 'p' was put there by the installer
All I can say is that this has not been my experience with the 11.04 64 bit desktop release!

My experience with FakeRAID has been acquired by using it and coping with various behaviors since 7.04. In my particular case 11.04 has been the best implemented yet, after some serious initial failures. I've been able to upgrade and do fresh installs of this version to a raid0 with no problems. That is not to say that no problems exist over the whole gamut of hardware it might be used on, only that I am not finding your problems on my own setup.

What makes what you relate puzzling is that it shouldn't matter how the partitions are named. Dmraid should discover them and load the symbolic links at /dev/mapper to enable accessing the operative file system. I don't see why the inconsistencies in naming show up in the Results.txt? Since I haven't used the 11.04 server there could be a problem specific to that release. 

If you do want to investigate the problem more thoroughly I could acquire the 11.04 server release and try installing it from scratch. What do you think?

---

### Post by wcorey on 2011-05-08
> **ronparent said:**
> All I can say is that this has not been my experience with the 11.04 64 bit desktop release!

If you do want to investigate the problem more thoroughly I could acquire the 11.04 server release and try installing it from scratch. What do you think?

Sorry for the delay Ron. I spent last week at RedHat Summit. I did try installing 11.04 desktop (from thumb drive) on that box. Again, the install went flawlessly but the reboot didn't. However, Fedora 13 installed flawlessly on it AND booted.To be sure there is that bug, verified, on Launchpad that, as written, deals with encrypted LVM. There are lots of forum threads dealing with not being able to reboot after installing 11.04. I think where there is smoke...

I would be more willing to say I must have screwed something up if it weren't for the fact I tried 6 or 7 times before I bagged LVM and it worked. I would try it again except I have zero confidence the outcome would be any different. Oh, and I did find a changelog referring to a typo in grub or that area...it didn't elaborate but could it be a 'p' suffix? As they say, what's the definition of insanity, doing the same thing over and over expecting a different outcome.

So if you have the time and interest RAID1 across 2 volumes, Oh, the other thing is the message I referenced above somewhere about gparted failing to write the changes with a reason of 'file not found'. The user doesn't give it a file name so that looks like its a bug.

Walt

ps..

See reason for editing. 
I tried it yet once again, and specified isw_asdjhsdjhjeucuueu_Array0 as the target for grub2. Damn if it didn't work. But, I've never done that before. In fact while I was trying it for the second time today, I checked my desktop system and gparted and disk utility showed 2 different things. This is df -h

walt@cor720:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/cor720-root
                      450G  278G  150G  65% /
none                  3.9G  284K  3.9G   1% /dev
none                  4.0G  1.3M  4.0G   1% /dev/shm
none                  4.0G  168K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
/dev/mapper/nvidia_efaaadhd5
                      236M  152M   72M  68% /boot
gparted shows /dev/mapper/didhdifheihrihirh but with hd1 and hd2 appended on the end. Note above the main drive is /dev/mapper/machine-name hyphen root. On the other machine it now is /dev/mapper/cor9100-root and the boot partition is

/dev/mapper/dfkdkdhkhfi_Array0p1 so it does have the p1 suffix. . In fact, in times past during upgrade I've gotten the curses box asking did I want to install it on sda1 or sdb1 and if I didn't know, select both. So how is one to know to specify /dev/mapper/isw_dkhdkfhdkfjkj_Array0? I never would have guessed that.


Once the

---

### Post by wcorey on 2011-05-21
I am marking this bug unsolved. In the previous message the installer gave a choice of where to install grub. My issue was not realizing where the proper place was. Once Ron made me aware of that it did install on that machine. However, on it's sister server the CD doesn't give me an option of where it is installing grub. It is the same fricking CD. This is a SERIOUS REGRESSION by Canonical. Microsoft can install properly on firmware RAID, as can Fedora. Historically Ubuntu for some reason didn't know how or was too denegrading by referring to it as FAKE raid. Oh, and a software version wasn't equally 'FAKE'? In prior questions on how-to install, the answers have been why would you possibly want to... It's enough that they did want to. Then Canonical decided they would do it but only begrudgingly and you'd have to install off another type of CD. Eventually they added the intelligence that Microsoft, Fedora, and, likely, all the other distros used in their base installer to graciously install on the hardware present. 
Apparently not any more. 

The insult to injury is if you bypass the failure and 'Continue without Bootloader' it properly tells you what you need to boot off of, that being /dev/mapper/some sequence_Array0. So why didn't the person who wrote that logic decide maybe that's where grub should be as well?

I think the question now is becoming how to boot into this such that I can manually run grub-install /dev/mapper/...._Array0?

I apologize for the rant...it is just irritating when something that works gets broken and not immediately fixed.:confused:

---

