---
title: "No partitions"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by jeffshepherd on 2011-06-15
Hi everyone,

I have just downloaded Ubuntu 11.04 and am trying to install it on a dual boot system with Windows Vista. I get as far as "Allocate drive space" but there are no partitions to choose from. I currently have Windows and Linux Mint on the hard drive and want to install Ubuntu in the same partition as Mint to overwrite it.

---

### Post by oldfred on 2011-06-15
Welcome to the forums:

Have you used all 4 primary partitions? Then the auto installer will not have any choices but to overwrite entire drive.

If overwriting an existing Linux partition and have swap you should use manual install or "Something Else" in Natty.

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jeffshepherd on 2011-06-15
Hi oldfred,
 
What do you mean all 4 partions? 
 
I have checked what I have been doing and the installation process is not detecting Windows Vista.

---

### Post by oldfred on 2011-06-15
Post boot script's results.txt so we can see what you are seeing. Sometimes it is a partition error also which script should show.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by jeffshepherd on 2011-06-15
This is as far as I can get. 

Just to recap, I want to install Ubuntu 11.04 alongside Windows Vista as a dual boot system. The Hard drive has  been partitioned and Linux partition previously had Linux Mint on it.

---

### Post by oldfred on 2011-06-15
Run boot script from your liveCD.

I also have had gparted not see my drive when NTFS partition needed chkdsk. I was able to boot XP and XP did not complain, but after chkdsk then gparted saw drive.

XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by jeffshepherd on 2011-06-18
Sorry for the delay in posting again.
 
I have run CHKDSK and everything was fine. I have now run boot script and the results are below. I have 3 partitions on the hard drive, sda1 and sda2 are for windows. sda3 currently has Linux Mint Debian edition on it, I want to install Ubuntu in sda3 overwriting the existing Linux.
 
I have mounted all partitions on the hard drive.
 
Boot Info Script 0.60 from 17 May 2011
 
 
============================= Boot Info Summary: ===============================
 
=> Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
1 of the same hard drive for core.img. core.img is at this location and 
looks in partition 3 for (,msdos3)/boot/grub.
=> Grub2 (v1.97-1.98) is installed in the MBR of /dev/mapper/pdc_jhadegb and 
looks at sector 1 of the same hard drive for core.img. core.img is at this 
location and looks in partition 3 for (,msdos3)/boot/grub.
 
sda1: __________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Mounting failed: fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
 
sda2: __________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Mounting failed: fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
 
sda3: __________________________________________________________________________
 
File system: ext4
Boot sector type: -
Boot sector info: 
Mounting failed: fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda3 already mounted or sda3 busy
 
pdc_jhadegb1: __________________________________________________________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files: /bootmgr /Boot/BCD /Windows/System32/winload.exe
 
pdc_jhadegb2: __________________________________________________________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: 
 
pdc_jhadegb3: __________________________________________________________________
 
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Linux Mint Debian Edition
Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start Sector End Sector # of Sectors Id System
 
/dev/sda1 * 63 104,743,799 104,743,737 7 NTFS / exFAT / HPFS
/dev/sda2 104,743,800 388,467,764 283,723,965 7 NTFS / exFAT / HPFS
/dev/sda3 388,468,736 490,233,855 101,765,120 83 Linux
 
 
Drive: pdc_jhadegb _____________________________________________________________________
 
Disk /dev/mapper/pdc_jhadegb: 251.0 GB, 251000127488 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start Sector End Sector # of Sectors Id System
 
/dev/mapper/pdc_jhadegb1 * 63 104,743,799 104,743,737 7 NTFS / exFAT / HPFS
/dev/mapper/pdc_jhadegb2 104,743,800 388,467,764 283,723,965 7 NTFS / exFAT / HPFS
/dev/mapper/pdc_jhadegb3 388,468,736 490,233,855 101,765,120 83 Linux
 
 
"blkid" output: ________________________________________________________________
 
Device UUID TYPE LABEL
 
/dev/loop0 squashfs 
/dev/sda1 16D4C18D4FFB9219 ntfs WINDOWS
/dev/sda2 4CB99BD53B027E9C ntfs STORAGE
/dev/sda3 12b9ea9d-b15c-4453-abd2-dcfe4bd674ba ext4 
 
================================ Mount points: =================================
 
Device Mount_Point Type Options
 
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sr0 /cdrom iso9660 (ro,noatime)
 
 
======================= pdc_jhadegb3/boot/grub/grub.cfg: =======================
 
--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
 
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
load_env
fi
set default="2"
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
 
function load_video {
insmod vbe
insmod vga
insmod video_bochs
insmod video_cirrus
}
 
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set 12b9ea9d-b15c-4453-abd2-dcfe4bd674ba
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set 12b9ea9d-b15c-4453-abd2-dcfe4bd674ba
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###
 
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###
 
### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set 12b9ea9d-b15c-4453-abd2-dcfe4bd674ba
insmod png
if background_image /boot/grub/linuxmint.png ; then
set color_normal=white/black
set color_highlight=white/light-gray
else
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###
 
### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64' --class linuxmint --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set 12b9ea9d-b15c-4453-abd2-dcfe4bd674ba
echo 'Loading Linux 2.6.32-5-amd64 ...'
linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=12b9ea9d-b15c-4453-abd2-dcfe4bd674ba ro quiet
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set 12b9ea9d-b15c-4453-abd2-dcfe4bd674ba
echo 'Loading Linux 2.6.32-5-amd64 ...'
linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=12b9ea9d-b15c-4453-abd2-dcfe4bd674ba ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set 16d4c18d4ffb9219
chainloader +1
}
### END /etc/grub.d/30_os-prober ###
 
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
 
### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------
 
=========================== pdc_jhadegb3/etc/fstab: ============================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=385ecae6-bd34-41c3-a524-974b8cd6d17f / ext3 errors=remount-ro 0 1
# swap was on /dev/sda2 during installation
UUID=c6876978-438f-4a1e-ae53-dacdf22d1e4a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda3 / ext4 rw,errors=remount-ro 0 0
--------------------------------------------------------------------------------
 
=============== pdc_jhadegb3: Location of files loaded by Grub: ================
 
GiB - GB File Fragment(s)
 
187.366050720 = 201.182765056 boot/grub/core.img 1
229.495445251 = 246.418857984 boot/grub/grub.cfg 1
185.813205719 = 199.515410432 boot/initrd.img-2.6.32-5-amd64 1
187.365226746 = 201.181880320 boot/vmlinuz-2.6.32-5-amd64 1
185.813205719 = 199.515410432 initrd.img 1
187.365226746 = 201.181880320 vmlinuz 1
 
========= Devices which don't seem to have a corresponding hard drive: =========
 
sdb sdc sdd sde

---

### Post by Quackers on 2011-06-18
Are you using a Promise raid array?

---

### Post by oldfred on 2011-06-18
Gparted or liveCD installer does not normally work with RAID or LVM as those are for server or advanced users with special requirements to partition. I think the altenate installer works for those as it has the extra drivers built in.

It is not a liveCD, you should still have a liveCD of the same version,  as you may need it for other repairs someday and can download the extra drivers if needed to fully use liveCD.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

Fixed links:
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)

---

### Post by jeffshepherd on 2011-06-18
Quackers,

Yes I believe I am using Promise raid array.

---

### Post by Quackers on 2011-06-18
I'm not sure whether Promise controllers are fully supported or not.
What you could try is to boot from the 11.04 live cd and select "try Ubuntu" and when the desktop loads connect to the internet.
Then using synaptic package manager install the kpartx package.
After its installation open gparted and see if your raid array is recognised by it. 
You may need to click on the down arrow next to /dev/sda in the little box to the right. You should see options such as /dev/sda, /dev/sdb and /dev/mapper/pdc_jhadegb.
This last one is your raid array.

---

### Post by jeffshepherd on 2011-06-18
Oldfred,

The link for the alternate installer doesn't work but I have google'd it and got to the right place.

As a workaround I installed 9.04 and am upgrading until I get to 11.04.

---

### Post by jeffshepherd on 2011-06-18
Ok I have finally managed to install Ubuntu 11.04 by using the alternate download however I now have other problems.

1. Grub does not recognize the 2 windows partition, When booting no Grub menu comes up.

2. I got a message to say I do not have the hardware to run the Unity desktop.

Unity can wait for the time being but I need the option to boot into Windows urgently.

Thanks,
Jeff

---

### Post by Quackers on 2011-06-18
run ```
sudo update-grub
``` in the terminal and see if the Windows Loader is found.

---

### Post by oldfred on 2011-06-18
You could try adding one or more of these. I have not seen a RAID boot of windows that I can remember.

    insmod raid
    insmod mdraid

To test, at grub menu select e and edit to add line(s) above. If it works then we can modify 40_custom.

---

### Post by jeffshepherd on 2011-06-18
Thanks for all your help guys but I am sorry to say I am giving up, installing an OS should not be this difficult so I have reverted to LMDE which works flawlessly with Windows, this is a shame as I really want to try Unity. I will continue to keep an eye in ubuntu in the hope that oneday there will be a release that installs without all this hassle.

---

### Post by oldfred on 2011-06-18
Understand RAID is an advanced configuration and is intended more for uptime or speed not backup. Depending on how you have it set up it, one drive failure may not let you into the other drive. It should not be a backup but a way to speed things up. 

Standard users with desktops rarely use RAID. If I am setting up RAID I want 5 drives set up so any one failure does not lose any data and lets me keep going. For my desktop I just do backups.

---

