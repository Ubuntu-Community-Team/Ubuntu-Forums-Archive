---
title: "rebuilding/fixing a partition."
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by ulao on 2013-02-07
I have a situation where I dont know how the old tables were set up. Though the OS will not boot as grub can not find the drive. I believe the initial grub was over written. 

I ran testdrive and was able to find the os partition ( LVM ) and I backup up all my files. Currently my tables are like so.

Disk /dev/sda - 20 GB / 19 GiB - CHS 2637 240 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33    33  11 59     497664
 2 P Linux LVM               33  44 29  2637  49 33   39372800

This does not boot and I believe that its because of the grub. I dont know a thing about grub nor how linux sets up partition tables. I know the LVM is how it was. I do not know why I choose LVM but my files are all there. I just need help making this boot.

I tried removing the * ( bootable primary ) and chaning the LVM to a * but still no boot. This is how I recovered my files from another box. So I put things back the way they were ( as shown above ).

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by darkod on 2013-02-07
If you are absolutely sure the LVM is fine, it will be easy. Do you know maybe if the small sda1 partition was your /boot partition or not?

If it was, you will have to add one more command, if not, ignore it.

Get an ubuntu live cd with the same version you have installed on the machine. Boot into live mode and open terminal. First add the lvm2 package (it's not included in the live cd) and activate the LVM:
```
sudo apt-get install lvm2
sudo vgchange -ay
```

That should list all LVs activated including your root LV, like /dev/VGname/LVname.

To install grub onto /dev/sda:
```
sudo mount /dev/VGname/LVname /mnt #(mount the root LV, use the correct VGname and LVname)
sudo mount /dev/sda1 /mnt/boot #(mount sda1 if it was your /boot, if not ignore this)
sudo grub-install --root-directory=/mnt /dev/sda
```

That should sort it out, provided everything is really good with the LVM.

---

### Post by ulao on 2013-02-07
The drive is tip top, and the OS was great till I tried to ghost it over to another drive. For what ever reason ( maybe my mistake ) it crippled it. Again, my guess is the grub was over written but I dont see why ghost would do that? I have messed with drive jumpers but dont see how that plays a role. I dont think trying to understand the unknowns will help much here. Best to focus on the knowns.

Yes the LVM is intact and all files are there. 
I only have a windows box and I use a few apps to see the drives.
The old system would boot right in to the os, I dont recall seeing a grub. So its possible that grub partition was not there and maybe ghost copped backwards? 

So from what I gather both of your suggestions are to run a live boot to do the work? If so when I boot with a live CD my sda will be that drive since no other drives are in the system. Guessing my LMV will be sda1

---

### Post by darkod on 2013-02-07
No, your LVM will not be sda1. Look above in your own post where you mentioned testdisk results. You pasted that before the LVM partition (/dev/sda2) there is a small /dev/sda1 partition.

That's why I mentioned if that is /boot you have to mount it too before running grub-install. You should know how your system is installed.

As for seeing grub or no, when you have only ubuntu it usually doesn't show. There is no second OS to select so what's the point to delay booting by showing grub menu. That doesn't mean you have no grub. You need to have a bootloader or nothing will boot.

Also, for servers the grub menu might show even when it's the only OS but the default delay is only 3sec then it starts booting ubuntu. So, if you are not carefully looking these 3 seconds, you can miss it too.

---

### Post by ulao on 2013-02-07
Thx for the explanation. I installed 10.10 when it was out so, yeah I dont remember how I set t up. 

One more question if I may. If I go ahead and install ubuntu on a new drive could I just copy my backed up files over the existing os? Just never tried that in linux. Would it work in theory? I dont recall the file system i think it was ex3 or 4.

---

### Post by darkod on 2013-02-08
The file system will not matter much, since it will copy from "old" to "new" partition.

But it depends on the type of files you copy. If you copy personal files like videos, photos, music, etc, that are not operating system files, no problem. You can copy them anywhere.

If you have some system files you want to copy so that you don't need to configure the same things on the new OS, in most cases it should also work. But sometimes it depends on the exact program that the file belongs to, and it might not work by simply copying.

If you don't remember whether /dev/sda1 is boot or not, you can try the grub2 install commands first without the /dev/sda1 mount command, and if it doesn't work, try with it.

Also, you can check becasue in /etc/fstab inside the LVM you would have an entry for /boot or not. From live mode you can do this by activating the LVM with the two commands written before, then mounting the root LV and listing your fstab like:
```
sudo mount /dev/VGname/LVname /mnt
cat /mnt/etc/fstab
```

That will list fstab from inside the LVM root LV. If you see a line starting with:
/dev/sda1 /boot.....

then you are using sda1 as boot. If not, you are not.

---

### Post by ulao on 2013-02-08
Ok not having much luck with the copying of files. So I want to try an fix the bad drive ( your first suggestion ) however I cannot preform those steps because as I mentioned the drive is not in working order. All I can see in linux liveCD is the grub partition. 

I saw this
[http://forums.fedoraforum.org/showthread.php?t=120445](http://forums.fedoraforum.org/showthread.php?t=120445)

I wonder if this is my issue. This also make me wonder if I just need to edit my grub to make things work again. Since I can boot to the grub I can make edits.

here is my current grub.cfg
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
insmod ext2
set root='(spawnlinux-root)'
search --no-floppy --fs-uuid --set=root b69b180c-1f1e-4b0f-8bdb-bb42d8e1eac6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
  set locale_dir=($root)/grub/locale
  set lang=en_US
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
if background_color 75,75,75; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-3.2.0-26-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 3.2.0-26-generic-pae ...'
	linux	/vmlinuz-3.2.0-26-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-26-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-3.2.0-25-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 3.2.0-25-generic-pae ...'
	linux	/vmlinuz-3.2.0-25-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-3.0.0-19-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-3.0.0-19-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 3.0.0-19-generic-pae ...'
	linux	/vmlinuz-3.0.0-19-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-19-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-3.0.0-17-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-3.0.0-17-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 3.0.0-17-generic-pae ...'
	linux	/vmlinuz-3.0.0-17-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-17-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-3.0.0-16-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 3.0.0-16-generic-pae ...'
	linux	/vmlinuz-3.0.0-16-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-3.0.0-15-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 3.0.0-15-generic-pae ...'
	linux	/vmlinuz-3.0.0-15-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-15-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-2.6.38-13-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-2.6.38-13-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 2.6.38-13-generic-pae ...'
	linux	/vmlinuz-2.6.38-13-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-13-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-2.6.35-23-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/vmlinuz-2.6.35-23-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-2.6.32-24-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/vmlinuz-2.6.32-24-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-2.6.32-23-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/vmlinuz-2.6.32-23-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux	/vmlinuz-2.6.32-21-generic-pae root=/dev/mapper/spawnlinux-root ro   quiet
	initrd	/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/vmlinuz-2.6.32-21-generic-pae root=/dev/mapper/spawnlinux-root ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 166d8ea3-4109-48f5-90d4-4b880286e9c6
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

anyway to convert this LVM to a normal ext4 ?

---

### Post by darkod on 2013-02-08
What do you mean "not in working order"? If the system doesn't boot because of messed up grub, that's not a huge problem.

But a disk not being in working order means hardware failure which is very different problem. But I guess the disk works fine, otherwise how did you get the grub.cfg from it?

I already suggested what to do, but it seems we have to go step by step since you are not doing it.

Boot into live mode, open terminal and post the output of:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/spwnlinux/root /mnt
cat /mnt/etc/fstab
```

Post the full output of those commands. After that I will probably be able to give you exact steps.

---

### Post by ulao on 2013-02-08
I though you were referring to the dev and mout of the LVM disk. I follow you now.

```

ubuntu@ubuntu:~$ sudo vgchange -ay
  2 logical volume(s) in volume group "spawnlinux" now active
ubuntu@ubuntu:~$ sudo mount /dev/spawnlinux/root /mnt
ubuntu@ubuntu:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/spawnlinux-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=166d8ea3-4109-48f5-90d4-4b880286e9c6 /boot           ext2    defaults        0       2
/dev/mapper/spawnlinux-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
ubuntu@ubuntu:~$ 


```

---

### Post by ulao on 2013-02-08
accidental dup post

---

### Post by darkod on 2013-02-08
You see, /dev/sda1 really is your /boot partition. If you rebooted you will have to again do the LVM activation and then continue with the second block of commands:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/spawnlinux/root /mnt
```

If you didn't reboot yet, continue from here:
```
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

That should sort it out if it was only grub2 missing on the MBR.

If you have another issue with the OS that's different topic. :)

---

### Post by ulao on 2013-02-08
I did as you suggested, no error during the grub install. I rebooted and this time it found something to boot to. It immediately clears the screen and turns off the monitor and  goes no where. The drive is not even seeking but the system is not froze as numlock still turns on and off the numlock LED.

I know you said this would be another topic but I just want to make certain there is nothing more to check here. Doing a cat on fstab shows the same info but that may be as expected, still learning.

---

### Post by darkod on 2013-02-09
Unfortunately it seems you have another issue now. Maybe as a result of the earlier problems when the whole partition table was gone. Depending how the problem happened, many things could be affected.

At this point it might be a better solution to copy all your personal data (you already said you copied it), make sure you have all of it, to some king of external storage like usb hdd or another hdd.

Then do a new clean install and put your data back. You might need to configure some settings so the system will work like the one you had before, but this would probably take less time then to try fixing this.

If you want to keep on troubleshooting, try holding Shift during boot so that the grub menu shows. Then highlight the first ubuntu entry and press 'e' for edit. In the boot lines using the arrows keys go to the end of the line starting with linux and delete the 'quiet splash' parameters.
Press Ctrl+X or F10 to boot.

That should intend booting and show you the text scrolling. Be ready and note down where does it get stuck, does it show any specific error messages on screen, etc. Googling those error messages might help find the problem.

---

### Post by ulao on 2013-02-09
Wow great, thx for all the help. I actuly did that last night and ran in to an issue see here ( I guess my post didnt commit?)
[http://ubuntuforums.org/showthread.php?p=12500443#post12500443](http://ubuntuforums.org/showthread.php?p=12500443#post12500443)

If I get anywhere with the boot Ill post that here.
Quick update on the booting issue..So get this.

I boot
hold shift
"GRUB loading..."
monitor goes off. 
starting to wonder I hit enter
continues to boot
monitor comes on 
OS comes up

WTF? Any way to edit the GRUB in the OS and may it auto boot, since I can even seen the friggen screen LOL.

---

### Post by darkod on 2013-02-09
It seems the monitor is not supporting the video during the grub boot menu. One thing you can do is set basic resolution just for the grub menu.

But after ubuntu tries to boot, what happens? You said just now OS comes up?

Does that mean uubntu is booting successfully or not? I thought that no...

---

### Post by ulao on 2013-02-09
Oh sorry, yes I'm back up. I guess it just sits at the grub screen. How do you change the grub res?

---

### Post by darkod on 2013-02-09
If you are back up, it's easy. That's why I asked.

Open the file /etc/default/grub for editing with:
gksu gedit /etc/default/grub

Find the line saying something similar to GFX_MODE=640x480 and uncomment it (remove the # in front). Save and close the file.

In terminal run:
sudo update-grub

to create new grub.cfg. That will change the resolution to 640x480 but only for the grub boot menu, your resolution in ubuntu will be the same.

EDIT PS: Note that if you have only ubuntu the menu doesn't show by default. You have to hold Shift right after the motherboard POST ends so that grub menu shows. If you have dual boot, it shows by default.

---

### Post by ulao on 2013-02-09
ok, after doing so I now have a blank screen with a flashing cursor. The monitor no longer goes off and hitting enter is no longer need. It boots on its own. I'm not even going to make scene of that. Thx for the help.

PS: have to add this for shyts and grins. So once my disc was back up I tried to close it with clone zilla and it failed. I know I choose the source and target correctly. It some how modified my grub ( saying it found two of them ) and not I have a grub when I boot.

---

