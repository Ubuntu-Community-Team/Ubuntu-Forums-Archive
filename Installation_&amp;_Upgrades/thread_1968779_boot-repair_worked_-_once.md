---
title: "boot-repair worked - once"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2012-04-29
Hi,

I just abandoned trying to setup 2 SSDs as RAID1 and LVM striped. I managed to dd my failing hdd onto a partition on a new hdd. I used boot-repair to reinstall grub and reboot, I also ran fsck from the livecd to fix the errors dd'd across from my failing hdd. 

But the 2nd reboot failed, so I pulled all disks out of the machine except this new one. The partition is in the middle of the disk and is about 500MB. boot-repair says it completes OK, but the disk boots to the grub> only. Ubuntu is proving to be a nightmare, I have spent 4 days friggin around trying to get my development machine working. 

[http://paste.ubuntu.com/955370/](http://paste.ubuntu.com/955370/)

Ideas?

---

### Post by darkod on 2012-04-29
The /boot/grub/grub.cfg file seems empty. You can try entering with chroot and recreating it from live mode:
```
sudo mount /dev/sda2 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the install with root permissions:
```
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and see if that works.

---

### Post by olddave1 on 2012-04-30
Hi,

I tried your approach. Sionce it is essential I keep my home dir I resized my /dev/vgssd to 13GB and created a lv of 103GB onto which I copied my old /home.

So now have /dev/md0 and 2 logical volumes. I tried an install, but Ubuntu installation does now show my /dev/vgssd/lvhome and /dev/vgssd/lvssd nor does it show my /dev/md0. It shows /dev/sda /dev/sda1 /dev/sda2 /dev/sdb /dev/sdb1 /dev/sdb2, that is all.

So wondering how you are able to chose the destinations of the / (to /dev/vgssd/lvssd) /boot (to /dev/md0) amd /home (to /dev/vgssd/lvhome)?

---

### Post by darkod on 2012-04-30
If you are using the live cd did you remember to install mdadm and lvm2 first and activate the devices?

---

### Post by olddave1 on 2012-04-30
A dooh moment, I had installed the mdadm and lvm2 packages but not started the devices.

Last question, I hope... Since I have my new /dev/vgssd/lvhome marked to hold the /home partition and since it already has my entire home content (which I cxopied acorss earlier), same if I use my username in the install will it damage any of my current files which are under the same user name? All partitions are not marked for format.

---

### Post by darkod on 2012-04-30
The general idea of reusing /home is to use the same username (best to be the first user created in the old install), reuse the /home partition without formatting it.

I think it should be fine.

This case has got me so interested that I started preparing a test environment in virtual box, I just need some spare time to do it, hopefully today. I want to test the exact situation with software raid /boot and striped LVM for root.

---

### Post by olddave1 on 2012-04-30
Hi,

Well after installing and selecting the 1st SSD as the 1st boot device in the bios I rebooted. Using the same username and password as I had on my old disk.

It boots to the screen that you select the kernal to use, I select the top one, and it goes to a purple screen with noting on it. I'll now boot to livecd and try to use boot-repair to repair this boot.

---

### Post by oldfred on 2012-04-30
You now may be past grub2 booting and into Ubuntu booting and most often video issues or perhaps other parameters. Most video issues are resolved with a nomodeset to get you booted. If nVidia, you then can install the nVidia driver as Ubuntu will offer it.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu


I only have one SSD. I installed using an ISO on my other hard drive directly booted with grub2's loopmount & I knew I need the nomodeset parameter so I include that. I partitioned my SSD in advance with gpt, with both efi & bios_grub partitions as I use BIOS now, and hope to have a new UEFI system soon. My install took less than 15 minutes to a working system. Aother half hour to basic configuration and I still am modifying configuration as I go.
What real benefit do you expect from RAID for SSDs? RAID was always for servers to allow multiple users faster access. But with SSDs you now have filled the capacity of SATA and cannot get much more speed. Plus on a desktop you cannot type any faster, your Internet downloads will not be faster. I consider it a luxury just to have an SSD as it boots faster, but I barely notice programs loading faster as they were so quick before. Of course my data is still on a rotating drive so that has not changed.

---

### Post by olddave1 on 2012-04-30
Hi,

I replaced splash and quiet with nomodeset and then pressed Ctrl-X I still get a purple screen, restarted and tried F10, same deal. Any other ideas?

I also tried leaving the quiet splash and putting nomodeset after them and before the vt.handoff=7, and tried both versions without having the vt.handoff=7 at the end of that line

Holding down the Shift key during boot did not seem to make a difference? Not sure what we are doing this for.

On the subject of SSDs I have lvm striped for speed similar to RAID0 but with trim operable. I have lots of compilations of code and unit tests to run, disk speed is paramount.

---

### Post by oldfred on 2012-04-30
If you remove quiet & splash you should see each task loading on a command line, not a purple screen?

If you only have one system, grub menu is not shown and you have to use shift to get menu to show.

Does alt-f2 show anything? That should just take you to terminal mode.

Sometimes boot is real slow due to other issues, one user said it booted after 5 minutes. I am surprised he waited that long.

---

### Post by olddave1 on 2012-04-30
This is not about video driver I think. I booted into recovery mode, I get this:

"Gave up waiting for root device. Common problems:
 - Boot args (cat proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/vgssd-lvssd does not exist. Dropping to a shell!"

So does this mean unbuntu is not starting lvm2 when it should?

---

### Post by olddave1 on 2012-04-30
This is not about video driver I think. I booted into recovery mode, I get this:

"Gave up waiting for root device. Common problems:
 - Boot args (cat proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/vgssd-lvssd does not exist. Dropping to a shell!"

So does this mean unbuntu is not starting lvm2 when it should?

---

### Post by darkod on 2012-04-30
Dave, I just did it. The same config you are trying to do from that OCZ forum post.

I configured virtual box machine with two hdds (15GB and 10GB, imagine the first one is 10GB too).

I followed that procedure, and only did a small change. After creating the /dev/md0 device I didn't create ext3 filesystem on it directly, as in that post.
What I did was to create partition table and partition with parted first, then format that partition as ext4:
sudo parted /dev/md0
mklabel msdos
unit MiB
mkpart primary 1 200 (my linux raid partitions for /boot are 200MB)
quit
sudo mkfs.ext4 /dev/md0p1 (with partition on it it has p1 at the end, so I created ext4 filesystem with this command)

On the virtual HDDs I created msdos table, 200MB linux raid partitions, and then the rest up to 10GB lvm partitions.
Configured the /dev/md0 and striped /dev/vgssd/lvssd just as in that post.

Grub2 install finished OK, it installed on both /dev/sda and /dev/sdb by itself without my intervention.
Strangely enough first reboot after install failed but with some VBox error which might not be related to the setup. But second try worked without any special parameters, etc.

If you want me to post any more data from the virtual machine, let me know. I have attached two screenshots.

So, in general, this should work. I have no idea if there is something related to your particular machine.

EDIT PS: I used live mode with mdadm and lvm2 added to prepare all setup, then used alternate cd to install. It recognized the raid and lvm devices without problem. I used the manual partitioning of course.

---

### Post by olddave1 on 2012-04-30
Hi,

The first screenshot will not show. Also since I have already installed can't I just put /boot on /dev/mdo? I mean I have it on another disk. I could do grub-install and then cp /boot across? Do I have to re-install the whole thing? When you say Grub2 installed OK, do you mean the installer unbiquity did it or you did the sudo grub-install?

---

### Post by darkod on 2012-04-30
Both screenshots show when I try them.

I added a PS that I prepared the configuration in live mode, like in the tutorial, and then used the alternate cd to install. In the manual partitioning it was the md0 and vgssd-lvssd devices automatically, so I just configured them as /boot and /.

Towards the end of the install, when it asked if I want the bootloder to the MBR, I just said Continue as usual, the message itself said something like "running grub-install to /dev/sda and /dev/sdb".

It installed on both disks by itself, without me telling it to install to both disks or running any manual commands. The installer finished the job.

I is aware of md0 device and installs grub to both disks I think.

---

### Post by darkod on 2012-04-30
Yes, you should be able to copy the content of /boot to the md0. Run the grub-install after, not before the copy.

But since you are trying to move an existing system, be careful how do UUIDs hold you back. When copying /boot it will of course copy grub.cfg with the same content which might have wrong UUIDs from the old system. Grub-install only installs it on the MBR, doesn't change anything in the grub.cfg and doesn't recreate it.
Also make sure you pay attention to /etc/fstab if moving your old system.

That's why I suggested a test run, first to see if a clean new install will work in this configuration. If it does, you know for sure that the configuration works. This will be a huge step since right now you are not sure if the problem is with the configuration, or somewhere else.

If the copied system doesn't, then your issue is with the moving of the system, not the md0/LVM setup. Try to eliminate the possible problems one by one.

---

### Post by olddave1 on 2012-04-30
Thinking about this, the fact I get the boot menu up suggests that it is reading /dev/md0 fine? Also the error message relates to /dev/mapper/vgssd-lvssd so it looks to me like when it tries to read /, on that LVM device, that it fails.

Here is the setup, I am going to reinstall, safer that way. I don't think the result will be different, because the lvm is setup identically to before

ubuntu@ubuntu:~$ sudo parted /dev/md0 print all
Model: Linux Software RAID Array (md)
Disk /dev/md0: 262MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  252MB  251MB  primary  ext4


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  263MB   262MB   primary               boot
 2      263MB   60.0GB  59.8GB  primary


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  263MB   262MB   primary               boot
 2      263MB   60.0GB  59.8GB  primary


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  212GB   212GB   primary  ntfs
 2      212GB   774GB   562GB   primary  ext4            boot
 4      774GB   790GB   16.8GB  primary  linux-swap(v1)
 3      790GB   1000GB  210GB   primary  ext4


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/vgssd-lvhome: 103GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  103GB  103GB  ext4


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/vgssd-lvssd: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  16.1GB  16.1GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by darkod on 2012-04-30
Here is mine, just so you can see the LVM is really striped.

You can try the same thing I did, creating partition on /dev/md0 instead of using the device directly. For me it was logical to create msdos table and one partition on it, since /dev/md0 is the device itself, like a hdd. You don't use it before you create a partition table and partitions.

Maybe it does make a difference since all boot files are there.

PS. I just did all the updates and also rebooted it few times, to make sure it will boot more than once. :) It does.

---

### Post by olddave1 on 2012-05-01
I reinstalled following your instructions on the /dev/md0, as I suspected it made no difference, for reasons unknown I get that same
ALERT! /dev/mapper/vgssd-lvssd does not exist. Dropping to a shell!"
message as before...

So I gave up, and used the spinning HDD I borrowed from my wife and setup a partition for /home and used the one I had previously setup of /. The install stalls at the "Restoring previous packages...". I cannot believe how flaky the installer ubiquity is. So now a week of effort and I still do not have my dev machine back, getting mighty pissed off with Ubuntu. Lucky I have Win 7 on my laptop.

Since my setup with the SSDs seems to be equivalent to yours no idea how to troubleshoot the mapper/vgssd-vlssd not being available.

---

### Post by darkod on 2012-05-01
The only thing on my mind is if it's not being brought online fast enough. Maybe a boot parameter like 'rootdelay=30' could help. That would wait a little before looking for /.
You can also try with 60 and 90.

Other than that, I'm drained of ideas. :)

---

### Post by olddave1 on 2012-05-01
Well, by formatting my / partition onto the spinning HDD it installed. But despite me specifying that I wanted my /home on a separate partition, no format, where I had previously cp all my files, it decided not to do that and so I have new install of 11.10. Now moving my /home partition and replace the empty one they gave me. Ubiquity is seriously crap.

---

### Post by darkod on 2012-05-01
Oh come on, I am doing clean installs since 9.10 and it has never ignored attaching my existing /home partition. You either made a mistake during the install, or you have some corrupted install media... I don't know what to say...

If you used the manual partitioning and selected the correct options, it should attach the partition you tell it to for /home.

---

### Post by olddave1 on 2012-05-02
You are right, it did create the /home on a separate /dev/sdc3 partition. The problem was that I had read instructions to put /home on that partition, this was not correct, you copy the users directories directly into that partition, there is no longer a /home directory at the base. Also note that since you had to do the copy as sudo all files are then owned by root, so I had to "sudo chown -R david:david /home/david"

So I have a working machine on a spinning HDD, which I have to give back at some point. I give up on the SSDs, cannot find an effective way to debug why Ubuntu does not seem to mount /dev/mapper/vgssd-lvssd (not even sure how thise relates to the lv called /dev/vgssd/lvssd). Maybe add vgchange -a y /dev/vgssd to the boot.cfg?

---

### Post by darkod on 2012-05-02
Well, since now you did the install without LVM (right?) there will not be many option to check why. The only thing in my mind, is to look at the menu entries in /boot/grub/grub.cfg. When using LVM it should load the module in the first lines of the menu entry, something like 'insmod lvm'.

Other than that, I don't have many clues. It might be some sort of issue with your hardware, just one of those things.

---

### Post by olddave1 on 2012-05-03
Here is the grub.cfg. It does insmod lvm at the start, but I note not in the "Ubuntu, with Linux 3.0.0-12-generic" section?

```
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
  insmod video_bochs
  insmod video_cirrus
}

insmod lvm
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(vgssd-lvssd)'
search --no-floppy --fs-uuid --set=root 1658fd81-31a4-490d-92e5-f9ab28401687
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod raid
  insmod mdraid09
  insmod part_msdos
  insmod part_msdos
  insmod part_msdos
  insmod ext2
  set root='(md0,1)'
  search --no-floppy --fs-uuid --set=root a26a1220-9bdd-4d3a-b987-a46ad25c0b22
  set locale_dir=($root)/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0,1)'
    search --no-floppy --fs-uuid --set=root a26a1220-9bdd-4d3a-b987-a46ad25c0b22
    linux    /vmlinuz-3.0.0-12-generic root=/dev/mapper/vgssd-lvssd ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0,1)'
    search --no-floppy --fs-uuid --set=root a26a1220-9bdd-4d3a-b987-a46ad25c0b22
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=/dev/mapper/vgssd-lvssd ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0,1)'
    search --no-floppy --fs-uuid --set=root a26a1220-9bdd-4d3a-b987-a46ad25c0b22
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0,1)'
    search --no-floppy --fs-uuid --set=root a26a1220-9bdd-4d3a-b987-a46ad25c0b22
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz root=/dev/sdc2
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz root=/dev/sdc2
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz root=/dev/sdc2
    initrd /initrd.img.old
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sdc2
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /boot/vmlinuz-3.0.0-14-generic root=/dev/sdc2
    initrd /boot/initrd.img-3.0.0-14-generic
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /boot/vmlinuz-3.0.0-15-generic root=/dev/sdc2
    initrd /boot/initrd.img-3.0.0-15-generic
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /boot/vmlinuz-3.0.0-16-generic root=/dev/sdc2
    initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /boot/vmlinuz-3.0.0-17-generic root=/dev/sdc2
    initrd /boot/initrd.img-3.0.0-17-generic
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz root=/dev/sdc2
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz root=/dev/sdc2
    initrd /initrd.img
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz root=/dev/sdc2
    initrd /initrd.img.old
}
menuentry "Ubuntu 11.10 (11.10) (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos2)'
    search --no-floppy --fs-uuid --set=root 41953c50-b4b0-4c5f-9970-52f50f599ab8
    linux /vmlinuz.old root=/dev/sdc2
    initrd /initrd.img.old
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
```

---

### Post by oldfred on 2012-05-03
Added code tags to make it a bit easier to review.

It also is strange that you have the insmod  part_msdos three times, I have never seen that. But I do not know LVM.

---

