---
title: "Live USB with persistence in a single FAT partition"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by jchennales on 2007-12-22
Hi,
 I know there are many tutorials about how to make a live persistent usb drive, but all of the ones I saw ask you to repartition the usb drive in two.
 I am playing around, trying to do this same thing while keeping only one partition on the drive, mainly because I would like to be able to use all of the drive's space if needed by deleting the big os images and later on adding them back.
 I think that the main reason for splitting into two partitions in the tutorials is that the fs mounted at /cdrom is mounted readonly and therefore accepts no modifications. I did some snooping at the boot scripts inside the initial ram drive and found that with a single one line change in /scripts/casper I could get the fs holding the os image mounted as read/write owned by the ubuntu user. With this setup I am already able to boot the os from the usb drive and write back to it, so all I am missing is the actual mapping of this writable space to the rest of the filesystem namespace.
 To do this I followed the persistence tutorial to create an ext2 loopback file "casper-rw" in the root of the drive. When I do this, the boot process is interrupted at some point and I end up with a busybox shell. Inside this shell I can see my usb drive, the casper-rw fs mounted and a filesystem.squashfs dir with what seems to be the contents of the big readonly image. It seems that when playing this trick of having the rofs image and casper-rw in the same device one of the boot scripts is getting something it did not expect and the unionfs merging of all the dirs is not done properly. I have looked at the casper and casper-functions scripts and they seem to be able to deal with an already-mounted fs for the persistence file. I cannot catch the error...

If anyone has any ideas or thoughts, please let me know. I am willing to try out things to get this working since I believe it is a much confortable way to achieve the usb perisntent os.

Thanks!

This is the change in the casper script:
```
458c458
<         mount -t ${fstype} -o ro,noatime "${devname}" $mountpoint || continue
---
>         mount -t ${fstype} -o rw,uid=999,gid=999,noatime "${devname}" $mountpoint || continue

```

dmesg does not show any significant errors, I could post it if necessary.

This is the output of mount:
```
none on /sys type sysfs (rw,nosuid,nodev,noexec)
none on /proc type proc (rw,nosuid,nodev,noexec)
udev on /dev type tmpfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /cdrom type vfat (rw,uid=999,gid=999,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /filesystem.squashfs type squashfs (ro,noatime)
/dev/sda1 on /casper-rw-backing type vfat (rw,uid=999,gid=999,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop1 on /cow type ext2 (rw,noatime)
unionfs on /root type unionfs (rw,noatime,dirs=/cow=rw:/filesystem.squashfs=ro,debug=4294967295,delete=whiteout) 
```

If there is anything else I can add just let me know

---

### Post by Kandinsky on 2008-04-11
Type twice exit in the busybox (initramfs prompt) in order to to start the system.

---

### Post by jchennales on 2008-04-12
Thanks! This worked just fine. The system starts up ok, it uses the persistent loopback image on the same partition as the "cd" and everything.
Now, having to do this every time is quite a drag... Do you know why this happens? Is it something I caused with the change to the script or a problem that was there before?

Thanks again for your help!

---

### Post by jchennales on 2008-06-03
Ok,
  I left this hanging for quite a while, I guess the lazy part of me was hoping someone would tell me what was wrong ;)
  Anyway, I came back to this and I did some debugging on the casper script and could trace the abort into busybox to the attempt to mount the partition to look for snapshots.
  The problem is in the function try_mount() in casper-helpers. This function always attempts to remount a device that is already mounted and in doing so, it attempts to set the mount options passed to it. The call that comes from find_files() has a "ro" mount mode since find_files() does not want to disturb anything while looking for files. find_files() should not care, however, if the device is already mounter read-write, so no remount is really necessary.
  I have changed these two files to implement a new parameter to try_mount() to indicate whether to remount if the device is already mounted. I use this parameter when calling try_mount() from find_files() and this should fix the problem.
  I have also added a command line parameter to set the mount options for the device that holds the squashfs image. This is so that I don't change one hardcoded mode for another and this should be usable from a readonly cdrom too. This parameter is called basemountmode and I setup my bootloader to append "basemountmode=rw,uid=999,gid=999" so that the flash drive is mounted read-write and owed by the ubuntu user.
  I have tested this in a virtual machine and it seems to work ok. I have never used snapshots so I cannot test that. I suppose that if someone wanted to include this a lot more testing would be required.
  Well, I've rambled long enough now. My pen drive is working fine, with persistence and with a single FAT partition, so I am happy.
  Here are the changes:

${initrd}/scripts/casper
```
11,12d10
< # Default value for new command line parameter to select the base device mount mode
< mountmode="ro"
52,54d49
<             # New command line parameter to select the base device mount mode
<             basemountmode=*)
<                 mountmode="${x#basemountmode=}" ;;
411,412c406
<     # Removed mode as per online forums. This is a different issue than that of having persistence in a single partition
<     mount ${cowdevice} -t ${cow_fstype} -o rw,noatime /cow || panic "Can not mount $cowdevice on /cow"
---
>     mount ${cowdevice} -t ${cow_fstype} -o rw,noatime,mode=755 /cow || panic "Can not mount $cowdevice on /cow"
471,472c465
<         # The main device that holds the squashfs image needs not be readonly. Changed the fixed "ro" mode for a new init parameter
<         mount -t ${fstype} -o noatime,$mountmode "${devname}" $mountpoint || continue
---
>         mount -t ${fstype} -o ro,noatime "${devname}" $mountpoint || continue

```

${initrd}/scripts/casper-helpers
```
162,166d161
<     # new fourth parameter: it indicates whether a remount is required if the device is already mounted.
<     # This parameter is optional and the default is to do the remount as it was before the change.
<     # The idea is that if the device is already mounted read-write we might not want to try and remount it read-only
<     # In my case this caused a panic and and abort to the busybox shell. My "cdrom" is a flash drive and mounted rw...
<     dorem="${4}"
169,172c164
<         if [ -z "${dorem}" -o "${dorem}" = "Y" ]
<         then
<             mount -o remount,"${opts}" ${dev} $(where_is_mounted ${dev}) || panic "Remounting failed"
<         fi
---
>         mount -o remount,"${opts}" ${dev} $(where_is_mounted ${dev}) || panic "Remounting failed"
214,215c206
<                 # Add the fourth parameter to avoid remounting if the device we want to try is already mounted
<                 try_mount "${devname}" "${snap_backing}" "ro" "N"
---
>                 try_mount "${devname}" "${snap_backing}" "ro"

```

Julian

---

### Post by jchennales on 2008-06-03
The diffs are reversed, just noticed... be careful!

---

### Post by bennmann on 2008-06-11
Newb tutorial please? I love the concept.

---

### Post by jchennales on 2008-06-17
There are plenty of tutorials online so I recommend you read some of those and come to understand the changes I propose. My version is so untested I would not guarantee it or recommend it for someone who does not know what they are doing.
Having said all that, here it goes... I don't want to be mean ;)

```
01 - boot into Kubuntu with the CD
02 - open a console window and enter root mode (K->System->Konsole)
		sudo su
03 - open fdisk on the pen drive (here referred to as /dev/sdX)
		fdisk /dev/sdX
			list partitions, make sure it is the pen drive ("p" command). quit and try another device if it isn't
			delete any existing partitions ("d" command, repeatedly)
			list partitions again, make sure the table is empty ("p" command)
			create primary partition 1, occupying the entire disk ("n" command)
			change type of partition 1 to "c" (Win95 FAT32 (LBA)) ("t" command)
			verify ("v" command)
			write ("w" command)
			quit ("q" command)
04 - create a FAT32 filesystem in the one partition
		mkfs.vfat -F 32 /dev/sdX1
05 - create mountpoint directory
		mkdir /u
06 - mount it and copy the following directories into it: /cdrom/.disk /cdrom/casper /cdrom/preseed
		mount /dev/sdX1 /u
		cp -rp /cdrom/.disk /cdrom/casper /cdrom/preseed /u
07 - go to casper dir
		cd /u/casper
08 - delete initrd.gz and download patched version
		rm initrd.gz
		wget <path_to_initrd.gz>
09 - install GRUB bootloader
		grub-install --root-directory=/u --no-floppy /dev/sdX
10 - create linux writable FS loopback file in FAT32 partition
     (for settings and new apps, size it at will, but don't make it to small - not < 300Mb)
		dd if=/dev/zero of=/u/casper-rw bs=1M count=200
11 - make ext2 filesystem on file (ignore warning, proceed on regular file)
		mkfs.ext2 -L casper-rw /u/casper-rw
12 - go to the GRUB dir
		cd /u/boot/grub
13 - download the menu file
		wget <path_to_menu.lst>
14 - that should be it! - reboot

```

I will see where I can post the patched version of the initrd and menu.lst and will put the links shortly.

Use this at your own risk...

---

### Post by jchennales on 2008-06-17
initrd.gz: [http://www.mediafire.com/?yjzycjz0fmz](http://www.mediafire.com/?yjzycjz0fmz)
menu.lst:  [http://www.mediafire.com/?kv3mznmvy02](http://www.mediafire.com/?kv3mznmvy02)

I don't think these links will work with wget directly. You'll have to download the files with a browser and copy them manually.

If someone finds a better hosting place feel free to copy them there and post new links.

---

