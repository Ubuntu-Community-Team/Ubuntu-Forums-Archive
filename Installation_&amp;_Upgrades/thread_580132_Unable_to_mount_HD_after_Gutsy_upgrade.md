---
title: "Unable to mount HD after Gutsy upgrade"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by cajunlibra on 2007-10-18
I am unable to mount 2 additional drives, including my XP partition after upgrading to Gutsy. They mount fine under kernel version 2.6.20-16. It's just when I boot up 2.6.22-14 that the drives aren't recognized.  I posted [elsewhere]("http://ubuntuforums.org/showthread.php?p=3518586#post3518586") but didn't find a fix.

I use Kubuntu primarily. I upgraded using the recommended method for Kubuntu.

Here is some output for the relevant commands with additional information on the other thread:

root@cajun:/home/cajun# sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
mount: /dev/sda1 already mounted or /media/sda1 busy
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()
mount: /dev/sda3 already mounted or /home/cajun/shared busy
mount: special device /dev/sdb1 does not exist
root@cajun:/home/cajun# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot Start End Blocks Id System
/dev/sda1 1 8 64228+ de Dell Utility
/dev/sda2 * 9 5107 40957717+ 7 HPFS/NTFS
/dev/sda3 7430 9729 18474750 c W95 FAT32 (LBA)
/dev/sda4 5108 7429 18651465 83 Linux

Partition table entries are not in disk order
root@cajun:/home/cajun# df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda4 18G 8.9G 7.9G 54% /
varrun 506M 200K 506M 1% /var/run
varlock 506M 4.0K 506M 1% /var/lock
udev 506M 92K 506M 1% /dev
devshm 506M 72K 506M 1% /dev/shm
lrm 506M 35M 472M 7% /lib/modules/2.6.22-14-386/volatile
root@cajun:/home/cajun# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda4 -- converted during upgrade to edgy
UUID=a3ae2bd5-310a-4124-9d7a-626049eebc65 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-0316 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=CC58102058100C38 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=B833-06C0 /home/cajun/shared vfat users,owner,rw,umask=000 0 0
/dev/sdb1 /media/sdb1 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
root@cajun :/home/cajun# ls /media/hda2
ls: /media/hda2: No such file or directory
root@cajun:/home/cajun# ls /media/hda1
ls: /media/hda1: No such file or directory
root@cajun:/home/cajun# ls /media/hda3
ls: /media/hda3: No such file or directory
root@cajun:/home/cajun#


ntfs-3g is already installed and is the most recent version.

---

### Post by mattpker on 2007-10-18
If you read the release notes it says ([http://www.ubuntu.com/getubuntu/releasenotes/710):](http://www.ubuntu.com/getubuntu/releasenotes/710):)

NFS mount support

    *

      To mount NFS filesystems, you must now install the nfs-common package.

Please make sure this is installed and then try again, Let me know if this dose not work.

---

### Post by cajunlibra on 2007-10-18
what about the FAT32 drive though?

in konqueror with root permissions, I can see the fat32 drive but cannot access it.  If I select it, I get an error telling me that I don't have permissions.  I get the same error when I right-click the mountpoint and choose mount.

Inside the Disk & Filesystems - System Settings, I attempt to enable the fat32 drive and get this error: An error occurred while enabling /home/cajun/shared.
The system reported: mount: /dev/sda3 already mounted or /home/cajun/shared busy.   Return code from mount was 32. "mount failure"

For my NTFS drive with XP installed, I get "An error occurred while enabling /home/cajun/windows.
The system reported: fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()" 
Return code from mount was 10.
"system error (out of memory, cannot fork, no more loop devices)"
"user interrupt" "
when I try to manually enable it in the same System settings.

---

### Post by cajunlibra on 2007-10-19
root@cajun:/home/cajun# dd if=/dev/sda count=1 | xxd
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.0116e-05 seconds, 25.5 MB/s
0000000: eb48 90d0 bc00 7cfb 5007 501f fcbe 1b7c  .H....|.P.P....|
0000010: bf1b 0650 57b9 e501 f3a4 cbbd be07 b104  ...PW...........
0000020: 386e 007c 0975 1383 c510 e2f4 cd18 8bf5  8n.|.u..........
0000030: 83c6 1049 7419 382c 74f6 a0b5 07b4 0302  ...It.8,t.......
0000040: ff00 0020 0100 0000 0002 fa90 90f6 c280  ... ............
0000050: 7502 b280 ea59 7c00 0031 c08e d88e d0bc  u....Y|..1......
0000060: 0020 fba0 407c 3cff 7402 88c2 52be 7f7d  . ..@|<.t...R..}
0000070: e834 01f6 c280 7454 b441 bbaa 55cd 135a  .4....tT.A..U..Z
0000080: 5272 4981 fb55 aa75 43a0 417c 84c0 7505  RrI..U.uC.A|..u.
0000090: 83e1 0174 3766 8b4c 10be 057c c644 ff01  ...t7f.L...|.D..
00000a0: 668b 1e44 7cc7 0410 00c7 4402 0100 6689  f..D|.....D...f.
00000b0: 5c08 c744 0600 7066 31c0 8944 0466 8944  \..D..pf1..D.f.D
00000c0: 0cb4 42cd 1372 05bb 0070 eb7d b408 cd13  ..B..r...p.}....
00000d0: 730a f6c2 800f 84ea 00e9 8d00 be05 7cc6  s.............|.
00000e0: 44ff 0066 31c0 88f0 4066 8944 0431 d288  D..f1...@f.D.1..
00000f0: cac1 e202 88e8 88f4 4089 4408 31c0 88d0  ........@.D.1...
0000100: c0e8 0266 8904 66a1 447c 6631 d266 f734  ...f..f.D|f1.f.4
0000110: 8854 0a66 31d2 66f7 7404 8854 0b89 440c  .T.f1.f.t..T..D.
0000120: 3b44 087d 3c8a 540d c0e2 068a 4c0a fec1  ;D.}<.T.....L...
0000130: 08d1 8a6c 0c5a 8a74 0bbb 0070 8ec3 31db  ...l.Z.t...p..1.
0000140: b801 02cd 1372 2a8c c38e 0648 7c60 1eb9  .....r*....H|`..
0000150: 0001 8edb 31f6 31ff fcf3 a51f 61ff 2642  ....1.1.....a.&B
0000160: 7cbe 857d e840 00eb 0ebe 8a7d e838 00eb  |..}.@.....}.8..
0000170: 06be 947d e830 00be 997d e82a 00eb fe47  ...}.0...}.*...G
0000180: 5255 4220 0047 656f 6d00 4861 7264 2044  RUB .Geom.Hard D
0000190: 6973 6b00 5265 6164 0020 4572 726f 7200  isk.Read. Error.
00001a0: bb01 00b4 0ecd 10ac 3c00 75f4 c300 0000  ........<.u.....
00001b0: 0000 0000 0000 0000 1623 ab41 0000 0001  .........#.A....
00001c0: 0100 defe 3f07 3f00 0000 c9f5 0100 8000  ....?.?.........
00001d0: 0108 07fe ffff 08f6 0100 2bee e104 00fe  ..........+.....
00001e0: ffff 0cfe ffff c516 1d07 fccd 3302 00fe  ............3...
00001f0: ffff 83fe ffff 33e4 e304 9232 3902 55aa  ......3....29.U.
root@cajun:/home/cajun#

---

### Post by asd12 on 2007-10-19
Try removing any evms packages and reboot.

---

### Post by chiragjog on 2007-10-19
Hi,
I upgraded from Feisty to Gutsy.
After upgrading i see that my NTFS partition is not mounted(which previously was).

SO i try a manual mount and get this error.
-----------------------------------------------
sudo mount /dev/sda1 /media/
mount: according to mtab, /dev/sda1 is already mounted on /media

FUSE mount point creation failed
Unmounting /dev/sda1 ()
------------------------------------------------

Here is my /etc/mtab

------------------------------------------------
chirag@hells-kitchen:~$ cat /etc/mtab
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/88da9686-a89d-4618-bc78-19be9390fefd / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/88da9686-a89d-4618-bc78-19be9390fefd /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sda7 /media/sda7 vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset= iso8859-1 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
--------------------------------------------------------------------
which doesnt have sda1

Is this related to above issue ?
__________________

---

### Post by m2006h on 2007-10-19
sudo aptitude remove --purge evms

---

### Post by Jeanpaul145 on 2007-10-20
I also have similar problems mounting an ntfs drive, only mine is an external drive using USB2.0. I use Kubuntu x86 Gutsy, freshly installed.
I have made an entry for my drive in /etc/fstab:

/dev/sdb1       /media/KingChoice ntfs user,noauto,rw,async 0 0


however, when I try to mount it, I get:

```
j@znote:~$ sudo mount /dev/sdb1
fuse: failed to access mountpoint /media/KingChoice: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (KingsChoice)
j@znote:~$    
```

I have *no* EVMS packages installed.


D'OH...Made a stupid typo in /etc/fstab: I made a dir in /media called "KingsChoice", and in /etc/fstab I put "KingChoice". No wonder it didn't work :p
Now I can mount it.

---

### Post by cajunlibra on 2007-10-23
> **m2006h said:**
> sudo aptitude remove --purge evms

and also asd12

thank you so much.  that fixed it.

---

### Post by GnuSense on 2007-10-26
I had the same problem mount my vfat, ntfs & my ext3 /home partition after upgrading to Gutsy.  No feed back, I just couldn't log in to the GUI from KDM as a regular user.  Luckily, I've been using Linux for a few years so I knew how to kill X and boot as root and search the net for solutions.  I wouldn't have known what to look for if I didn't know how manually mount and unmount drives from a terminal.  

I did a "aptitude remove --purge evms" & that seemed to fix the problem after a reboot.  (I guess I should have tried a simple 'mount -a').  


 I have to say, I'm been nursing this install since Dapper Drake (5.04) and this was maybe the nastiest upgrade since the first (probably the first wouldn't have seemed so rocky if I was experienced as I am now).   A corrupted tarball caused a lot of things not to install properly, and I had to fool around for an hour or two manually uninstalling and installing & "apt-get -f install"ing to fix the situation (with the help of Google, natch).  dpkg-reconfigure -a bombed out with a cryptic message at some point when I tried to continue:
[INDENT]Unknown DM device 254:0
Failed to create initrd image.[/INDENT]

I should probably go through the same "dpkg-reconfigure -a" procedure again, now that I'm booted in Gutsy, maybe it will go through, but its pretty tedious.

My Samba shares are not auto-mounting from the FSTAB.  I know there are work arounds, I have to find them, but this is an issue I first experienced with Feisty, it  seems like it should have been fixed by now.

Using wine for any simple little app causes my system to freeze (I gather because of my VIA Unichrome driver).  I would have saved a lot of time if I'd just blown the root partition away and started fresh, but I've had this install for 2.5 years, so it is a point of pride to maintain it, just to show that Linux can indeed be upgraded (sort of).  Oh well, it still beats using Vista.

---

