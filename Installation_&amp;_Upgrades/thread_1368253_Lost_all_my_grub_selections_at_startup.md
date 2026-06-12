---
title: "Lost all my grub selections at startup"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Narven on 2009-12-30
Hi,

Yesterday i made some upgrades to ubuntu, but today after a start my grub is only showing: Memory test(memtest86+) and Memory test(memtest86+, serial console 115200).

What happend to my linux start and windowz? :(

How can i repair this?

thanks.

---

### Post by audiomick on 2009-12-30
Which version of Ubuntu is it? The purpose of the question is actually to find out which Grub you have. Is it Grub2 or grub legacy? A fresh install of 9.10 will have grub 2, anything else will have grub legacy.

---

### Post by Narven on 2009-12-30
the grub version is 1.97~Beta4

---

### Post by presence1960 on 2009-12-30
Let's see what is on your machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I am leaving as I am taking my daughter to Disney On Ice. But do that and post the info as requested that way whomever may try to help can see your setup & boot process. I will check back in about 3 or so hours.

---

### Post by Narven on 2009-12-30
thanks for the fast reply :D

and the results are:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b6e5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   419,665,994   419,665,932   7 HPFS/NTFS
/dev/sda2         419,665,995   625,137,344   205,471,350   5 Extended
/dev/sda5         419,666,058   616,687,154   197,021,097  83 Linux
/dev/sda6         616,687,218   625,137,344     8,450,127  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 998 MB, 998768640 bytes
20 heads, 51 sectors/track, 1912 cylinders, total 1950720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 129     1,950,719     1,950,591   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="F8A040E8A040AEC6" TYPE="ntfs" 
sda5: UUID="86abe240-41ef-44e6-b4cb-0e0f75cf97cc" TYPE="ext4" 
sda6: UUID="3f51b114-2822-4bbb-a322-c20b10526e1c" TYPE="swap" 
sdb1: UUID="D0E5-944C" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde 

```

---

### Post by presence1960 on 2009-12-30
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

[COLOR="Red"]sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'[/COLOR]
```

This why. See the red above. That is your ubuntu partition. Something is wrong because it can not be mounted. What exactly were you doing and did any errors occur during the updates? Do you know which updates you applied?

---

### Post by Narven on 2009-12-30
dont know exactly the what where the updates... i know i did sudo apt-get upgrade

it updated some x...lib files

but i didnt see any errors :(

---

### Post by presence1960 on 2009-12-30
> **Narven said:**
> dont know exactly the what where the updates... i know i did sudo apt-get upgrade

it updated some x...lib files

but i didnt see any errors :(

I have no idea what could have made your file system unmountable & unknown. Maybe you should wait a while to see if anyone else knows what happened prior to trying to recover your data.

---

### Post by Narven on 2009-12-30
da.mn buáaaaaaaaaaaaa

thanks anyway :D

isn't there any way to mount it?

---

### Post by presence1960 on 2009-12-30
> **Narven said:**
> da.mn buáaaaaaaaaaaaa

thanks anyway :D

isn't there any way to mount it?

There is a way from the terminal to force mount it and a way to fsck it but I am really busy now with my daughter.

---

### Post by Narven on 2009-12-30
no need to be today :D

tomorrow or when u have a moment :D just tell me what to do.

thanks :D

---

### Post by presence1960 on 2009-12-30
To run a file system check on sda5 boot the Ubuntu Live CD, choose "try Ubuntu without any changes...", when the desktop loads open a terminal and run ```
sudo e2fsck /dev/sda5 -y -f -c -v
```

---

### Post by Narven on 2009-12-30
done... no errors... no problems nothing in the result.

but... the problem continues :( :( :( :(

is better to try to rescue??? :|

---

### Post by presence1960 on 2009-12-30
> **Narven said:**
> done... no errors... no problems nothing in the result.

but... the problem continues :( :( :( :(

is better to try to rescue??? :|

I can't fathom what would do that to your filesystem.

---

### Post by Narven on 2009-12-31
:S best is to format and install?

---

### Post by Narven on 2009-12-31
I was reading the sticky post about ext3 and ext4. Could this be a ext4 bug/problem?

---

### Post by presence1960 on 2009-12-31
> **Narven said:**
> I was reading the sticky post about ext3 and ext4. Could this be a ext4 bug/problem?

possibly but I doubt it. That sticky is from when jaunty first was released. I have been using ext4 since then and have had no problems. Also there arr only a few threads about ext4 being a problem.

I would try reinstalling. But if you have data you want to get from that sda5 you might want to look at BackTrack Linux CD. See [here]("http://www.remote-exploit.org/backtrack_download.html").

Download the iso and burn it as an image to CD. Then boot off the CD. I use it to recover files off of clients unbootable windows machines.

---

### Post by Narven on 2009-12-31
thanks alot for the the help :D

ive reinstall it :D hope it doenst happend again.

happy new year and thanks again :D

---

### Post by presence1960 on 2009-12-31
Happy New Year to you too!

---

