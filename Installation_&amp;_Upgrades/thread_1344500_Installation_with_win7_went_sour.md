---
title: "Installation with win7 went sour"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by rideonXX on 2009-12-03
Loaded Ubuntu 9.10 as second OS.   Win 7 is primary.  Grub just keeps looping back to the Ubuntu choice---so I can't get Win7 to boot---please help.   

Here is the results of running the slick program mentioned in other threads.
Sorry I don't know where to place the markers as I am a noobie noobie.   Thanks
kel

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=c12b7371-0202-447d-b8d3-6f01397f9bd5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub1.97
    Boot sector info:  Grub1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 909995523 on boot drive #1 for 
                       core.img and on partition #8 for /boot/grub. No errors 
                       found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb7 starts at sector 589519859.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc5 starts at sector 40965813.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b8f0b8e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
224 heads, 19 sectors/track, 229504 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x082b1176

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             19   194,724,723   194,724,705   7 HPFS/NTFS
/dev/sdb2         194,724,742   976,769,023   782,044,282   f W95 Ext d (LBA)
/dev/sdb5         194,724,743   589,519,751   394,795,009   7 HPFS/NTFS
/dev/sdb6         960,979,283   976,769,023    15,789,741  82 Linux swap / Solaris
/dev/sdb7         589,519,859   906,953,599   317,433,741   b W95 FAT32
/dev/sdb8         906,953,619   960,979,263    54,025,645  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00002411

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2          40,965,750   140,295,644    99,329,895   5 Extended
/dev/sdc5          40,965,813   140,295,644    99,329,832   c W95 FAT32 (LBA)
/dev/sdc3         140,295,645   488,392,064   348,096,420   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="IDE_CMN STR" UUID="7283-D248" TYPE="vfat" 
/dev/sdb1: UUID="01C9D0FA8960E580" LABEL="DRV1_VOL1" TYPE="ntfs" 
/dev/sdb5: UUID="01C9D0FA8A8F0540" LABEL="DRV1_VOL2" TYPE="ntfs" 
/dev/sdb6: UUID="dd35d208-ff01-4379-b7e2-47f06137cb56" TYPE="swap" 
/dev/sdb7: LABEL="" UUID="1282-92FC" TYPE="vfat" 
/dev/sdb8: UUID="8448d55c-1d77-4a76-830d-1b9b4d62cc75" TYPE="ext4" 
/dev/sdc1: LABEL="MoreStrg" UUID="62D6-58C0" TYPE="vfat" 
/dev/sdc3: UUID="5898E99098E96CC6" LABEL="CMN_STORAGE" TYPE="ntfs" 
/dev/sdc5: LABEL="STORAGE" UUID="1741-11C3" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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


=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set root=(hd1,8)
search --no-floppy --fs-uuid --set 8448d55c-1d77-4a76-830d-1b9b4d62cc75
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
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 8448d55c-1d77-4a76-830d-1b9b4d62cc75
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8448d55c-1d77-4a76-830d-1b9b4d62cc75 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 8448d55c-1d77-4a76-830d-1b9b4d62cc75
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8448d55c-1d77-4a76-830d-1b9b4d62cc75 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 01c9d0fa8960e580
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=8448d55c-1d77-4a76-830d-1b9b4d62cc75 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=dd35d208-ff01-4379-b7e2-47f06137cb56 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


 464.3GB: boot/grub/grub.cfg
 464.3GB: boot/initrd.img-2.6.31-14-generic
 464.3GB: boot/vmlinuz-2.6.31-14-generic
 464.3GB: initrd.img
 464.3GB: vmlinuz

---

### Post by namok on 2009-12-03
You have Grub2 installed in Win7 PBR partition  and this is the reason that you can not start win7.> sdb1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  [COLOR=Red]Grub1.97[/COLOR]
    Boot sector info:  [COLOR=Red]Grub1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 909995523 on boot drive #1 for 
                       core.img and on partition #8 for /boot/grub. No errors 
                       found in the Boot Parameter Block[/COLOR].
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
To correct this you need to restore Win7 bootloader. Follow this link: [URL="http://ubuntuforums.org/showthread.php?t=1014708"]http://ubuntuforums.org/showthread.php?t=1014708
[/URL] and find *'How to restore the Windows Vista or 7 bootloader'.*

---

### Post by rideonXX on 2009-12-03
Thank you very much----I will give it a try.   The treads move fast around here so I really appreciate you responding to this 'old' one.   Happy trails    kel

PS--I'll post the results but I'm a real nooobie at this stuff so it may take me a while today.

---

### Post by rideonXX on 2009-12-03
OK----I did that and it worked great---and easy, even for a nooobie!   THANKS A LOT namok!  

Now I'm able to have Win7 but need a functional loader so that I can use and explore the ubuntu world.  Any suggestions will be greatly appreciater

---

### Post by darkod on 2009-12-03
From the data you posted your Ubuntu 9.10 install is on /dev/sdb8. Boot with the ubuntu cd, select Try Ubuntu option and in terminal run:
sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That will install grub2 on the MBR of sdb (the second drive) and will create grub menu with ubuntu and win7 entries. Make sure in BIOS the sdb drive is first in boot order.

---

### Post by rideonXX on 2009-12-03
Thank you for your response and suggestion Darkrod---much appreciated.   

I tried it and here is the response I got-------

o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sdb8 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$ 

I am getting this computer ready to give to my adult daughter as hers is going bad and is old.  I built this on 6 months ago and its been sweet---so off it goes.  I will be putting another drive in to replace one I am taking out with all my data on it---so perhaps it would be best to install ubuntu on that drive and then update the grub after I re-attach the drive containing Win7.  That is a good way to set up a duel boot machine if I am understanding several of the posts on this board.   Is that your opinion as well?

Thanks again---the help on here is great.   Good folks-----happy trails   kel

---

### Post by darkod on 2009-12-03
Something strange has happened. :(
As for adding the new drive, actually my personal opinion is that you get all your hardware together and only then install any type of OS. It needs to know the hardware it's got. I do not recommend unplugging windows disk for example, installing ubuntu on another disk and then replugging the windows one back. But that doesn't mean it wouldn't work that way. Just my personal opinion you need to have all your hardware already attached and working fine when installing OS.
If you decide to leave the drives in, just before starting the ubuntu install make the ubuntu drive first in BIOS boot order, not the windows one.

---

### Post by rideonXX on 2009-12-03
Thanks for the response and your take on the matter.

If I leave the drive with Win7 hooked up, and make the drive ubuntu will be on as the 1st choice in the Bios, what do I put as the mounting point while during the partioning step?  Please excuse if this is a really silly question.  As I mentioned before, I am a nooobie and haven't found that information in the reading of threads.  

I really do appreciate you sharing your expertise----------happy trails, kel

---

