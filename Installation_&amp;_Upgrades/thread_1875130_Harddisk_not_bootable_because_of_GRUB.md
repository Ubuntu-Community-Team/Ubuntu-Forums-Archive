---
title: "Harddisk not bootable because of GRUB?"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by qwyrp on 2011-11-04
I've a I3-2100, motherboard DH67CF (B3) and 2TB Samsung HDD.
When I install Windows 7 it will boot but whenever I install Ubuntu is stated that the decive isn't bootable. So it looks to me like GRUB isn't recognizable by the BIOS. How is that possible what am I doing wrong?

---

### Post by raja.genupula on 2011-11-04
Hi man ....what error actually you're getting ? you said its not booting , so make sure about boot order in the BIOS settings.is your system directly booting into other OS with out asking you to choose.then hold shift key while your system booting to get the grub menu.

---

### Post by qwyrp on 2011-11-04
When Windows 7 was installed it was directly and correctly starting Windows. 
After (several) installations of Ubuntu the error was REBOOT AND SELECT 
PROPER BOOT DEVICE OR INSERT BOOT MEDIA IN SELECTED DEVICE AND PRESS A KEY.
When UEFI was enabled the error was A BOOTABLE DEVICE AND HAS NOT BEEN 
DETECTED SEE INTEl-url
Only one device (HDD) was selected/activated in the boot priority

Ubuntu was the only OS on the disk so therefor holding the SHIFT-key won't help 
me I think because it stated the disk isn't bootable

---

### Post by qwyrp on 2011-11-04
After several test and reruns are here some additions:
[LIST]
[*]USB with LiveCD also don't start up
[*]When pressing F10 (bootmenu) during booting I can select a device and when I select the USB stick or even the harddisk it started correctly
[/LIST]
I'm complety suprised :confused: and don't know what to do now..... help !!!

---

### Post by darkod on 2011-11-04
I can't help much, but I can point you in a direction I think is correct. I think it's because of the UEFI boot. Investigate more about booting ubuntu with UEFI and where actually you need to install grub2. I have no experience with that unfortunately.

If it was MBR boot I'm sure it would have worked straight away.

---

### Post by oldfred on 2011-11-04
If using UEFI, you have to have a FAT efi partition with the efi boot loaders. That partition has to be first. Windows then creates its own additional boot partition. If Windows is installed first, there are issues as grub creates a new efi partition and overwrites the windows boot. With UEFI it is better to install Ubuntu first, then Windows which is just the opposite of BIOS boot suggested procedures. You can also back up the Windows boot files in the efi partition and restore after grub installs.

If using BIOS boot, may Intel motherboards need a boot flag. Grub/Linux does not use boot flag, so a partition does not have the boot flag. You can add a boot flag to any primary partition and then it will work.

You can post boot script, but it does not parse efi partition to see if boot files are there.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

---

### Post by qwyrp on 2011-11-04
Mmmm looks interesting but first I look at the bootflag. Is there a command or a program to set this bootflag?

---

### Post by oldfred on 2011-11-04
If your first partition is not a FAT efi partition, then you are in BIOS mode.But in BIOS mode Windows does create a hidden 100MB boot partition NTFS. Vendors also  may create a larger FAT partition for a vendor recovery set of DVDs to restore system. So you need to review partitions to see how they are set up. Windows will only boot UEFI with gpt partitioning, not MBR(msdos). Ubuntu can boot UEFI or BIOS from gpt type partitioning.

Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.

You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
OR:
    #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

You can also make an active NTFS partition with Windows which will be the boot partition for a Windows install.

---

### Post by qwyrp on 2011-11-04
Wow, I definitely need your help because this way above my head. Hereby the code your asked for. 
I only want one OS (Ubuntu 10.01 Server 64bit)
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    2048 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,gpt2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2's core.img
    Boot sector info:  
    Mounting failed:   mount: onbekende bestandssysteemsoort '' //Translation: unknown filesystem

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Schijf /dev/sda: 2000.4 GB, 2000398934016 bytes
255 koppen, 63 sectoren/spoor, 243201 cilinders, totaal 3907029168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 EFI System partition
/dev/sda2           4,096 3,859,574,783 3,859,570,688 Data partition (Windows/Linux)
/dev/sda3   3,859,574,784 3,907,028,991    47,454,208 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        867b92d8-544a-4f6d-ab48-0b3346db05fe   ext4       
/dev/sda3        eeb72a9e-fa3a-492e-a390-6583449ad22d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 867b92d8-544a-4f6d-ab48-0b3346db05fe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 867b92d8-544a-4f6d-ab48-0b3346db05fe
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 867b92d8-544a-4f6d-ab48-0b3346db05fe
	linux	/boot/vmlinuz-2.6.35-22-server root=UUID=867b92d8-544a-4f6d-ab48-0b3346db05fe ro   quiet
	initrd	/boot/initrd.img-2.6.35-22-server
}
menuentry 'Ubuntu, with Linux 2.6.35-22-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 867b92d8-544a-4f6d-ab48-0b3346db05fe
	echo	'Loading Linux 2.6.35-22-server ...'
	linux	/boot/vmlinuz-2.6.35-22-server root=UUID=867b92d8-544a-4f6d-ab48-0b3346db05fe ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 867b92d8-544a-4f6d-ab48-0b3346db05fe
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 867b92d8-544a-4f6d-ab48-0b3346db05fe
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=867b92d8-544a-4f6d-ab48-0b3346db05fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=eeb72a9e-fa3a-492e-a390-6583449ad22d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 640.135864258 = 687.340650496  boot/grub/core.img                             1
 796.196514130 = 854.909497344  boot/grub/grub.cfg                             1
   0.273323059 = 0.293478400    boot/initrd.img-2.6.35-22-server               2
 640.133365631 = 687.337967616  boot/vmlinuz-2.6.35-22-server                  1
   0.273323059 = 0.293478400    initrd.img                                     2
 640.133365631 = 687.337967616  vmlinuz                                        1



```

---

### Post by darkod on 2011-11-04
I will let oldfred continue, just to add this. If you want only Ubuntu Server on this system, and as a clean install (that would mean no data to back up), I would rather delete this partition table and create a msdos one. If I remember correctly it can work for up to 2TB disks like yours.
Much less complicated than GPT and UEFI.

Also in your place I would investigate the option of installing as LVM on such a big disk and with ubuntu being the only OS. Gives great flexibility for partitions resizing on the fly.

---

### Post by qwyrp on 2011-11-04
@darkod: thank you for your tips and I'll keep them in mind but first I'm letting oldfred lead the way !!

---

### Post by oldfred on 2011-11-04
Do these commands show anything?
If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"     

It looks more like you have BIOS boot and the first partition is mis-labled. It says efi, but efi has to have a FAT format and it has none. In BIOS boot you need a bios_grub partition to have a place for core.img which is in sda1. And a bios_grub partition has no format.

I now prefer gpt, but with MBR you cannot put Windows on the drive. Windows will only boot with UEFI on a gpt drive. As Darko says you can use MBR(msdos) if you prefer up to 2TiB or about 2.2TB.

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.

There was a bug where grub had trouble finding boot files higher up in very large partitions.  You have a very large partition. I prefer smaller / (root) partitions and separate /home or even better but more advanced separate /data partitions. System has better performance if drive does not have to process 2TB of space to find all the system files it uses a lot. But with a server you may have databases or programs that prefer to have data in / and then you need a bigger root. I still prefer moving all data out of / if possible.

As a quick test since you have not installed much yet. Use gparted from liveCD and shrink the / partition to a much smaller size. Also in gparted click on sda1, select flags and change to bios_grub. I think the bios_grub looks like a boot flag to BIOS but am not sure. If not we may need a boot flag also. If all this works then you need to decide how to partition.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by qwyrp on 2011-11-04
Your suggested commands dmesg etc doesn't show anything.

I'll tried to change SDA1 to GRUB_GRUB but that wasn't an option.

I'll really appreciate your help but it's all confusing (English is not my first language) and frustrating (all new terms like GPT,MBR etc) to me so here's a idea: 
The data on the disk isn't important so I'm thinking of beginning from scratch. Can you please explain me what to do so I can install ubuntu and enyoing a automatically booting system

[LIST]
[*]What about Formatting: must I format the drive and if so which program to use and in what format (NTFS, FAT or .....)
[*]How to install the correct boot-tables (GPT or MBR) and also with program to use so it boots automatically
[/LIST]

---

### Post by oldfred on 2011-11-04
It is bios_grub as a flag in gparted on sda1. I would like you to try that and shrinking your main partition just as a test to see it it works at all. Then you can reformat.

I think any drive over 1+ TB, the auto install of Ubuntu to a full drive automatically uses gpt. If you format in advance, gparted will default to MBR(msdos). My normal suggestion is 10 to 20GB for / (root) but since you have 2TB and it is a server, it should be somewhat larger. If you partition in advance you use manual install to choose the pre-existing partitions. Not sure of differences with server installs.

I really only know desktops, so your may want to supply what kind of server you are installing so others can make some suggestions.

If only installing Ubuntu in MBR. This is my suggestion as a starting point. But each user has different requirements, data storage needs, additional  partitions for testing or shared NTFS with Windows.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 25+ GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

With gpt all partitions are primary, with MBR you can only have 4 primary partitions and one needs to be the extended partition to hold logical partitions.

More info on swap:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Lots of detail on installs, screenshots may be different versions but process is the same for all. Server installs do not normally have a gui.
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

For BIOS with MBR, you always install the grub2 bootloader to the MBR of the drive.

---

### Post by qwyrp on 2011-11-05
I've installed several times but every time there was no automatic boot. So my main concern: how to get empty/correct boottables because they causing my problems.
 
Is there a way to totally clean my diskdrives (including MBR/GPT etc) maybe a kind of lowlevel format. Resulting in a complete emtpty disk and empty and thus correct boottables (MBR/EFI or whatever)

---

### Post by darkod on 2011-11-05
You don't need low level format, the ordinary quick format deletes the partitions. Not really, but as far as the computer is concerned, yes.

With new technologies there are more options now, and more new things to learn. First you need to investigate around, google a bit, and decide how you want to do it.

For partition tables, except the msdos now exists gpt.

For booting now exists EFI on top of the "old way".

If all of these new technologies are confusing you too much, I will stick to what I said. msdos partition table still works with 2TB disks. Just use that and that's it.

To avoid banging your head deciding about correct partitions sizing right now, just use LVM and you're good to go.

If you decide to go this route:
Make sure in BIOS you are not using EFI boot (don't know how your BIOS looks like so I can't tell you where to go, refer to the board manual).

1. Boot the computer with ubuntu desktop cd (I know you want to use server version) into live mode. It's probably easier if you have graphic environment.
2. Open Gparted and select your hdd (it's probably only one).
3. Go in Device - Create Partition Table... Select to create msdos partition table (not sure if there is another type offered).
4. There will be warning all data will be destroyed. Accept it and you have your empty 2TB hdd with msdos partition table.

Then boot with your server cd and start the install. If you decided to do LVM there is even automatic install option with LVM, just use that if you want to.
Otherwise, create your partitions manually.

That's it.

For other ways of doing it, depends on your research about msdos/gpt and standard boot/efi.

---

### Post by qwyrp on 2011-11-05
My EFI-boot is off 

> **darkod said:**
> 
3. Go in Device - Create Partition Table... Select to create msdos partition table (not sure if there is another type offered).

Do you mean my msdos FAT16 or FAT32 because there's no msdos description

---

### Post by darkod on 2011-11-05
Honestly I have never used that option.
We are not talking about filesystems FAT16 and FAT32 right?

If the create partition table offers FAT16 and FAT32, use FAT32.

---

### Post by darkod on 2011-11-05
I think you are talking about filesystems. I just booted a 10.04 disc in live mode, when you select Create Partition Table a new window opens. In there it says it will create msdos partition table by default.

If you lick the + sign in front of Advanced, it will offer many other types of partition tables, including gpt.

So, forget about all the partition on the disk, everything. Just go into Device - Create Partition Table, since you want msdos table click Apply in the small window that opens, and then in the main Gparted window you need to click the green tick mark button to apply the changes to the disk. Gparted doesn't apply any changes until you click this green tick mark button.

---

### Post by qwyrp on 2011-11-05
I've tried gparted on a bootable cd and did all you explained but sadly it still won't boot :(

---

### Post by darkod on 2011-11-05
Hold on, did you install ubuntu server after that?

Creating a new blank partition table deletes all the partitions on the disk. It will not boot anything immediately after you create the table.
What it will do is create a msdos table instead of gpt.
Now you need to boot with the ubuntu server cd and install it.

---

### Post by qwyrp on 2011-11-05
I created the tables AND also installed Ubuntu Server with the disapointing result

---

### Post by darkod on 2011-11-05
Can you run the bootinfoscript again to see how it looks like now?

Do you get any error messages? Did you double check the boot process is set correctly in BIOS? Not just if EFI is off, but also the boot devices sequence, and that your HDD is set as boot device there?

Also, as oldfred says, some motherboards don't boot if there is no partition with the boot flag. Use the live mode and Gparted again, right click the root partition and from the menu select Flags (or similar) and turn on the boot flag. See if it boots the hdd after that. Even though ubuntu doesn't need this, some motherboards do.

---

### Post by qwyrp on 2011-11-05
I got no error messages. 

Hereby the code 
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    2048 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,gpt2)/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pwserver-root': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: onbekende bestandssysteemsoort ''

pwserver-swap_1': ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: onbekende bestandssysteemsoort ''
mount: onbekende bestandssysteemsoort ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Schijf /dev/sda: 2000.4 GB, 2000398934016 bytes
255 koppen, 63 sectoren/spoor, 243201 cilinders, totaal 3907029168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2           4,096       503,807       499,712 Data partition (Windows/Linux)
/dev/sda3         503,808 3,907,028,991 3,906,525,184 Logical Volume Manager (LVM) partition (Linux)

Drive: sdb _____________________________________________________________________

Schijf /dev/sdb: 7948 MB, 7948206080 bytes
245 koppen, 62 sectoren/spoor, 1021 cilinders, totaal 15523840 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    14,753,791    14,751,744  83 Linux
/dev/sdb2          14,755,838    15,521,791       765,954   5 Extended
/dev/sdb5          14,755,840    15,521,791       765,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/pwserver-root 1b24fa14-3cd1-4715-93cd-af328a6036df   ext4       
/dev/mapper/pwserver-swap_1 459bb811-ddb9-4969-a1e7-a04c5bab1f75   swap       
/dev/sda2        13e78ec8-ed1a-44ee-9105-74a6f691f4a9   ext2       
/dev/sda3        a4wLR2-jYp9-LBAf-Ukdy-vCpp-Hcp5-tnPeE8 LVM2_member 
/dev/sdb1        6e1988aa-ed5a-4202-a375-87267428f233   ext4       
/dev/sdb5        f92780e0-84c4-4e74-8d4e-0da61ae3cca9   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pwserver-root
pwserver-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod lvm
insmod part_gpt
insmod ext2
set root='(pwserver-root)'
search --no-floppy --fs-uuid --set 1b24fa14-3cd1-4715-93cd-af328a6036df
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 13e78ec8-ed1a-44ee-9105-74a6f691f4a9
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 13e78ec8-ed1a-44ee-9105-74a6f691f4a9
	linux	/vmlinuz-2.6.35-22-server root=/dev/mapper/pwserver-root ro   quiet
	initrd	/initrd.img-2.6.35-22-server
}
menuentry 'Ubuntu, with Linux 2.6.35-22-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 13e78ec8-ed1a-44ee-9105-74a6f691f4a9
	echo	'Loading Linux 2.6.35-22-server ...'
	linux	/vmlinuz-2.6.35-22-server root=/dev/mapper/pwserver-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 13e78ec8-ed1a-44ee-9105-74a6f691f4a9
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 13e78ec8-ed1a-44ee-9105-74a6f691f4a9
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.123135567 = 0.132215808    grub/core.img                                  2
   0.119714737 = 0.128542720    grub/grub.cfg                                  1
   0.034460068 = 0.037001216    initrd.img-2.6.35-22-server                   49
   0.013267517 = 0.014245888    vmlinuz-2.6.35-22-server                      19

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6e1988aa-ed5a-4202-a375-87267428f233
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 6e1988aa-ed5a-4202-a375-87267428f233
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6e1988aa-ed5a-4202-a375-87267428f233
	linux	/boot/vmlinuz-2.6.35-22-server root=UUID=6e1988aa-ed5a-4202-a375-87267428f233 ro   quiet
	initrd	/boot/initrd.img-2.6.35-22-server
}
menuentry 'Ubuntu, with Linux 2.6.35-22-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6e1988aa-ed5a-4202-a375-87267428f233
	echo	'Loading Linux 2.6.35-22-server ...'
	linux	/boot/vmlinuz-2.6.35-22-server root=UUID=6e1988aa-ed5a-4202-a375-87267428f233 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6e1988aa-ed5a-4202-a375-87267428f233
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 6e1988aa-ed5a-4202-a375-87267428f233
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-server (on /dev/mapper/pwserver-root)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 78965958-6b7e-4879-b696-852f377a2d59
	linux /vmlinuz-2.6.35-22-server root=/dev/mapper/pwserver-root ro quiet
	initrd /initrd.img-2.6.35-22-server
}
menuentry "Ubuntu, with Linux 2.6.35-22-server (recovery mode) (on /dev/mapper/pwserver-root)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 78965958-6b7e-4879-b696-852f377a2d59
	linux /vmlinuz-2.6.35-22-server root=/dev/mapper/pwserver-root ro single
	initrd /initrd.img-2.6.35-22-server
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=6e1988aa-ed5a-4202-a375-87267428f233 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=f92780e0-84c4-4e74-8d4e-0da61ae3cca9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.254211426 = 2.420441088    boot/grub/core.img                             1
   4.243385315 = 4.556300288    boot/grub/grub.cfg                             2
   0.516601562 = 0.554696704    boot/initrd.img-2.6.35-22-server               2
   2.460182190 = 2.641600512    boot/vmlinuz-2.6.35-22-server                  1
   0.516601562 = 0.554696704    initrd.img                                     2
   2.460182190 = 2.641600512    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on pwserver-root'


Unknown BootLoader on pwserver-swap_1'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/pwserver-root': Bestand of map bestaat niet
hexdump: /dev/mapper/pwserver-root': Bestand of map bestaat niet
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/pwserver-swap_1': Bestand of map bestaat niet
hexdump: /dev/mapper/pwserver-swap_1': Bestand of map bestaat niet


```

---

### Post by qwyrp on 2011-11-05
All booting settings are correct and now I've every partion (1 - 3) with the bootflag on but none of them worked.

Hereby some info

```
**parted -s /dev/sda print**
Model: ATA SAMSUNG HD204UI (scsi)
Schijf /dev/sda: 2000GB
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: gpt

Nummer  Begin   Einde   Grootte  Bestandssysteem  Naam  Vlaggen
 1      1049kB  2097kB  1049kB
 2      2097kB  258MB   256MB    ext2
 3      258MB   2000GB  2000GB                          opstart

```

---

### Post by darkod on 2011-11-05
I don't know how, but you still have the GPT partition table as earlier.

GUID Partition Table detected.

There was no new msdos table written.

Did you use this computer earlier with any other OS? Did you assemble it now yourself?

---

### Post by qwyrp on 2011-11-05
I didn't assemble it myself but I got it delevired with Win7 (booting automtically. Then I tried Ubuntu 11 and it worked. Then I'll tried Ubuntu 10 and the sh*t was hitting the fence ......
I'll tried several things (reinstall Windows 7, Ubuntu 10, EFI on, EFI off etc) in other words I make a big mess of it :(

Is there a way to get rit of the GPT?

---

### Post by darkod on 2011-11-05
Well, the procedure we talked about should delete the gpt table and create msdos one. But it seems it wasn't executed correctly.

In Gparted when you select Device - Create Partition Table by default it creates msdos. Just click Apply, then the green tick mark button in the Gparted toolbar, and that's it.
Install the server afterwards, and hopefully it should be OK.

If that procedure does not create new blank msdos table, something is weird with that HDD.

---

### Post by qwyrp on 2011-11-05
In parted I did following:
[LIST]
[*]mklable msdos
[*]mktable msdos
[/LIST]

And after typing parted -s /dev/sda print it now stated MSDOS, seems good to me.

And now following the procedure you're mentioning (in parted create mstable etc) .... keeping my fingers crossed !!!

---

### Post by darkod on 2011-11-05
> **qwyrp said:**
> In parted I did following:
[LIST]
[*]mklable msdos
[*]mktable msdos
[/LIST]

And after typing parted -s /dev/sda print it now stated MSDOS, seems good to me.

And now following the procedure you're mentioning (in parted create mstable etc) .... keeping my fingers crossed !!!

Not parted, Gparted in ubuntu desktop live mode. The GUI tool.

I don't know the commands for parted, I am not giving you instructions for that. I thought it's easier to use the ubuntu desktop live mode and the Gparted program.

---

### Post by qwyrp on 2011-11-05
I read that using mklabel en mktable in parted solving the persistent GPT. I'm using it and it stated msdos in stead of GPT so I think it's working (for now).

After  that I still following you and with gparted

---

### Post by darkod on 2011-11-05
OK. Let us know how it goes after the install.

parted is a text tool similar to Gparted so I don't think you need both procedures, but never mind. As long as it works.

---

### Post by qwyrp on 2011-11-05
D*mm stil not booting and still showing GPT ....

---

### Post by darkod on 2011-11-05
OK, lets go back to what oldfred was saying and try something. And don't use parted this time.

1. Boot ubuntu desktop live mode and open Gparted.
2. The disk is still GPT, that's what it says. Delete all partitions on the disk, all of them.
3. Create just one partition of 1MB at the start (front). Then right-click on it and from Manage Flags option select bios_grub.
4. Apply the changes in Gparted.

Boot with the server cd and install. Lets see how that goes.

---

### Post by oldfred on 2011-11-05
I still like gpt, but if you want to remove it. But once you have partitions set up you should be ok whether gpt or MBR.

Because the gpt has backups, some times it does not get totally housecleaned. You need to use gpt tools to houseclean the gpt.

GPT & MBR are types a partitioning a drive. NTFS &  FAT for Winodws and  ext3, ext4 etc for LInux are types of formats for the partitions.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by qwyrp on 2011-11-05
> **darkod said:**
> 
3. Create just one partition of 1MB at the start (front). Then right-click on it and from Manage Flags option select bios_grub.
Ik can Manage Flags but it only says± boot, lvm and several other options but no bios_grub

---

### Post by oldfred on 2011-11-05
Did you already change to MBR? In gparted on my system, it does not show bios_grub in MBR drive, but only on gpt drive.

---

### Post by qwyrp on 2011-11-05
> **oldfred said:**
> Did you already change to MBR? In gparted on my system, it does not show bios_grub in MBR drive, but only on gpt drive.
Probably a long the way I changed it to MBR ...... not of my knowledge.

I'm using FixParts but it stated on the homepage "Do not use gdisk if you want to use FixParts! " so maybe it's not a good idea to use gdisk. What's your opinion and if necessary maybe you have an alternative

---

### Post by qwyrp on 2011-11-05
And still no auto-booting and the disk is recognized as GPT (and I've used FixParts and it stated that it was MBR and no GPT)

Pffffff any ideas/suggestions?

---

### Post by oldfred on 2011-11-05
I have not used either fixparts or gdisk to remove gpt. The fixparts was created as an easy way to remove gpt data. My sda is MBR and my sdc is gpt.

Post this:
sudo parted /dev/sda unit s print

```
fred@fred-MavericDT:~$ sudo parted /dev/sda unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      63s         115330634s  115330572s  primary  ntfs         boot
 4      115330635s  156296384s  40965750s   primary  fat32
 2      156296385s  312576704s  156280320s  primary  ext3

fred@fred-MavericDT:~$ sudo parted /dev/sdc unit s print
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdc: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s                                bios_grub
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4
```

---

### Post by qwyrp on 2011-11-06
Still not booting 

sudo parted /dev/sda unit s print
```

Model: ATA SAMSUNG HD204UI (scsi)
Schijf /dev/sda: 3907029168s
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: gpt

Nummer  Begin        Einde        Grootte      Bestandssysteem  Naam  Vlaggen
 1      2048s        4095s        2048s                               bios_grub
 2      4096s        3859574783s  3859570688s  ext4
 3      3859574784s  3907028991s  47454208s    linux-swap(v1)

```

---

### Post by darkod on 2011-11-06
Not booting with the gpt disk, and it should, is one part of the problem. I can't help much because I have no experience with gpt.

But I am also very surprised that even after you tried writing a msdos table, it still clearly says the disk is gpt:

> 
Partitietabel: gpt


I would say this is impossible. It's like the disk is ignoring your commands to overwrite the gpt with msdos.

---

### Post by oldfred on 2011-11-06
I do not think it matters if it is gpt or msdos, if you have a huge / (root) grub will not be able to find all the files.

Try shrinking your sda2 partition to 25 or 50GB. You may also have to reinstall grub, but try booting right after shrinking /.

---

### Post by qwyrp on 2011-11-06
Oke I will give this a try but how2 (re)install grub?

---

### Post by qwyrp on 2011-11-06
I've resize SDA2 to 50Gb but no result. Now I'm looking for a way to reinstall GRUB.
Is setting the bootflag an option to try?

---

### Post by qwyrp on 2011-11-06
I'm so #$@##$# tired of it so I replaced this disk with an other disk and now it's working eeeh booting smoothly

Many thanks to **@oldfred, @darkod** and others for there continues idea's, tuts and help !!!!

---

