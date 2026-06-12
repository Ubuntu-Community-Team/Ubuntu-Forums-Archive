---
title: "Disk Boot Failure Grub Issue"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by adamg2000 on 2010-01-23
Hi All, this is my first post so please be gentle. I converted to Ubuntu from OSX a few weeks ago and have been having the time of my life. Just love the freedom. Been enjoying all sorts of tricks and new tools and games. However I moved the computer to another house and when I started it, I got the following: DISK BOOT FAILURE, INSERT SYSTEM DISK...

I've searched around, and found a variety of articles in the forum etc on this, though am struggling to figure out what to do next as I cannot fix the issue. The computer is a self built one with two hard drives, no other OSs installed (except for a web development copy of winxp in VirtualBox).

I've been able to get into my installation of Ubuntu using the LiveCD, choosing 'Boot to first Disk' - I changed the bios to boot from CD-ROM to get that far.

One previous poster (who's problem was solved) was asked run the boot_info_script script, so I pre-empted that request and have added it below. I read it in an attempt to understand it, but I can't make anything much out of it - I can see that it describes the installation as I made it. Any assistance would be very gratefully received.

--------------

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ad394

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,992,429     9,992,367  83 Linux
/dev/sda2           9,992,430   234,436,544   224,444,115   5 Extended
/dev/sda5           9,992,493    17,992,799     8,000,307  82 Linux swap / Solaris
/dev/sda6          17,992,863   234,436,544   216,443,682  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ed1d2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0a3a530f-af24-4080-a1c2-1a390ee5bb30" TYPE="ext4" 
/dev/sda5: UUID="b10daee7-b04b-496f-b58c-9944410c7720" TYPE="swap" 
/dev/sda6: UUID="4d13a8c8-9c95-4d02-83fb-3393178918a1" TYPE="ext4" 
/dev/sdb1: UUID="987d01cd-084d-4133-a8f5-b506977e0900" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /boot type ext4 (rw)
/dev/sdb1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/adam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adam)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=adam)


============================= sda1/grub/grub.cfg: =============================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 4d13a8c8-9c95-4d02-83fb-3393178918a1
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: initrd.img-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-17-generic

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 4d13a8c8-9c95-4d02-83fb-3393178918a1
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0a3a530f-af24-4080-a1c2-1a390ee5bb30 /boot           ext4    defaults        0       2
# /home was on /dev/sdb1 during installation
UUID=987d01cd-084d-4133-a8f5-b506977e0900 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b10daee7-b04b-496f-b58c-9944410c7720 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


   9.2GB: boot/grub/core.img
   9.2GB: boot/grub/grub.cfg
   9.2GB: boot/initrd.img-2.6.31-14-generic
   9.2GB: boot/initrd.img-2.6.31-17-generic
   9.2GB: boot/vmlinuz-2.6.31-14-generic
   9.2GB: boot/vmlinuz-2.6.31-17-generic
   9.2GB: initrd.img
   9.2GB: initrd.img.old
   9.2GB: vmlinuz
   9.2GB: vmlinuz.old

---

### Post by Leppie on 2010-01-23
booting off the livecd, issue these commands:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by kansasnoob on 2010-01-23
> I've been able to get into my installation of Ubuntu using the LiveCD, choosing 'Boot to first Disk' - I changed the bios to boot from CD-ROM to get that far.

So you can actually boot into you installed Ubuntu?

If so post the output of:

```
df -H
```

I'm looking over your output :)

---

### Post by kansasnoob on 2010-01-23
> **Leppie said:**
> booting off the livecd, issue these commands:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

I'm thinking the OP has a separate /boot partition on sda1. Maybe?

---

### Post by adamg2000 on 2010-01-23
First, thanks to you both for such a fast response, I was told the community was helpful, one of the many reasons I picked this distro, but that's above and beyond!

I thought I'd post the read out of kansasnoob's command before trying a fix in case it clarified anything:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6              110G   4.4G   100G   5% /
udev                   1.1G   259k   1.1G   1% /dev
none                   1.1G   1.4M   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda1              5.1G   177M   4.7G   4% /boot
/dev/sdb1              493G    35G   433G   8% /home
/dev/sr0               725M   725M      0 100% /media/cdrom0

Also, yes I can get to my installation. For clarity, the steps are:

1. Switch BIOS to boot from CD-ROM, instead of HD
2. Load LiveCD, select Boot From First Drive option, instead of previewing.
3. Then I log in as normal, and I'm away using me two week old installation!

---

### Post by Leppie on 2010-01-24
> **kansasnoob said:**
> I'm thinking the OP has a separate /boot partition on sda1. Maybe?
haha... that proves it, never post when you're tired... :P

---

### Post by darkod on 2010-01-24
> **adamg2000 said:**
> First, thanks to you both for such a fast response, I was told the community was helpful, one of the many reasons I picked this distro, but that's above and beyond!

I thought I'd post the read out of kansasnoob's command before trying a fix in case it clarified anything:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda6              110G   4.4G   100G   5% /
udev                   1.1G   259k   1.1G   1% /dev
none                   1.1G   1.4M   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda1              5.1G   177M   4.7G   4% /boot
/dev/sdb1              493G    35G   433G   8% /home
/dev/sr0               725M   725M      0 100% /media/cdrom0

Also, yes I can get to my installation. For clarity, the steps are:

1. Switch BIOS to boot from CD-ROM, instead of HD
2. Load LiveCD, select Boot From First Drive option, instead of previewing.
3. Then I log in as normal, and I'm away using me two week old installation!

Yes, you do have separate /boot partition. As long as the problem is only reinstalling grub2 to the MBR, boot the live cd in live desktop mode (Try Ubuntu option) and in terminal execute:

sudo mount /dev/sda6 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd and see if it helped.

---

### Post by kansasnoob on 2010-01-24
> **Leppie said:**
> haha... that proves it, never post when you're tired... :P

That was only an edumicated guess :)

I'm just wondering why any settings would be lost moving the computer :confused:

And, to be perfectly honest, I've never used a separate /boot partition yet with grub2 so I'm kind of scratching my head :confused:

Hopefully Darko has it nailed :)

---

### Post by Leppie on 2010-01-24
> **kansasnoob said:**
> That was only an edumicated guess :)
good guess then, +1 :)

> **kansasnoob said:**
> I'm just wondering why any settings would be lost moving the computer :confused:
i've had systems that wouldn't switch on at all after having been moved.
they seem to have a bit of their own life as well after all...

> **kansasnoob said:**
> And, to be perfectly honest, I've never used a separate /boot partition yet with grub2 so I'm kind of scratching my head :confused:
i always use a separate boot partition (and always have to adjust the commands i use to what others have when posting). maybe the disk has a bad sector in the mbr...
i think the OP should check the integrity of the entire disk.

---

### Post by adamg2000 on 2010-01-24
> **darkod said:**
> Yes, you do have separate /boot partition. As long as the problem is only reinstalling grub2 to the MBR, boot the live cd in live desktop mode (Try Ubuntu option) and in terminal execute:

sudo mount /dev/sda6 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd and see if it helped.

I tried this and the operation was reported as being a success, however on boot, the same DISK BOOT FAILURE error occured when I set the bios to boot from Hard Disk. I am still able to access my installation using the CD-ROM.

---

### Post by Leppie on 2010-01-24
> **adamg2000 said:**
> I tried this and the operation was reported as being a success, however on boot, the same DISK BOOT FAILURE error occured when I set the bios to boot from Hard Disk. I am still able to access my installation using the CD-ROM.
have you checked your hd's health?

---

### Post by adamg2000 on 2010-01-24
> **Leppie said:**
> have you checked your hd's health?
Hi leppie, I'm using the SMART Data Extended self-test in Palimpsest Disk Utility to do that now. It may take a couple of hours, I'll drop back my findings when it's complete. If there are any other tests I should be doing, please let me know. Thanks.

---

### Post by Leppie on 2010-01-24
ok, good luck

---

### Post by adamg2000 on 2010-01-24
Test completed and reports disk is healthy although in the Read Error Rate entry there are the following numbers (Normalized:69, Worst: 64, Threshold: 6, Value: 94203474) where is says "non-zero value indicates a problem..." though the Assesment column says Good.

---

### Post by Leppie on 2010-01-24
try with the manufacturer's disk tool.

---

### Post by meierfra. on 2010-01-24
Couple of things to try:

1) Make sure that your Bios are set to boot from the Ubuntu drive and not your 500GB drive.

2)  Is your hard drive plugged in correctly?  Check the cables.

3)  Do you a  have floppy drive or any other kind of external media which might conflict with booting?

4)  You might see what happens if you unplug the 500GB drive.

5)  The opposite of 4)  Install Grub to the MBR of of "500GB" drive: 
     Boot into Ubuntu via  "Boot from first hard drive"
      ```
sudo grub-install /dev/sdb
sudo sfdisk -A1 /dev/sdb
```
     and then set your Bios to boot from your 500GB drive.

---

### Post by adamg2000 on 2010-01-24
> **Leppie said:**
> try with the manufacturer's disk tool.
Done this now also, downloaded seagate tools for linux ran long test, drive PASSED.

---

### Post by adamg2000 on 2010-01-24
> **meierfra. said:**
> Couple of things to try:

1) Make sure that your Bios are set to boot from the Ubuntu drive and not your 500GB drive.

2)  Is your hard drive plugged in correctly?  Check the cables.

3)  Do you a  have floppy drive or any other kind of external media which might conflict with booting?

4)  You might see what happens if you unplug the 500GB drive.

5)  The opposite of 4)  Install Grub to the MBR of of "500GB" drive: 
     Boot into Ubuntu via  "Boot from first hard drive"
      ```
sudo grub-install /dev/sdb
sudo sfdisk -A1 /dev/sdb
```
     and then set your Bios to boot from your 500GB drive.

I looked into 1) seemed correct. I tried 2, now got a flashing cursor and no failure. just nothing. 3, No. 4) tried this and now cannot boot into Ubuntu using the LiveCD, only the try ubuntu feature, which can happily see the disks and browse them without issue.

---

### Post by adamg2000 on 2010-01-24
Hi All, I'm getting a new error now, when I try to use the LiveCD to boot to first disk. isolinux: disk error 01, AX = 0201, drive 80 Boot Failed: press a key to retry...

I've done a quick search on the web but most of the reports are about USB drives or dual boot, of which my install is neither. Any ideas?

---

### Post by adamg2000 on 2010-01-24
> **meierfra. said:**
>  5)  The opposite of 4)  Install Grub to the MBR of of "500GB" drive: 
     Boot into Ubuntu via  "Boot from first hard drive"
      ```
sudo grub-install /dev/sdb
sudo sfdisk -A1 /dev/sdb
```     and then set your Bios to boot from your 500GB drive.

Though I can no longer access via "Boot from first hard drive" option, I thought I'd give this a go from the LiveCD in which I mounted the 500GB drive (it was given sda in this instance) but got the following:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by meierfra. on 2010-01-24
> I tried 2, now got a flashing cursor and no failure. just nothing. 
...
isolinux: disk error 01, AX = 0201, drive 80 Boot Failed:


Are the hard drives plugged in the same way before?
It really sounds like there is something wrong with  way your hard drives are plugged in. Or maybe  your cables are failing?



> grub-probe: error: cannot find a device for /boot/grub.
From the LiveCD you have to do
```
sudo mount /dev/sda6 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ --recheck /dev/sdb
```

---

### Post by adamg2000 on 2010-01-24
> **meierfra. said:**
> 
It really sounds like there is something wrong with  way your hard drives are plugged in. Or maybe  your cables are failing?

Hi meierfra. I've made sure they are plugged into SATA ports 1 and 2 as before, I've also got a spare cable which I've swapped out the boot discs original cable with, exactly the same result, only this time, it gets stuck at a cursor with BOOTING FROM FIRST DISC or something very similar.

It does sound like hardware - but how is everything else working once I'm into LiveCD?

---

### Post by adamg2000 on 2010-01-24
Weird, I just ran this again:

sudo mount /dev/sda6 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ --recheck /dev/sdb

and it's working, logging in like it did before the move. I've tried it twice and it's worked twice. Something got fixed. Has this moved grub and booting to the 500GB drive? If so, is this tidy? Would it impact on the stability of the machine later?

Sorry for being such a noob, I am hoping to live with Linux from now on, and I can't help but want to get under the hood - plus I'd like to know what happened so if needs be I can fix it myself if it happens again.

---

### Post by meierfra. on 2010-01-24
> Has this moved grub and booting to the 500GB drive? 

Yes, that installed grub to the MBR of the 500GB drive. But Grub is also still installed in the MBR of the Ubuntu drive.
Did you switch the boot order in the bios? Or are you still booting from the Ubuntu drive?


> If so, is this tidy?
It just fine. Sometimes booting is slower if Grub is not on the same drive as Ubuntu, since Grub has to find the Ubuntu partition via  its UUID. But otherwise, it really makes not difference where Grub is installed.


> Would it impact on the stability of the machine later?
Not at all. But of of course you can only boot if your 500GB drive is plugged in

> but want to get under the hood 
Me too. But I have no clue why you are not able  to boot directly from your Ubuntu drive.

---

### Post by adamg2000 on 2010-01-24
> **meierfra. said:**
> Or are you still booting from the Ubuntu drive?

I didn't change the boot order of the disks - but the read out below indicates that's where it's booting from doesn't it?

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks for 
    (UUID=0a3a530f-af24-4080-a1c2-1a390ee5bb30)/grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ad394

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,992,429     9,992,367  83 Linux
/dev/sda2           9,992,430   234,436,544   224,444,115   5 Extended
/dev/sda5           9,992,493    17,992,799     8,000,307  82 Linux swap / Solaris
/dev/sda6          17,992,863   234,436,544   216,443,682  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ed1d2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0a3a530f-af24-4080-a1c2-1a390ee5bb30" TYPE="ext4" 
/dev/sda5: UUID="b10daee7-b04b-496f-b58c-9944410c7720" TYPE="swap" 
/dev/sda6: UUID="4d13a8c8-9c95-4d02-83fb-3393178918a1" TYPE="ext4" 
/dev/sdb1: UUID="987d01cd-084d-4133-a8f5-b506977e0900" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /boot type ext4 (rw)
/dev/sdb1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/adam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adam)


============================= sda1/grub/grub.cfg: =============================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 4d13a8c8-9c95-4d02-83fb-3393178918a1
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: initrd.img-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-17-generic

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 4d13a8c8-9c95-4d02-83fb-3393178918a1
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-17-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0a3a530f-af24-4080-a1c2-1a390ee5bb30
    linux    /vmlinuz-2.6.31-14-generic root=UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4d13a8c8-9c95-4d02-83fb-3393178918a1 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0a3a530f-af24-4080-a1c2-1a390ee5bb30 /boot           ext4    defaults        0       2
# /home was on /dev/sdb1 during installation
UUID=987d01cd-084d-4133-a8f5-b506977e0900 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b10daee7-b04b-496f-b58c-9944410c7720 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


   9.2GB: boot/grub/core.img
   9.2GB: boot/grub/grub.cfg
   9.2GB: boot/initrd.img-2.6.31-14-generic
   9.2GB: boot/initrd.img-2.6.31-17-generic
   9.2GB: boot/vmlinuz-2.6.31-14-generic
   9.2GB: boot/vmlinuz-2.6.31-17-generic
   9.2GB: initrd.img
   9.2GB: initrd.img.old
   9.2GB: vmlinuz
   9.2GB: vmlinuz.old

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img

---

### Post by adamg2000 on 2010-01-24
> **meierfra. said:**
> 
Did you switch the boot order in the bios? Or are you still booting from the Ubuntu drive?
My apologies for posting garbage, I've just checked the BIOS and it has changed the order for me. Clever bugger.

---

### Post by meierfra. on 2010-01-24
> No boot loader is installed in the MBR of /dev/sda 
Grub disappeared from the MBR of Ubuntu drive.  That's very strange.  Its not easy to erase the MBR and definitely
none of the instruction we gave you could have done that.  

> Clever bugger.   
Maybe your Bios are too clever and that's what caused all your problems.

But since everything is working  right now, it's best to leave your BIOS alone.

---

### Post by adamg2000 on 2010-01-24
> **meierfra. said:**
> Grub disappeared from the MBR of Ubuntu drive.  That's very strange.  Its not easy to erase the MBR and definitely
none of the instruction we gave you could have done that.  


Maybe your Bios are too clever and that's what caused all your problems.

But since everything is working  right now, it's best to leave your BIOS alone.

Well hi all, thanks to all those who posted a response, would be great to know what happened, 'tis a mystery but thanks for helping me to resuscitate my installation.

---

