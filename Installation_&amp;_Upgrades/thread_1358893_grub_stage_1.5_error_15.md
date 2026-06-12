---
title: "grub stage 1.5 error 15"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by idom on 2009-12-18
Hi

I was trying to install ubuntu 9.1 and it got stuck for a long time at some stage. finally when I rebooted my laptop and tried to boot from hdd and it is giving following error

Grub loading stage 1.5 
Grub loading please wait 
Error 15 

It was a clean install on my primary hdd. And it got stuck twice. Hence I tried to boot from hdd. I did manual partitioning.

---

### Post by oldfred on 2009-12-19
See this link in the errors section at the end of the initial post.[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[B]
File Not Found (Error 15)[/B]
This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy.

---

### Post by idom on 2009-12-19
Hi thanks I following instructions from 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

( I followed 2 METHOD 2 - Copy GRUB 2 Files from the Installed Partition ) 
now it is going to the grub prompt.

step no 6 Refresh the GRUB 2 menu with sudo update-grub 
gave following message 
grub-probe: error: cannot find a device for /.

I tried to boot from the hdd now and it went to grub prompt
can you further point out what should I do? 

> **oldfred said:**
> See this link in the errors section at the end of the initial post.[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)[B]
File Not Found (Error 15)[/B]
This error is the result of a GRUB 2 installation to /boot but a Master Boot Record ( MBR ) which still contains Grub legacy.

---

### Post by darkod on 2009-12-19
In your case you seem to be missing the config files too, like grub was never installed fully. From that link you posted follow the Method 3 CHROOT procedure.
That can create new config files if none exist.

---

### Post by idom on 2009-12-19
As per your suggestion, I tried running the step 3. A few steps where output was not normal

update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
root@ubuntu:/# sudo grub-install --recheck /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# 

after that I rebooted the system and it is going into memcheck instead of booting from HDD. I think now grub is completely gone.

suggestions please..

> **darkod said:**
> In your case you seem to be missing the config files too, like grub was never installed fully. From that link you posted follow the Method 3 CHROOT procedure.
That can create new config files if none exist.

---

### Post by darkod on 2009-12-19
Did you mount all devices from all previous steps as per the instructions?

To summarize, you need to execute something like:

```
sudo -i
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt/ /dev/sda
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
```

In the second command, replace /dev/sda1 with your root partition. Do you know what your root partition is? Were you mounting it at all?

If you are not sure about root partition, execute in terminal
sudo fdisk -l

and copy the result here and I'll see which one is it. After that execute the above commands.

---

### Post by idom on 2009-12-19
I am pretty sure that it is /dev/sda1

however, I am still pasting the output here

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094ad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4985    40041981   83  Linux
/dev/sda2            4986        9726    38082082+  83  Linux
/dev/sda3            9727       12158    19535040    b  W95 FAT32
/dev/sda4           12159       19457    58629217+   5  Extended
/dev/sda5           12159       19088    55665193+  83  Linux
/dev/sda6           19089       19457     2963961   82  Linux swap / Solaris


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0622b86c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       20398    81923467+   7  HPFS/NTFS
/dev/sdb3           20399       30401    80349097+   7  HPFS/NTFS


Can you please confirm that it is /dev/sda1 

I had made two primary partition for linux and for /dev/sda1 I had given mount point as / 

Thanks for the help.


> **darkod said:**
> Did you mount all devices from all previous steps as per the instructions?

To summarize, you need to execute something like:

```
sudo -i
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt/ /dev/sda
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
```

In the second command, replace /dev/sda1 with your root partition. Do you know what your root partition is? Were you mounting it at all?

If you are not sure about root partition, execute in terminal
sudo fdisk -l

and copy the result here and I'll see which one is it. After that execute the above commands.

---

### Post by idom on 2009-12-19
And I think yes, i followed all the steps. 

Thanks again for all the help. 

> **idom said:**
> I am pretty sure that it is /dev/sda1

however, I am still pasting the output here

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094ad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4985    40041981   83  Linux
/dev/sda2            4986        9726    38082082+  83  Linux
/dev/sda3            9727       12158    19535040    b  W95 FAT32
/dev/sda4           12159       19457    58629217+   5  Extended
/dev/sda5           12159       19088    55665193+  83  Linux
/dev/sda6           19089       19457     2963961   82  Linux swap / Solaris


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0622b86c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       20398    81923467+   7  HPFS/NTFS
/dev/sdb3           20399       30401    80349097+   7  HPFS/NTFS


Can you please confirm that it is /dev/sda1 

I had made two primary partition for linux and for /dev/sda1 I had given mount point as / 

Thanks for the help.

---

### Post by darkod on 2009-12-19
From this output you can't tell for sure because sda1, sda2 and sda5 are all linux type partitions. But if you selected mount point / for /dev/sda1 then that's it.
Execute the commands with /dev/sda1 in the second and see how it goes.

---

### Post by idom on 2009-12-19
I am pasting the complete terminal output

Please advise  . ( /media/Modi_* are external USB disk partitions so those can be ignored , I think )  And one more comment I have to go out for something for half an hour, however, I will be back asap. 

Thanks for your patience.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount --bind /sys /mnt/sys
root@ubuntu:~# chroot /mnt update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
ls: cannot access /media/Modi_1: No such file or directory
ls: cannot access /media/Modi_1: No such file or directory
ls: cannot access /media/Modi_1: No such file or directory
ls: cannot access /media/Modi_1: No such file or directory
ls: cannot access /media/Modi_2: No such file or directory
ls: cannot access /media/Modi_2: No such file or directory
ls: cannot access /media/Modi_2: No such file or directory
ls: cannot access /media/Modi_2: No such file or directory
ls: cannot access /media/Modi_3: No such file or directory
ls: cannot access /media/Modi_3: No such file or directory
ls: cannot access /media/Modi_3: No such file or directory
ls: cannot access /media/Modi_3: No such file or directory
done
root@ubuntu:~# umount /mnt/sys
root@ubuntu:~# umount /mnt/dev
root@ubuntu:~# umount /mnt/pro
umount: /mnt/pro: not found
root@ubuntu:~# umount /mnt/proc
root@ubuntu:~# exit
logout




> **darkod said:**
> From this output you can't tell for sure because sda1, sda2 and sda5 are all linux type partitions. But if you selected mount point / for /dev/sda1 then that's it.
Execute the commands with /dev/sda1 in the second and see how it goes.

---

### Post by darkod on 2009-12-19
OK, time for the heavy artillery. :) Something is messed up with your install. Boot with the LiveCD again. Download the script in my signature, move it on desktop for example, and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with your whole boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by idom on 2009-12-19
Hi I do not know how to do it in Code tags

And I have another problem Live ubuntu CD is a friends and his ubuntu has crashed to he needs the CD 
I will reboot after this with 9.04 live Cd instead of 9.1 cd 

Thanks again

ubuntu@ubuntu:~$ cp /home/ubuntu/Downloads/boot_info_script041.sh  /home/ubuntu/Desktop/
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~$ more /home/ubuntu/Desktop/RESULTS.txt 
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00094ad6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    80,084,024    80,083,962  83 Linux
/dev/sda2          80,084,025   156,248,189    76,164,165  83 Linux
/dev/sda3         156,248,190   195,318,269    39,070,080   b W95 FAT32
/dev/sda4         195,318,270   312,576,704   117,258,435   5 Extended
/dev/sda5         195,318,333   306,648,719   111,330,387  83 Linux
/dev/sda6         306,648,783   312,576,704     5,927,922  82 Linux swap / Solar
is


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1c500e30-2f7c-4cf3-8ba8-7c1043d59bcd" TYPE="ext4" 
/dev/sda2: UUID="5b971240-6b6f-4308-9b76-45573d027c18" TYPE="ext4" 
/dev/sda3: UUID="D0EC-E24E" TYPE="vfat" 
/dev/sda5: UUID="ca234d80-afc9-4490-9f7a-dc0ccf3234f2" TYPE="ext4" 
/dev/sda6: UUID="6fb6becc-cafd-46d0-ab37-2e76d08e6c87" TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev
)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nod
ev,user=ubuntu)


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
search --no-floppy --fs-uuid --set 1c500e30-2f7c-4cf3-8ba8-7c1043d59bcd
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
UUID=1c500e30-2f7c-4cf3-8ba8-7c1043d59bcd /               ext4    errors=remount
-ro 0       1
# /data was on /dev/sda5 during installation
UUID=ca234d80-afc9-4490-9f7a-dc0ccf3234f2 /data           ext4    defaults      
  0       2
# /proj was on /dev/sda2 during installation
UUID=5b971240-6b6f-4308-9b76-45573d027c18 /proj           ext4    defaults      
  0       2
# /win was on /dev/sda3 during installation
UUID=D0EC-E24E  /win            vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=6fb6becc-cafd-46d0-ab37-2e76d08e6c87 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg

> **darkod said:**
> OK, time for the heavy artillery. :) Something is messed up with your install. Boot with the LiveCD again. Download the script in my signature, move it on desktop for example, and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with your whole boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by darkod on 2009-12-19
I'm getting out of ideas. It looks normal. Grub2 is now installed on the MBR but it doesn't seem to "see" your Ubuntu on /dev/sda1. That's why only memtest is reported when doing update-grub and when you boot memtest starts automatically.
I really don't know what could be wrong with this. Sorry. :(

---

### Post by presence1960 on 2009-12-19
> **darkod said:**
> I'm getting out of ideas. It looks normal. Grub2 is now installed on the MBR but it doesn't seem to "see" your Ubuntu on /dev/sda1. That's why only memtest is reported when doing update-grub and when you boot memtest starts automatically.
I really don't know what could be wrong with this. Sorry. :(

Darko, his grub.cfg has no linux entries. I can't help right now as we are having a major snowstorm and have to dig my car out and shovel my home front.

---

### Post by oldfred on 2009-12-19
Something is wrong with the install as the last entry shows no boot files.

This is his:

    .0GB: boot/grub/grub.cfg

There does not seem to be any boot files???

This is mine ( from a week or two ago):
 107.7GB: boot/grub/grub.cfg
 107.3GB: boot/initrd.img-2.6.31-14-generic
 107.6GB: boot/initrd.img-2.6.31-15-generic
 107.4GB: boot/vmlinuz-2.6.31-14-generic
 107.2GB: boot/vmlinuz-2.6.31-15-generic
 107.6GB: initrd.img
 107.3GB: initrd.img.old
 107.2GB: vmlinuz
 107.4GB: vmlinuz.old

Can you check from the liveCD and see if /boot has any vmlinuz or initrd.img files?

---

### Post by darkod on 2009-12-19
My point exactly. I noticed there are no linux entries in the grub/cfg but that's because update-grub doesn't find them. As far as I know the OP doesn't have separate /boot partition.
I don't know ubuntu enough to figure this out. I guess reinstall would be the next step.

---

### Post by idom on 2009-12-19
even I was thinking that there must be something wrong with the initrdfile as my installation in the first place did not go through 
completely. 

     ..
ubuntu@ubuntu:~$ ls -alrt  /media/1c500e30-2f7c-4cf3-8ba8-7c1043d59bcd/boot/
total 2500
-rw-r--r--  1 root root 1664737 2009-10-16 18:03 System.map-2.6.31-14-generic
-rw-r--r--  1 root root  111371 2009-10-16 18:03 config-2.6.31-14-generic
-rw-r--r--  1 root root  629174 2009-10-16 18:03 abi-2.6.31-14-generic
-rw-r--r--  1 root root    1196 2009-10-16 18:06 vmcoreinfo-2.6.31-14-generic
-rw-r--r--  1 root root  128796 2009-10-23 16:11 memtest86+.bin
drwxr-xr-x 24 root root    4096 2009-12-18 19:50 ..
drwxr-xr-x  3 root root    4096 2009-12-18 19:50 .
drwxr-xr-x  2 root root    4096 2009-12-19 15:47 grub


so what choice do I have now ? 


> **oldfred said:**
> Something is wrong with the install as the last entry shows no boot files.

This is his:

    .0GB: boot/grub/grub.cfg

There does not seem to be any boot files???

This is mine ( from a week or two ago):
 107.7GB: boot/grub/grub.cfg
 107.3GB: boot/initrd.img-2.6.31-14-generic
 107.6GB: boot/initrd.img-2.6.31-15-generic
 107.4GB: boot/vmlinuz-2.6.31-14-generic
 107.2GB: boot/vmlinuz-2.6.31-15-generic
 107.6GB: initrd.img
 107.3GB: initrd.img.old
 107.2GB: vmlinuz
 107.4GB: vmlinuz.old

Can you check from the liveCD and see if /boot has any vmlinuz or initrd.img files?

---

### Post by oldfred on 2009-12-19
Boot files are rather important:). I do not know if you can chroot into your system and do a full update and it will install them or if you just have to do a total reinstall?

I would try the chroot which is similar to Darko's except I add  commands for internet connection:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

update: Also run the update-grub while chrooted.

---

### Post by idom on 2009-12-19
apt-get update gives following error

root@ubuntu:/# apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory
root@ubuntu:/# apt-get upgrade 
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I am rather hesitant for the full install because last night I had tried full install twice and both time it got stuck at some point ( laptop was hung so I do not know what is point at which it got stuck, laptop was in the same state for some 4 hours and after that I did poweroff ) 
I did disc checking and it was ok so I do not know if I do full install 3rd time it will be successful.

Also internet command 
root@ubuntu:/# cp /etc/resolv.conf /mnt/etc/resolv.conf 
cp: cannot stat `/etc/resolv.conf': No such file or directory
 also had error, hence I am afraid that installation is completely messed up. 


> **oldfred said:**
> Boot files are rather important:). I do not know if you can chroot into your system and do a full update and it will install them or if you just have to do a total reinstall?

I would try the chroot which is similar to Darko's except I add  commands for internet connection:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by kansasnoob on 2009-12-19
I'd try one of two things (or try the first and if it fails try the second) before reinstalling:

#1: Physically reinstall grub2 (packages and all).

#2: Revert to legacy grub.

To update the package list and remove/install packages we need to add a few steps to the mount & chroot. Look here please for full explanation:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Whether you choose option #1 or #2 first make sure we're properly mounted, etc:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

***Yes those steps are to unmount but I want to know if that returns any errors, if so refer to the aforementioned link about individual commands to properly unmount.***

Then mount and chroot:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now, just to gather more info about partitions:

```
df -H
``` and:

```
parted /dev/sda print
```

Then backup the old grub folder and create a new one:

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

Then purge grub2:

```
apt-get --purge remove grub-pc grub-common os-prober
```

Now if you chose option #1 **only if you want to give grub2 another try:**

```
apt-get update && apt-get install grub-pc
```

```
update-grub
```

```
grub-install /dev/sda
```

If that appeared to succeed or you just want to see if the system will boot:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

If you chose to try option #1 and it failed mount & chroot again and we'll try legacy grub:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Then once again backup the old grub folder and create a new one (I'm assuming that /boot/grub_backup has already been used):

```
mv /boot/grub /boot/grub_backup2
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub-pc grub-common os-prober
```

```
apt-get update && apt-get install grub
```

```
update-grub
```

You'll be asked if you want to create a /boot/grub/menu.lst - yes, you do, so type y and enter!

```
grub-install /dev/sda
```

Now we need a grub shell:

```
grub
```

```
find /boot/grub/stage1
```

Should show (hd0,0) so:

```
root (hd0,0)
```

```
setup (hd0)
```

```
quit
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

And if all went well you should have a bootable OS.

Is that clear as mud? Maybe I should have separated the steps for option #1 and #2 better :confused:

Sometimes I almost confuse myself:(

---

### Post by idom on 2009-12-19
Guys thanks for all the help. 

I tried a fresh install from 9.1 Live Cd and again it got stuck.

I really needed something to work properly by tomorrow. I got bugged and went back to 8.04 LTS and its installation seems to have gone smooth. 

Now what are the potential problems if I upgrade from 8.04 LTS to 9.1 I need 9.1 because it is better mostly I read that it supports voice chat over gtalk

Please point to some link where majority of the issues in these upgrades are mentioned.

Thanks again for so much patience and so much help.

Regards,
Idom

---

### Post by kansasnoob on 2009-12-19
You can't directly upgrade from 8.04 to 9.10 in Ubuntu. I've read that you can in Kubuntu but haven't tried it.

In Ubuntu you'd have to go 8.04 > 8.10 > 9.04 > 9.10. IMHO very time consuming and apt to fail!

Since you can now boot 8.04 please post the output of:

```
df -H
``` and:

```
sudo parted /dev/sda print
```

They're just informational.

---

### Post by kansasnoob on 2009-12-19
BTW I'd love to have seen if that would have booted with legacy grub.

---

### Post by kansasnoob on 2009-12-19
Dumb question: have you thought to check the Cd for defects?

[ATTACH]140560[/ATTACH]

Old pic but similar.

Pic courtesy of my hero Herman:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by idom on 2009-12-20
I tried installing 8.04 ( completely fresh install ), However, this time it said that installation completed successfully. Please reboot. I rebooted 
and again it is stuck at grub stage 1.5 error 15 :(

I will debug more today. 

Is it possible that Now grub2 is installed and it would have problem with 8.04. However, as it was completely fresh install I do not see how it can have grub2 information. 

Please advise.

---

### Post by idom on 2009-12-20
Yes I have checked disc for defects. 
I also did mem test just to see if everything is ok with my RAM
And both tests passed. 

idom

> **kansasnoob said:**
> Dumb question: have you thought to check the Cd for defects?

[ATTACH]140560[/ATTACH]

Old pic but similar.

Pic courtesy of my hero Herman:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by idom on 2009-12-20
Finally this is what I did.

As ubuntu 9.1 was not getting installed properly hence I decided to go ahead and installed 8.04 LTS version. 

I did a fresh install and / (root ) partition was at the end of the 160 GB HDD and hence it was giving grub stage 1.5 error 18. A quick yahoo search revealed that it is mostly because my BIOS does not have the capability to handle 160 GB. 

Hence again I did another fresh install with / (root) partition at the beginning of HDD and it went through cleanly.

Now I need to upgrade to 9.1 via internet. 

Let me see how it goes. After 4 futile fresh installation, the 5th time I have succeeded in installing ubuntu on my comp.Let me see how the update goes.

Thanks all the guys for all the help. I hope that I do not face problem with 8.04 to 9.1 now

idom


> **idom said:**
> Yes I have checked disc for defects. 
I also did mem test just to see if everything is ok with my RAM
And both tests passed. 

idom

---

