---
title: "USB Boot=easy, HDD install=X"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Ubuwho? on 2009-12-05
I just want to install Ubuntu on my laptop's local hard drive!!
 
I'm brand new (this weekend kind of new!) to Linux. i have a wiped IBM T42 laptop with a dodgy CD-drive. I also have a 16GB USB flash Drive.
 
Ultimately i want to get so that the Laptop boots straight into Ubuntu on it's own. the computer won't have any other OS's on it.
 
As the CD-drive isn't working, i have installed 9.10.iso onto the USB and booted, no problems. it runs under the "Persistently" mode great. With the Casper thing it even remembers changes i make once i'm in. Lovely.
 
Then i run the "Install" program. it all seems to be ok, goes through the motions. i choose to format and install on the local hard drive. i have no idea about drive flags etc, ext3/4/5, swaps.
 
i would have thought then, shutdown, remove USB, boot up, done.
 
NO. 
 
It comes up with a Grub is loading line, then a GNU Grub version screen in a large white box, with 4 options:
Ubuntu, Linux, 2.6.31-14-generic
Ubuntu, Linux, 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
 
choosing the top of the 4, error: no such device: and a load of numbers/letters, press a key to continue.
 
 
Any ideas why it won't boot up without the USB?
 
any help is appreciated. thanks.

---

### Post by darkod on 2009-12-05
We can only guess at this point, but it might be that during install your usb stick was hd0 and internal hdd hd1. Now with the stick out the hdd is hd0 but Grub2 is looking for hd1.

Boot with the stick again, select Try Ubuntu option. It will run liveCD from the stick. Download the script in my signature, for example on the desktop. Run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with your complete boot process. Post the content of that file here, and while posting it with the text selected please put CODE tags around it. Just hit the # button in the this toolbar when posting. Makes it easier to read.

---

### Post by Ubuwho? on 2009-12-05
Thanks for the quick reply.
```
============================= Boot Info Summary: ==============================
 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63    56,098,979    56,098,917  83 Linux
/dev/sda2    *     56,098,980    58,605,119     2,506,140   5 Extended
/dev/sda5          56,099,043    58,605,119     2,506,077  82 Linux swap / Solaris
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0046774e
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *             32    31,326,207    31,326,176   c W95 FAT32 (LBA)
 
blkid -c /dev/null: ____________________________________________________________
/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="c1d0bf75-bc2f-ae4b-9796-5e14075851f1" TYPE="ext2" 
/dev/sda1: LABEL="Laptop" UUID="59acded3-539b-4d0b-aa93-83302f31a3db" TYPE="ext4" 
/dev/sda5: UUID="d33a8806-e2ab-4dcc-b4fd-3427cb9ff4a4" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: LABEL="USBEEE" UUID="BCFE-3773" TYPE="vfat" 
=============================== "mount" output: ===============================
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
 
=========================== sda1/boot/grub/grub.cfg: ===========================
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 59acded3-539b-4d0b-aa93-83302f31a3db
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 59acded3-539b-4d0b-aa93-83302f31a3db
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=59acded3-539b-4d0b-aa93-83302f31a3db ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 59acded3-539b-4d0b-aa93-83302f31a3db
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=59acded3-539b-4d0b-aa93-83302f31a3db ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=59acded3-539b-4d0b-aa93-83302f31a3db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d33a8806-e2ab-4dcc-b4fd-3427cb9ff4a4 none            swap    sw              0       0
=================== sda1: Location of files loaded by Grub: ===================
 
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

```
 
i hope that means something to somemone

---

### Post by darkod on 2009-12-05
It looks all normal. No problem to point out, at least to my knowledge.
One thing you could try is to run in terminal:
sudo apt-get remove dmraid

It sometimes help when it can't "see" the drive, which might be a reason for "no device" error. Execute that command, reboot and unplug the stick to see if booting from the hdd will be fixed.

---

### Post by Ubuwho? on 2009-12-05
it looked promising, but unfortunately it does the same on booting without the USB plugged in:
 
Grub Loading, then the white box with the 4 options.  Choosing the logical top one, error: no such device:  59acded3-539b-4d0b-aa93-83302f31a3db.
 
i do't believe that it should be this complicated!
Thanks

---

### Post by darkod on 2009-12-05
That code is UUID correct. I can't see nothing wrong, sorry.
You might try to reinstall grub2 although it looks fine, it only takes two commands in terminal (after you have booted with the usb stick, if you did that to get internet do it right now):

sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
sudo update-grub

Reboot, and see how it boots. Is a hassle you have to unplug the stick to check if the boot from hdd will work. :(

---

### Post by Ubuwho? on 2009-12-05
there is a difference now.  it won't boot with the USB installed now
 
Choosing the Persistently boot option with the usb in it says:
(initramfs) FATAL: Could not load /lib/modules/2.6.31-15-generic/modules.dep:  No such file or directory.
Unable to find a medium containing a file system.
 
 
Looking at the lines typed above, it's trying to load -15, when previously it was saying -14 i think! Does this mean anything?

---

### Post by darkod on 2009-12-05
And the boot from hdd still doesn't wanna work?

---

### Post by Ubuwho? on 2009-12-05
nope.

---

### Post by darkod on 2009-12-05
Sorry, I have no idea what could be wrong. I have installed from usb stick to my netbook (no cd-rom anyway) and it definitely works.
Even the grub2 reinstall didn't help, maybe you need to consider a clean install on your internal hdd. :(

---

### Post by Ubuwho? on 2009-12-05
no problem, but how do i do that?
 
I would love to format the local drive and boot from a fresh USB install, but this is the loop i have done too many time already with the same outcome.
 
once i get into the USB boot version, i don't quite get the process to install to the local HDD.  i just want to format and totally wipe it, then install a bootable version done.
 
so, boot from USB, 
Click to install
do i want to erase the whole drive? (i would have thoght so)
then under the advanced tab, do i want a boot loader?

---

### Post by Ubuwho? on 2009-12-05
Using the pendrivelinux USB installer and the downloaded ISO file, i'm back up and running, exactly as i left it before from the USB, including the results and script on the dektop!
 
how do i wipe the local hard drive completely, other than in the install steps?
 
i have /dev/sda1 on ext4 file sysem, with no ticks on manage flags.
should this have a tick on boot?

---

### Post by darkod on 2009-12-05
Yes, exactly. There is option Erase and use whole drive, and select the correct drive (in your case in the list there might be the internal disk and the usb stick). When selecting the drive make a note whether it's /dev/sda (should be) or /dev/sdb.
On the last screen before you click Install, click on Advanced button and double check where grub2 will be installed. Yes, you want a bootloader to be installed and double check that the destination is the internal drive (if it's /dev/sda then it should say also /dev/sda here, or /dev/sdb depending how it's called in the earlier step). And that should be it. When it finishes installation unplug the stick and also during the restart put the hdd drive as first boot choice in BIOS and that should be it.

---

### Post by darkod on 2009-12-05
> **Ubuwho? said:**
> Using the pendrivelinux USB installer and the downloaded ISO file, i'm back up and running, exactly as i left it before from the USB, including the results and script on the dektop!
 
how do i wipe the local hard drive completely, other than in the install steps?
 
i have /dev/sda1 on ext4 file sysem, with no ticks on manage flags.
should this have a tick on boot?

No, only windows needs those boot flags. You can use Gparted in System-Administration if you really want to wipe the hdd before starting the install but the installer will do it anyway. See previous post and attachment.

---

### Post by Ubuwho? on 2009-12-05
thanks for all of the help.
 
after multiple retries, i'm trying kubuntu now.  it will now boot from an install on the local hdd.  just have the display problem to sort out now.
 
Thanks for the quick replies.

---

