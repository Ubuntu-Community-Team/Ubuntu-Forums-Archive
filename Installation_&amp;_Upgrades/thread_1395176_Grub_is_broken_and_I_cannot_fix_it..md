---
title: "Grub is broken and I cannot fix it."
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by slugicide on 2010-01-31
When I try and log in to my newly installed OS I get stuck in some sort of grub wasteland. rescue:grub> to be exact. I've scoured the Web for help and made posts in multiple places, but no one wants to help. 
Anyone want to take the time?

---

### Post by Sef on 2010-01-31
1) What version of Ubuntu are you using?

2) If Karmic, how did you obtain it: upgrade or clean install?

---

### Post by drs305 on 2010-01-31
Have you referred to the booting from the command line section of the Grub 2 community doc?  [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

If you don't want to try fixing it with those instructions, we can help but need some information. Running this boot info script and posting the RESULTS.txt contents will tell us what we need to know to fix your system. You can run it from the LiveCD. Please post the contents within 'code tags' (use the # symbol in the menu).
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by slugicide on 2010-01-31
> **Sef said:**
> 1) What version of Ubuntu are you using?

2) If Karmic, how did you obtain it: upgrade or clean install?

I bought a new SSD and put Ubuntu on it via USB. When that left me stuck at grub I thought maybe something was wrong with the USB image so I downloaded Mint, put it on the usb and installed that, but when I restarted I was left at the same place: rescue:grub>

---

### Post by slugicide on 2010-01-31
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15434883072 bytes
255 heads, 63 sectors/track, 1876 cylinders, total 30146256 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4ec50ed

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,772,414    28,772,352  83 Linux
/dev/sda2          28,772,415    30,137,939     1,365,525   5 Extended
/dev/sda5          28,772,478    30,137,939     1,365,462  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001ecbb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,849,447     7,849,386   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       fdf1f572-f7ae-41c4-bbcf-f2ff7fabb818   ext3                                     
/dev/sda1        dce96c70-3566-4538-af37-aba37262abc9   ext4                                     
/dev/sda5        84f6a0f1-6d22-4dbf-b1b2-c3c801546d54   swap                                     
/dev/sdb1        22D4-755F                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda1)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dce96c70-3566-4538-af37-aba37262abc9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=dce96c70-3566-4538-af37-aba37262abc9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dce96c70-3566-4538-af37-aba37262abc9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=dce96c70-3566-4538-af37-aba37262abc9 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=dce96c70-3566-4538-af37-aba37262abc9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=84f6a0f1-6d22-4dbf-b1b2-c3c801546d54 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by darkod on 2010-01-31
Hmmm, it looks fine as far as I can see. It should boot your Linux Mint, since that's what you have right now on /dev/sda.

---

### Post by slugicide on 2010-01-31
> **darkod said:**
> Hmmm, it looks fine as far as I can see. It should boot your Linux Mint, since that's what you have right now on /dev/sda.

Unfortunately, when I try and boot I land at rescue:grub>.

---

### Post by darkod on 2010-01-31
I know this is probably not what you want to hear, but if you plan to use ubuntu and not linux mint would you mind doing another ubuntu install on the SSD using the Erase and use whole disk option?

I suspect there might be something messed up on the hdd. If even after that ubuntu doesn't boot, reinstall grub2 using the 9.10 cd and Try Ubuntu option, in terminal execute:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by slugicide on 2010-01-31
I reinstalled Ubuntu using the erase disk option. When I restarted I landed on the rescue:grub> screen. It says

```
rescue:grub> unaligned pointer 0x89bc7d89
Aborted. Press any key to exit.
```

---

### Post by slugicide on 2010-01-31
When I go into the live CD and do the grub install as you suggest I get the error
```
cp: cannot stat 'mnt//boot/grub/raid.mod': Input/output error
```

---

### Post by darkod on 2010-01-31
raid? You don't have any weird raid setting enabled in BIOS right? Or raid meta data (settings) on your hard disk?

---

### Post by slugicide on 2010-01-31
I just poked around the BIOS and there was nothing weird. I reset everything to Dell's default, but I don't think was changed. When I restarted I ended up at the rescue:grub> screen again.

---

### Post by darkod on 2010-01-31
I don't know too much about this subject but I definitely don't like that message ending with raid.mod. What would that file be doing in /boot/grub in the first place?

The only way that I know to get rid of raid settings, provided that is the problem, is:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

But I can't be sure if you would need to reinstall grub2 again to /dev/sda with the same commands or even reinstall whole ubuntu again, because this previous install might have been done while raid settings existed on the disk.

And the above is a big question mark since I'm not even sure there are raid settings on the hdd. But the first command I quoted now should let you know if there is any raid data to get rid of.

---

### Post by slugicide on 2010-01-31
This is the results of those commands:

```
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda
no raid disks and with names: "/dev/sda"
ubuntu@ubuntu:~$ sudo apt-get remove dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dmraid
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 176kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120318 files and directories currently installed.)
Removing dmraid ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/initrd.img': No such file or directory
cp: cannot stat `/vmlinuz': No such file or directory
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
cp: cannot stat `/vmlinuz': No such file or directory
ubuntu@ubuntu:~$ 

```

---

### Post by darkod on 2010-01-31
As we thought, no raid settings were present.
Sorry, these errors are beyond my knowledge. :( I have no clue why this is happening even when you install from scratch.

---

### Post by slugicide on 2010-01-31
Ouch. Thanks for your help. Hopefully someone will come along who can make sense of this.

---

### Post by slugicide on 2010-02-01
So, anyone else know what I should do here?

---

### Post by meierfra. on 2010-02-01
I'm not sure, but you might be hit by this bug:

[https://bugs.launchpad.net/netbook-remix/+bug/430333](https://bugs.launchpad.net/netbook-remix/+bug/430333)
[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852)

I only glanced over  those two reports  and can't give you any concrete advice yet.  But I'll have a  closer look later today.

---

### Post by slugicide on 2010-02-01
That'd be great, thanks!

---

### Post by meierfra. on 2010-02-01
Just to get started.  Boot from your LiveCD and run a file system check:

```
sudo umount /dev/sda1
sudo e2fsck -yfvc /dev/sda1
```

---

### Post by slugicide on 2010-02-01
```
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  127698 inodes used (14.20%)
      75 non-contiguous files (0.1%)
      68 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 12/12/12
         Extent depth histogram: 106643/3
  578872 blocks used (16.10%)
       0 bad blocks
       1 large file

   86394 regular files
   14450 directories
      68 character device files
      26 block device files
       0 fifos
       6 links
   26754 symbolic links (20944 fast symbolic links)
       0 sockets
--------
  127695 files

```

---

### Post by meierfra. on 2010-02-01
Your "e2fsck" results look fine. I read through various  bug reports and also googled some of your other error messages. But I was not  able to find anything which looked promising. It seems that the problem is caused by Ubuntu/Mint 9.10. So I recommend to install Ubuntu 9.04 or Mint 9.04.  Make sure to create a separate home partition. Then  it will be fairly easy to install 10.04 in  April.

---

### Post by slugicide on 2010-02-01
Thanks, I'll try that.

---

### Post by slugicide on 2010-02-01
That seems to have done it. The older version of Ubuntu installed just fine. There must be some bug with Karmic and the 16gb SaberTooth AA Mini PCIe SSD.

Thanks again.

---

