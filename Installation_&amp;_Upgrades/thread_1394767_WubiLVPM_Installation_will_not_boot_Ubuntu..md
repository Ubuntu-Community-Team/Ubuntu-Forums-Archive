---
title: "Wubi/LVPM Installation will not boot Ubuntu."
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by alkh3myst on 2010-01-31
Help! I'm new to Ubuntu. Don't be fooled by my join date. I tried Gutsy, but didn't have enough time to learn Linux.I installed Wubi, and really liked it. Karmic is much more user-friendly. So, I used LVPM to put Ubuntu on a new partition. I shrank NTFS using Windows (Vista :mad:), and used GParted to format EXT 4 on dev/sda2 and swap on dev/sda3. Did I do this right? Next, I used LVPM to put my Wubi installation on the EXT 4 partition, but LVPM reformatted it to EXT 3. Now Ubuntu will not boot at all on the new partition. I've spent the last 4 days struggling with GRUB documentation, most of which is out of date, for GRUB legacy. Even the "official" GRUB 2 documentation has not kept up with changes. More than half of the commands I found in my GRUB 2 menu, using "tab" don't match the docs. Did I mention I'm new to Ubuntu? Still, I've kept searching for an answer. Everybody is very helpful, knows just what's wrong, but their suggestions don't work. I tried running a script in .sh format in the terminal, but it doesn't run either, despite following several contradictory sets of instructions on how to do this. Did I say I'm new to Ubuntu? Never had to use a command line with so huge a number of possible commands before. *Now, **finally** "Startup Manager" came up in a search of the forums.*This seems to work, but I can't figure out how to diagnose my problem, which seems to be the case of the missing kernel. I really don't know my initards from my uuids, and haven't found a GRUB glossary. I'm treading water in mid Pacific, can somebody throw me a life preserver? I'd burn a CD and start from scratch, but my burner's not working right. One last thing. Does Ubuntu boot from EXT or swap? It may sound stupid, but what's really stupid is me not asking. Did I forget to say I'm new to Ubuntu? Mama said there'd be days like this...

---

### Post by Sef on 2010-01-31
Read [this]("https://wiki.ubuntu.com/WubiGuide").  The answer is located under Misc.

---

### Post by alkh3myst on 2010-01-31
Thanks. Maybe you didn't read my post carefully. I said that: ***"I used LVPM to put Ubuntu on a new partition."*** Your suggestion, while I thank you for responding, will not resolve my problem at all. My **permanent** Ubuntu installation will not boot, not my Wubi, which works fine, for now. GRUB 2 doesn't recognize my permanent Ubuntu installation on dev/sda2; *changing the default OS to Ubuntu will only boot my Wubi installation as the default OS.* **This solves nothing.** You also seem not to notice that I'm running Vista instead of XP, which the instructions you refer to call for. Longhorn is a jealous bootloader, probably by Microsoft's monopolistic intent, that you tamper with at your own peril. Voice of experience. Again I thank you for responding at all, but can you give me a solution that actually works, and applies to my problem?

---

### Post by oldfred on 2010-01-31
I saw your post in the other thread, but understand that using LVPM is a more advanced configuration to combine drive space. Very few users have that configuration. I do not know LVPM, but there are a few here who may be able to give specific advice. 

Again we need to see the boot_info script. It should run from your Wubi install ( I run it from my standard install just to see my configuration, but it puts the results.txt in /home for me) but instructions are for users who cannot boot and are using a liveCD. I suggest using the liveCD if you have trouble, so you can follow the specific directions.
This link has extra instructions and a link to download.

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Are you only booting Vista and getting the Vista/Wubi choice? Grub2 booting should give you your install and Vista as choices on a menu.

---

### Post by oldfred on 2010-01-31
Here is another thread with lvm.
[http://ubuntuforums.org/showthread.php?t=1394399](http://ubuntuforums.org/showthread.php?t=1394399)

Herman says you have to install with the alternative CD, not the standard desktop.

---

### Post by darkod on 2010-01-31
> **oldfred said:**
> Here is another thread with lvm.
[http://ubuntuforums.org/showthread.php?t=1394399](http://ubuntuforums.org/showthread.php?t=1394399)

Herman says you have to install with the alternative CD, not the standard desktop.

LVM has nothing to do with LVPM which is some sort of software to move wubi into full ubuntu on its own partition.
Maybe it's too late now, but what about installing ubuntu into the space you designated for the LVPM transfer, and then just move your data from wubi into the full ubuntu.
It's not a perfect solution, but neither is LVPM. In fact, the moment you decided you want ubuntu for long term, you should have got rid of wubi and make a full install.
The sourceforge LVPM webpage doesn't even say it's supported for 9.10.

---

### Post by oldfred on 2010-01-31
Good catch Darko I missed the difference between LVM and LVPM. I have seen where the conversion from wubi to a partition did not complete correctly. As I remember it just needed a fix or two. The script should tell us what is missing.

I think backing up /home or any other data from wubi and a full clean install would always be better. If space is available one could do a new install and temporarily mount the wubi install to copy over and data/settings.

---

### Post by Leppie on 2010-01-31
> **alkh3myst said:**
> Help! I'm new to Ubuntu. Don't be fooled by my join date. I tried Gutsy, but didn't have enough time to learn Linux.I installed Wubi, and really liked it. Karmic is much more user-friendly. So, I used LVPM to put Ubuntu on a new partition. I shrank NTFS using Windows (Vista :mad:), and used GParted to format EXT 4 on dev/sda2 and swap on dev/sda3. Did I do this right? Next, I used LVPM to put my Wubi installation on the EXT 4 partition, but LVPM reformatted it to EXT 3. Now Ubuntu will not boot at all on the new partition. I've spent the last 4 days struggling with GRUB documentation, most of which is out of date, for GRUB legacy. Even the "official" GRUB 2 documentation has not kept up with changes. More than half of the commands I found in my GRUB 2 menu, using "tab" don't match the docs.
i am sorry you're having this bad experience with the lvpm process. to be honest i've never done a wubi install, so i wouldn't really know how that works. i'll try it when i've set up my virtual machine properly.

> **alkh3myst said:**
> Did I mention I'm new to Ubuntu? Still, I've kept searching for an answer. Everybody is very helpful, knows just what's wrong, but their suggestions don't work. I tried running a script in .sh format in the terminal, but it doesn't run either, despite following several contradictory sets of instructions on how to do this.
to run a script, you normally need to make it executable. most howto's and guides tell you to download to the desktop, so the command to run the script after downloading without changing its permissions would be:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

> **alkh3myst said:**
> I'd burn a CD and start from scratch, but my burner's not working right. One last thing. Does Ubuntu boot from EXT or swap?
i don't know what you mean by "EXT", but ubuntu should boot from your normal install's partition (not swap, swap is like extended memory on disk).
can you boot off a livecd, or boot into your wubi install and run the script? this would really help us analyse the problems you're facing.

---

### Post by alkh3myst on 2010-02-02
Thanks so much everybody! Sorry for the delay, I had some JDK tweaking to do, installing the new version, and writing a little test code. I didn't know you had to save the script to the desktop, I had it saved in Documents. I will paste it here. (I'm sure there's a way to do this via a link but I don't know how yet. I'm going to have to get the latest edition of Ubuntu for Dummies.) One more question: Once this issue is fixed God willing, I can move my Ubuntu install somewhere else and reformat dev/sda2 to ext4, since LVPM changed it to ext3, right? Thanks again gang! You don't know how much I appreciate this.***FORGOT TO ADD...GRUB 2 GIVES ME THESE CHOICES: IT SHOWS UBUNTU ON DEV/SDA2 BUT WONT LET ME BOOT. THE OTHER 2 CHOICES ARE "UNKNOWN OS" WHICH SENDS ME TO LONGHORN, AND "VISTA BOOTLOADER" WHICH DOES THE SAME THING...HOPE THIS HELPS.



============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x044b35a9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   341,753,534   341,753,472   7 HPFS/NTFS
/dev/sda2         341,766,810   621,731,564   279,964,755  83 Linux
/dev/sda3         621,731,565   625,137,344     3,405,780  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8253 MB, 8253341696 bytes
255 heads, 63 sectors/track, 1003 cylinders, total 16119808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00030938

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    16,113,194    16,113,132   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       67c49498-ff96-43d9-b038-6c12a66607cf   ext4                                     
/dev/sda1        B81CBE6A1CBE2374                       ntfs                                     
/dev/sda2        69db9f11-beab-4a8a-95ef-4c972e1d9edb   ext3                                     
/dev/sda3        57a046da-d5a1-48e9-8be3-dbcb616a1d8c   swap                                     
/dev/sdb1        DAF2-325A                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /host                    fuseblk    (rw)
/dev/sdb1        /media/DAF2-325A         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda1/Wubi/boot/grub/menu.lst: ========================



title Ubuntu-on-/dev/sda2
root (hd0,1)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda2
root (hd0,1)
configfile /boot/grub/menu.lst


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
# kopt=root=UUID=B81CBE6A1CBE2374 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=B81CBE6A1CBE2374

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

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

=========================== sda2/boot/grub/menu.lst: ===========================



title Ubuntu-on-/dev/sda2
root (hd0,1)
configfile /boot/grub/menu.lst



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title UnknownOS
root (hd0,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd0,0)
makeactive
chainloader +1
boot


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b81cbe6a1cbe2374
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda2
UUID=     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=       /media/drv0                defaults      0   0


# /dev/sda3
UUID=      none            swap        sw          0   0


=================== sda2: Location of files loaded by Grub: ===================


 174.9GB: boot/grub/grub.cfg
 174.9GB: boot/grub/menu.lst
 174.9GB: boot/grub/stage2
 174.9GB: boot/initrd.img-2.6.31-14-generic
 174.9GB: boot/initrd.img-2.6.31-17-generic
 174.9GB: boot/vmlinuz-2.6.31-14-generic
 174.9GB: boot/vmlinuz-2.6.31-17-generic
 174.9GB: initrd.img
 174.9GB: initrd.img.old
 174.9GB: vmlinuz
 174.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by oldfred on 2010-02-04
You can run a script from anywhere, the instructions are a little different depending on where it goes and all the older versions defaulted to the desktop.
In the panel with fonts and editing when you are commenting is a code tag (#). If you highlight code with click/mouse (your entire results.txt) then it is a little easier to review.

The conversion did not convert to grub2 but to grub legacy (0.97) as your boot loader and it wrote a very minimal menu.lst which does not have your ubuntu listed. I think the config file is how it is supposed to work but it refers to itself. 

You have several choices. You should be able to manually boot from the grub menu, but you have to type in all the commands (tab can help complete the line) and then update from your install. You can chroot into your system from a liveCD and totally reinstall grub legacy or uninstall grub legacy and install grub2. All these will reinstall grub to the MBR but more importantly update menu.lst for old grub or grub.cfg for grub2.

to update and reinstall old grub from liveCD terminal
sudo mount /dev/sda2 /mnt
for i in dev proc sys; do mount --bind /$i /mnt/$i; done
sudo chroot  /mnt
sudo update-grub
grub
at grub prompt:
root (hd0,2)
setup (hd0,2)
quit

---

