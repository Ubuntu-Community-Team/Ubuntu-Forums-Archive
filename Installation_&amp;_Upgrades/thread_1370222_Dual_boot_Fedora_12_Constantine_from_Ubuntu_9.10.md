---
title: "Dual boot Fedora 12 Constantine from Ubuntu 9.10"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by austeze on 2010-01-02
After much searching I was unable to find any information on dual booting Fedora 12 from Ubuntu 9.10. Here is how I got it to work:

If you are installing both distributions it is recommended that you install Fedora 12 first, then Ubuntu. It may be possible to chainload Ubuntu's bootloader (grub2) from Fedora 12's (legacy grub), although I haven't tested to confirm if this works. (If it works for you please reply).

Once you are done installing both distributions, boot Ubuntu and open a terminal (Applications -> Accessories -> Terminal).

When you are in the terminal type:
*"sudo blkid /dev/xxx*", where xxx is the root partition of Fedora 12.

If you specified a sepearate /boot partition, then you will need the UID of that partition as well.

You will recieve output that appears much like:
[I]austin@ubuntu:/$ sudo blkid /dev/sda1
/dev/sda1: LABEL="Fedora Boot" UUID="e7cd142b-1fb7-4c34-8a2b-b00dd8e7f081" TYPE="ext3"[/I]

Copy down the UID from the "UUID=" field (without quotes). For example, from the output above, the UID of my Fedora 12 boot partition is *e7cd142b-1fb7-4c34-8a2b-b00dd8e7f081.*

Next, type the command:
*sudo nano /etc/grub.d/40_custom*

Copy and paste this at the end of the file:

[I]menuentry "Fedora 12 Constantine" {
    insmod ext2
    set root=(hd0,<x>)
    search --no-floppy --fs-uuid --set <uid>
    linux /vmlinuz-2.6.31.9-174.fc12.i686.PAE ro root=UUID=<uid> LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.9-174.fc12.i686.PAE.img
}[/I]

On the line "*set root=*" replace <x> to the number of your root (or /boot) partition. For example, if your Fedora 12 has a /boot partition on /dev/sda1, your "root=" line will be: "*set root=(hd0,2)*".

Next, replace "<uid>" on the line "*search --no-floppy"* with the UID that you copied down before by issuing the *blkid* command. If you have a seperate /boot partition, this is where your UID for the /boot partition goes. If you do not have a seperate /boot partition, the UID is simply that of your root partition.

Below that line you will see the *"linux" and "initrd"* lines. At the time of writing this is the current kernel and initrd versions for Fedora 12. You may want to verify this. Ubuntu will automount your Fedora 12 partitions, so just simply navigate to your /boot directory on your Fedora 12 partition and verify that these are the correct filenames to boot.

On the "*linux*" line you will see "*root=UUID="*, replace <uid> with the UID you copied from the command *blkid* for your root partition. If you do not have a seperate /boot partition, this is the same UID from the "*search --no-floppy*" line.

Press CTRL+x and answer Yes to save.

You will be back in the terminal prompt. Type the commands:
[I]sudo chmod 666 /boot/grub/grub.cfg
sudo grub-mkconfig > /boot/grub/grub.cfg
sudo chmod 444 /boot/grub/grub.cfg[/I]

Your output will appear as follows:
[I]austin@ubuntu:/$ sudo chmod 666 /boot/grub/grub.cfg
austin@ubuntu:/$ sudo grub-mkconfig > /boot/grub/grub.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
austin@ubuntu:/$ sudo chmod 444 /boot/grub/grub.cfg

[/I]Reboot your machine.

You will now be able to boot either Ubuntu 9.10 or Fedora 12.

---

### Post by Setarkos on 2010-01-10
> **austeze said:**
> You will now be able to boot either Ubuntu 9.10 or Fedora 12.

Would you say that works with Win7, Linux Mint 8 and Fedora 12? With Win7 installed at first and then as you wrote?

---

### Post by nvinicio on 2010-02-04
Hi all
I would like to have a 3-boots, Windows, Fedora and Ubuntu 
Windows and Fedora work well at boot time, I don't know how to boot Fedora!!
Here is my situation on my computer


# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31613160

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        6454    31358880   83  Linux
/dev/sda3   *        6455        6480      204800   83  Linux
/dev/sda4            6481       19457   104237752+   5  Extended
/dev/sda5            6481       19457   104237056   8e  Linux LVM






# blkid /dev/sda5
/dev/sda5: UUID="vJ1tp6-QTGm-3wih-vVl3-dpe7-Zt2n-fmvc8d" TYPE="LVM2_member" 




menuentry "Fedora 12 Constantine" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set vJ1tp6-QTGm-3wih-vVl3-dpe7-Zt2n-fmvc8d
    linux /vmlinuz-2.6.31.9-174.fc12.i686.PAE ro root=UUID=vJ1tp6-QTGm-3wih-vVl3-dpe7-Zt2n-fmvc8d LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.9-174.fc12.i686.PAE.img
}




but doesn't work!!!!!!!!!!!!!
what is wrong? 

thanks

---

### Post by oldfred on 2010-02-04
/dev/sda5
set root=(hd0,6)
Should not that be (hd0,5) ? I do not even see a sda6.

---

### Post by paintonhisface on 2010-02-05
Hi.  Installed Fedora 12 on the first two partitions (sda1,sda2) and I think I had it install legacy grub to the MBR.  I've tried adding it the way that you say, but it still boots straight to Ubuntu.  Here's the output of fdisk:
```
Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x426a426a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        7038    56320000   8e  Linux LVM
/dev/sda3            7039       14098    56709450   83  Linux
/dev/sda4           14099       14596     4000185   82  Linux swap / Solaris

```
Here's my 40 custom file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 12 Constantine" {
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 508237f6-b873-491d-a762-758a71075034
linux /vmlinuz-2.6.31.5-127.fc12.x86_64.PAE ro root=UUID=9ixnBC-vT78-EpWL-Sb4N-sU2E-2ZYa-JIonxl LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}
```
Any ideas?

---

### Post by Coge on 2010-03-17
Try *sudo update-grub*

---

### Post by andrewthomas on 2010-03-23
> **paintonhisface said:**
> Hi.  Installed Fedora 12 on the first two partitions (sda1,sda2) and I think I had it install legacy grub to the MBR.  I've tried adding it the way that you say, but it still boots straight to Ubuntu.  Here's the output of fdisk:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 12 Constantine" {
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 508237f6-b873-491d-a762-758a71075034
linux /vmlinuz-2.6.31.5-127.fc12.x86_64.PAE ro root=UUID=9ixnBC-vT78-EpWL-Sb4N-sU2E-2ZYa-JIonxl LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}
```Any ideas?From [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> General **menuentry** Construction  Rules: 

[LIST]
[*]The first line must start with **menuentry**  and end with **{**
[*]The area between the quotation symbols  is what will appear on the GRUB 2 menu. Edit as desired.
[*]The last  line of the *menuentry* must be **}**
[*]Do ***not***  leave empty spaces at the end of lines
[*]**The *set root=*  line should point to the GRUB 2 /boot location** ( sd**XY** )
[*]The *root* reference in in the *linux*  line should point to the system partition.
[LIST]
[*]If GRUB 2 cannot find the referenced  kernel, try replacing the UUID with the device name (example: /dev/sda6  ).
[/LIST]
 
[/LIST]
Your Fedora /boot location seems to be **sda1**, so your **set root=(hd0,2)** line should probably be **set root=(hd0,1)**.
If you are still having problems,
post the output of this in your next reply.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by SkyNet2029 on 2010-04-10
Interesting post. This method is far too complex methinks.
One could simply install Ubuntu 9.10 or 10.04 FIRST.
Install Fedora 12 and specifying to install the Fedora bootloader to the first sector of the 
(Fedora) /boot partition.

Reboot. You will now be back at your standard Ubuntu grub screen, with NO option to boot
into Fedora install. This is fine and what we want.
Boot into Ubuntu.
Fire up a terminal and do:

```
$sudo grub-mkconfig /dev/sdX
```
where X is your primary drive.
This command will generate plenty of output on the terminal. No worries, as again..
this is what we want. Now do:
```
$sudo update-grub
```
You will notice grub finds your Fedora installation and adds it to your boot menu.
Sweet!
Very easy and fast.
I think this is actually proper way to do this, as it utilizes built-in Grub commands to force grub to 
remap the partition records, and then regenerates a proper grub boot menu.

Hope this helps and no disrespect meant to OP, just thought this was a little easier.

Cheers!

---

### Post by andrewthomas on 2010-04-27
With the release of os-prober 1.37, Fedora is now unconditionally picked up.  

[https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/549300](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/549300)

---

### Post by Aravind_1729 on 2010-05-08
I just installed ubuntu 10.04
I had ubuntu 9.04 before. I removed it and in that space I installed 10.04

This is the ouput of sudo fdisk -l command in my Laptop

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97659073    5  Extended
/dev/sda2   *       12159       16560    35355648   83  Linux
/dev/sda3           16560       17046     3905536   82  Linux swap / Solaris
/dev/sda4           17047       19457    19366357+  8e  Linux LVM
/dev/sda5               1       12158    97659072    b  W95 FAT32

I am not seeing the boot menu (to switch between Fedora and Ubuntu) at the beginning. It is directly entering into Ubuntu 10.04

Even though I have been using Ubuntu for 2-3 years now, my knowledge is limited. I tried everything. I think I made some basic mistake while editing the partition table manually. 

Can anyone please help me in solving this problem.

---

### Post by Aravind_1729 on 2010-05-10
Continuation of this [link]("http://ubuntuforums.org/showthread.php?t=1370222")


After installing lvm2 package , I was able to see the fedora partition. But still its not coming in the boot menu

---

### Post by andrewthomas on 2010-05-11
post the output of this in your next reply.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tron101 on 2010-05-11
Hi,

I hope you won't mind my jumping in.

I have the same problem and ran the script and attach the relevant file.

Very grateful for any thoughts/pointers!

Best

[HTML]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 122900994 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /grub/grub.conf.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda4: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   122,882,047   122,880,000  83 Linux
/dev/sda2         228,501,502   234,440,703     5,939,202   5 Extended
/dev/sda5         228,501,504   234,440,703     5,939,200  82 Linux swap / Solaris
/dev/sda3    *    122,882,048   123,291,647       409,600  83 Linux
/dev/sda4         123,291,648   228,499,455   105,207,808  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c704d982-a91b-4a8e-9fdc-db953acd6636   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        664cf91f-8377-49ab-80ba-4f6fdd7697cb   ext4                                     
/dev/sda4        Es3PG4-Ikmz-qlYr-OA3L-bc1j-wEIk-O7DoLR LVM2_member                               
/dev/sda5        c5b975c7-c0c3-47b1-be5e-56e5bf93fd12   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c704d982-a91b-4a8e-9fdc-db953acd6636
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c704d982-a91b-4a8e-9fdc-db953acd6636
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c704d982-a91b-4a8e-9fdc-db953acd6636
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c704d982-a91b-4a8e-9fdc-db953acd6636 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c704d982-a91b-4a8e-9fdc-db953acd6636
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c704d982-a91b-4a8e-9fdc-db953acd6636 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c704d982-a91b-4a8e-9fdc-db953acd6636
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c704d982-a91b-4a8e-9fdc-db953acd6636
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c704d982-a91b-4a8e-9fdc-db953acd6636 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5b975c7-c0c3-47b1-be5e-56e5bf93fd12 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  19.7GB: boot/grub/core.img
  19.7GB: boot/grub/grub.cfg
  19.7GB: boot/initrd.img-2.6.32-21-generic
  19.6GB: boot/vmlinuz-2.6.32-21-generic
  19.7GB: initrd.img
  19.6GB: vmlinuz

============================= sda3/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_john-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda3
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.5-127.fc12.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.31.5-127.fc12.i686 ro root=/dev/mapper/vg_john-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.5-127.fc12.i686.img

=================== sda3: Location of files loaded by Grub: ===================


  62.9GB: grub/grub.conf
  62.9GB: grub/menu.lst
  62.9GB: grub/stage2
  62.9GB: initramfs-2.6.31.5-127.fc12.i686.img
  62.9GB: vmlinuz-2.6.31.5-127.fc12.i686
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  32 39 20 32 32 3a 35 34  3a 30 37 20 73 74 61 74  |29 22:54:07 stat|
00000010  75 73 20 68 61 6c 66 2d  69 6e 73 74 61 6c 6c 65  |us half-installe|
00000020  64 20 6c 6f 63 6b 66 69  6c 65 2d 70 72 6f 67 73  |d lockfile-progs|
00000030  20 30 2e 31 2e 31 31 75  62 75 6e 74 75 32 0a 32  | 0.1.11ubuntu2.2|
00000040  30 30 38 2d 31 30 2d 32  39 20 32 32 3a 35 34 3a  |008-10-29 22:54:|
00000050  30 37 20 73 74 61 74 75  73 20 75 6e 70 61 63 6b  |07 status unpack|
00000060  65 64 20 6c 6f 63 6b 66  69 6c 65 2d 70 72 6f 67  |ed lockfile-prog|
00000070  73 20 30 2e 31 2e 31 31  75 62 75 6e 74 75 32 0a  |s 0.1.11ubuntu2.|
00000080  32 30 30 38 2d 31 30 2d  32 39 20 32 32 3a 35 34  |2008-10-29 22:54|
00000090  3a 30 37 20 73 74 61 74  75 73 20 75 6e 70 61 63  |:07 status unpac|
000000a0  6b 65 64 20 6c 6f 63 6b  66 69 6c 65 2d 70 72 6f  |ked lockfile-pro|
000000b0  67 73 20 30 2e 31 2e 31  31 75 62 75 6e 74 75 32  |gs 0.1.11ubuntu2|
000000c0  0a 32 30 30 38 2d 31 30  2d 32 39 20 32 32 3a 35  |.2008-10-29 22:5|
000000d0  34 3a 30 37 20 69 6e 73  74 61 6c 6c 20 6c 73 62  |4:07 install lsb|
000000e0  2d 72 65 6c 65 61 73 65  20 3c 6e 6f 6e 65 3e 20  |-release <none> |
000000f0  33 2e 32 2d 31 34 75 62  75 6e 74 75 32 0a 32 30  |3.2-14ubuntu2.20|
00000100  30 38 2d 31 30 2d 32 39  20 32 32 3a 35 34 3a 30  |08-10-29 22:54:0|
00000110  37 20 73 74 61 74 75 73  20 68 61 6c 66 2d 69 6e  |7 status half-in|
00000120  73 74 61 6c 6c 65 64 20  6c 73 62 2d 72 65 6c 65  |stalled lsb-rele|
00000130  61 73 65 20 33 2e 32 2d  31 34 75 62 75 6e 74 75  |ase 3.2-14ubuntu|
00000140  32 0a 32 30 30 38 2d 31  30 2d 32 39 20 32 32 3a  |2.2008-10-29 22:|
00000150  35 34 3a 30 37 20 73 74  61 74 75 73 20 75 6e 70  |54:07 status unp|
00000160  61 63 6b 65 64 20 6c 73  62 2d 72 65 6c 65 61 73  |acked lsb-releas|
00000170  65 20 33 2e 32 2d 31 34  75 62 75 6e 74 75 32 0a  |e 3.2-14ubuntu2.|
00000180  32 30 30 38 2d 31 30 2d  32 39 20 32 32 3a 35 34  |2008-10-29 22:54|
00000190  3a 30 37 20 73 74 61 74  75 73 20 75 6e 70 61 63  |:07 status unpac|
000001a0  6b 65 64 20 6c 73 62 2d  72 65 6c 65 61 73 65 20  |ked lsb-release |
000001b0  33 2e 32 2d 31 34 75 62  75 6e 74 75 32 0a 00 fe  |3.2-14ubuntu2...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 5a 00 00 00  |............Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[/HTML]

---

### Post by andrewthomas on 2010-05-16
@tron101
add the following menuentry to your /etc/grub.d/40_custom 
```
gksudo gedit /etc/grub.d/40_custom
```and add to the bottom
```
menuentry "chainload Fedora on sda3" {
set root='(hd0,3)'
chainloader +1
}
```then```
 sudo update-grub
```

---

### Post by tron101 on 2010-05-17
Andrew

Many thanks for looking at this- unfortunately it hasn't worked. I've checked the 40_custom file to make sure I saved the changes, and they are there.

Happy to post the output from bootinfoscript again if that would help.

Best

---

### Post by tron101 on 2010-05-26
Bump

---

### Post by oldfred on 2010-05-26
For a chainload entry to work you have to have installed Fedora's grub to the Fedora partition.

You should be able to do that with the Fedora disk just like Ubuntu but instead of sda you specify sda4. not sure what differences a LVM makes. You may have to mount it differently.

---

### Post by Emmtor on 2010-09-06
Hello everyone,

I have 2 hard drive devices, sda and sdb
My aim is to dual boot ubuntu 9.10 and fedora 13. I initially had ubuntu 9.10 on my machine installed on my sdb hard disc.My sda hard disc was formatted to ext3 but it was unmounted. I then used the fedora live cd to install fedora to my whole sda hard drive. Contrary to what i thought would happen, i booted to fedora. I can't boot into ubuntu now, no matter which of the hard drives i choose to boot from (in the boot menu, which i enter by pressing F9 during system boot). All my files in sdb are still there. I probably misread the instructions given by a fellow poster of this thread, (skynet2029 he/she is), by skipping the 'specifying to install the Fedora bootloader to the first sector of the Fedora /boot partition' step.

Any ideas?
I am attaching a screenshot of the output of my fdisk -l terminal command.

Thanks, Emmtor

---

