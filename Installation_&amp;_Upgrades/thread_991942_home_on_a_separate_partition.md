---
title: "/home on a separate partition"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Jimmy9pints on 2008-11-24
OK guys, please help me out here. I am really baffled with this.

This is the...er...third attempt (with three different computers) at mounting the home folder on a separate and I still can't get it right!

I have successfully managed this from a new install (through the partition manager) but not after I've installed. I want to do a fresh install of intrepid, but before I start, I have to successfully do this!!!

I have followed instructions from several places before (with the same result). This time I followed the instructions from issue 15 of Full Circle Magazine ([the same instructions can be found here]("http://www.everythingexpress.co.uk/index.php?option=com_content&task=view&id=17&Itemid=6")).

The end result of working through this is that when I reboot and try to login I get this message:
```
Your home directory is listed as:'/home/james' but it does not appear to exist. Do you want to log in with the / (root) directory as you home directory? It is unlikely that anything will work unless you use a failsafe session.
```

Bascically, working through this guide there are a few stumbling blocks which I have tried to work around. I'll mention all of the steps, just in case my "workaround" has actually caused the problem.

Step 1 and 2 went fine, my old partition was still called sda5 and the new one called sda8.

Step 3 went fine too apparently. I was careful to change hda3 and hda1 (in the guide) to sda8 and sda5 respectively. 

Step 4 was strange. It tells me to 
```
cd /oldhome
```
but the result was:
```
bash: cd: /oldhome: No such file or directory
```
Ahh! Why? I don't know. But by cd.. a couple of times and going cd mnt/oldhome/ I got into the mountpoint (so there was indeed such a file or directory). Then the cpio command worked fine too, it spent about 10 minutes copying everything over. I used the gui file browser to check everything was where it should be and it was. There was a copy of the home folder in both partitions full of my files. Great...I thought.

Note: There are two step 4's on [this guide]("http://www.everythingexpress.co.uk/index.php?option=com_content&task=view&id=17&Itemid=6").

Step 4 (the second) and 5 went fine. Now the old partition / has no home folder, only a folder called home_backup_old.

Step 6 didn't throw up any errors. After this step I checked the contents of the newly mounted /home directory with:
```
cd /home
```
and
```
ls
```
which showed me the files I expected to see. I moved around that folder a bit and I could see everything there.

NB. There is no step 7.

Step 8, again no problems. Added the line 
```
/dev/sda8 /home ext3 nodev,nosuid 0 2 
```
I was supposed to. Saved it. Exited. 

Step 9. Rebooted, which led to the error I mentioned at the start. 

I have since been back in on a live session and checked everything is as it should be. I can't see any problems. But this error message is exactly what I got last two times I tried this!

What am I doing wrong????

Please help me if you can.

---

### Post by caljohnsmith on 2008-11-24
OK, from your Live CD, first make sure you don't have any of your partitions mounted, and then please post the output of the following, but replace "sdXY" with your main Ubuntu partition:
```

sudo fdisk -l
sudo blkid
sudo mkdir /mnt/sda8 /mnt/sdXY
sudo mount /dev/sda8 /mnt/sda8
sudo mount /dev/sdXY /mnt/sdXY
ls -l /mnt/sda8/*
cat /mnt/sdXY/etc/fstab
ls -l /mnt/sdXY /mnt/sdXY/home
```
And we can work from there if you want. :)

---

### Post by Jimmy9pints on 2008-11-24
OK, Thanks for your reply. Let's try.

sda5 is my 'main ubuntu partition' i.e. my / partition.  sda8 should be my /home partition.

the output of sudo fdisk -l:
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e851e84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        7296    48363682+   f  W95 Ext'd (LBA)
/dev/sda5            1276        2045     6184993+  83  Linux
/dev/sda6            3826        7017    25639708+   7  HPFS/NTFS
/dev/sda7            7018        7296     2241036   82  Linux swap / Solaris
/dev/sda8            2046        3825    14297818+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1999 MB, 1999241216 bytes
1 heads, 63 sectors/track, 61980 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0xe1b0cb1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       61973     1952112    b  W95 FAT32
```

Output of sudo blkid:
```
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="00F8B2DCF8B2CF62" TYPE="ntfs" 
/dev/sda5: UUID="43c8fe04-2655-4538-b7bb-b68bd198f328" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="78248BF8248BB7A0" TYPE="ntfs" 
/dev/sda7: TYPE="swap" UUID="c8622e3d-5d9b-438f-b9d2-b19aed7e6f08" 
/dev/sda8: UUID="383a6a13-9ca6-43fb-a5b3-09225e47251f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="48BD-75EE" TYPE="vfat" 
/dev/loop0: TYPE="squashfs"
```

Then did:
```
sudo mkdir /mnt/sda8 /mnt/sda5
```and```
sudo mount /dev/sda8 /mnt/sda8
```
No problems.

Then:
```
sudo mount /dev/sdXY /mnt/sd
```
Fine.

Then the out put of ls -l /mnt/sda8/* :
```
-rw-r--r--  1 root root        208 2008-09-03 02:49 modules
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 modutils
lrwxrwxrwx  1 root root         13 2008-11-24 07:33 motd -> /var/run/motd
-rw-r--r--  1 root root        346 2008-07-02 10:47 motd.tail
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 mplayer
-rw-r--r--  1 root root        414 2008-11-24 06:59 mtab
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 mysql
-rw-r--r--  1 root root       7672 2008-04-08 14:02 nanorc
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 ndiswrapper
-rw-r--r--  1 root root       2064 2006-11-23 19:33 netscsid.conf
drwxr-xr-x  6 root root       4096 2008-11-24 07:33 network
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 NetworkManager
-rw-r--r--  1 root root         91 2007-05-15 16:07 networks
-rw-r--r--  1 root root        513 2008-07-02 10:57 nsswitch.conf
drwxr-xr-x  2 root root       4096 2008-04-03 12:12 ODBCDataSources
-rw-r--r--  1 root root          0 2008-04-03 12:12 odbc.ini
-rw-r--r--  1 root root          0 2008-04-03 12:12 odbcinst.ini
-rw-r--r--  1 root root         60 2007-12-03 23:31 openalrc
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 openoffice
drwxr-xr-x  2 root root       4096 2008-07-02 10:47 opt
-rw-r--r--  1 root root        552 2008-04-09 20:22 pam.conf
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 pam.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 pango
-rw-r--r--  1 root ubuntu        7 2008-09-03 02:49 papersize
-rw-r--r--  1 root root       1388 2008-09-02 18:48 passwd
-rw-------  1 root root       1380 2008-09-02 18:48 passwd-
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 pcmcia
drwxr-xr-x  4 root root       4096 2008-11-24 07:33 perl
drwxr-xr-x  5 root root       4096 2008-11-24 07:33 pm
-rw-r--r--  1 root root       7649 2008-07-02 10:55 pnm2ppa.conf
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 PolicyKit
-rw-r--r--  1 root ubuntu      343 2008-11-23 15:12 popularity-contest.conf
drwxr-xr-x  4 root root       4096 2008-11-24 07:33 power
drwxr-xr-x  8 root root       4096 2008-11-24 07:33 ppp
-rw-r--r--  1 root root        497 2008-07-02 10:48 profile
drwxr-xr-x  2 root root       4096 2008-04-15 05:53 profile.d
-rw-r--r--  1 root root       2510 2007-12-03 22:04 protocols
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 pulse
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 purple
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 python
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 python2.5
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 qt3
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc0.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc1.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc2.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc3.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc4.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc5.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rc6.d
-rwxr-xr-x  1 root root        306 2008-09-27 13:50 rc.local
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 rcS.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 readahead
-rw-r--r--  1 root root        373 2007-12-10 05:17 rearj.cfg
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 resolvconf
-rw-r--r--  1 root root        181 2008-11-24 06:51 resolv.conf
-rwxr-xr-x  1 root root        268 2008-04-04 11:07 rmt
-rw-r--r--  1 root root        887 2007-12-03 22:04 rpc
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 samba
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 sane.d
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 scim
-rw-r--r--  1 root root       3663 2007-10-23 16:02 screenrc
-rw-r--r--  1 root root         23 2007-12-06 13:20 scrollkeeper.conf
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 seamonkey
-rw-r--r--  1 root root       1024 2008-04-03 01:08 securetty
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 security
-rw-r--r--  1 root root      18274 2007-12-03 22:04 services
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 sgml
-rw-r-----  1 root shadow      853 2008-09-02 18:48 shadow
-rw-------  1 root root        820 2008-09-02 18:48 shadow-
-rw-r--r--  1 root root        181 2008-07-02 10:55 shells
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 skel
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 sound
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 ssh
drwxr-xr-x  4 root root       4096 2008-11-24 07:33 ssl
-r--r-----  1 root root        470 2008-09-02 18:48 sudoers
-rw-r--r--  1 root root       2405 2008-03-13 22:24 sysctl.conf
-rw-r--r--  1 root root       1614 2007-11-23 09:06 syslog.conf
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 terminfo
drwxr-xr-x  4 root root       4096 2008-11-24 07:33 thunderbird
-rw-r--r--  1 root root         14 2008-10-29 03:05 timezone
-rw-r--r--  1 root root       1260 2008-02-21 07:22 ucf.conf
drwxr-xr-x  3 root root       4096 2008-11-24 07:33 udev
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 ufw
-rw-r--r--  1 root root        142 2008-01-24 16:51 uniconf.conf
-rw-r--r--  1 root root        214 2008-03-08 18:22 updatedb.conf
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 update-manager
drwxr-xr-x  2 root root       4096 2008-04-04 21:34 update-notifier
-rw-r--r--  1 root root        116 2008-09-03 02:49 usplash.conf
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 vga
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 vim
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 w3m
-rw-r--r--  1 root root       4221 2007-06-18 09:45 wgetrc
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 wildmidi
-rw-r--r--  1 root root       1343 2007-01-09 18:39 wodim.conf
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 wpa_supplicant
-rw-r-----  1 root dialout      66 2008-07-02 10:56 wvdial.conf
drwxr-xr-x 10 root root       4096 2008-11-24 07:33 X11
drwxr-xr-x 11 root root       4096 2008-11-24 07:33 xdg
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 xml
drwxr-xr-x  2 root root       4096 2008-11-24 07:33 xulrunner-1.9
-rw-r--r--  1 root root        461 2008-04-03 19:33 zsh_command_not_found

/mnt/sda8/home:
total 4
drwxr-xr-x 41 root root 4096 2008-11-24 07:33 james

/mnt/sda8/initrd:
total 0

/mnt/sda8/lib:
total 6696
lrwxrwxrwx  1 root root      21 2008-11-24 07:31 cpp -> /etc/alternatives/cpp
drwxr-xr-x  2 root root    4096 2008-11-24 07:31 dhcp3-client
drwxr-xr-x  4 root root    4096 2008-11-24 07:29 firmware
drwxr-xr-x  2 root root    4096 2008-04-04 23:28 i486-linux-gnu
drwxr-xr-x  2 root root    4096 2008-11-24 07:30 init
drwxr-xr-x  2 root root    4096 2008-11-24 07:30 iptables
-rwxr-xr-x  1 root root   64612 2008-06-10 05:45 klibc-B9LS-Gjx2D7BYcbQig0RlgHKO9Y.so
-rwxr-xr-x  1 root root  109152 2008-09-12 14:32 ld-2.7.so
lrwxrwxrwx  1 root root       9 2008-11-24 07:31 ld-linux.so.2 -> ld-2.7.so
lrwxrwxrwx  1 root root      15 2008-11-24 07:31 libacl.so.1 -> libacl.so.1.1.0
-rw-r--r--  1 root root   22544 2007-11-14 10:59 libacl.so.1.1.0
-rw-r--r--  1 root root    9804 2008-09-12 14:32 libanl-2.7.so
lrwxrwxrwx  1 root root      13 2008-11-24 07:31 libanl.so.1 -> libanl-2.7.so
lrwxrwxrwx  1 root root      15 2008-11-24 07:31 libatm.so.1 -> libatm.so.1.0.0
-rw-r--r--  1 root root   32224 2007-08-14 20:27 libatm.so.1.0.0
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libattr.so.1 -> libattr.so.1.1.0
-rw-r--r--  1 root root   13592 2007-10-31 22:45 libattr.so.1.1.0
lrwxrwxrwx  1 root root      15 2008-11-24 07:31 libblkid.so.1 -> libblkid.so.1.0
-rw-r--r--  1 root root   36964 2008-03-27 17:25 libblkid.so.1.0
-rw-r--r--  1 root root    5440 2008-09-12 14:32 libBrokenLocale-2.7.so
lrwxrwxrwx  1 root root      22 2008-11-24 07:31 libBrokenLocale.so.1 -> libBrokenLocale-2.7.so
lrwxrwxrwx  1 root root      15 2008-11-24 07:31 libbz2.so.1 -> libbz2.so.1.0.4
lrwxrwxrwx  1 root root      15 2008-11-24 07:29 libbz2.so.1.0 -> libbz2.so.1.0.4
-rw-r--r--  1 root root   66276 2008-03-21 10:32 libbz2.so.1.0.4
-rwxr-xr-x  1 root root 1274092 2008-09-12 14:32 libc-2.7.so
lrwxrwxrwx  1 root root      14 2008-11-24 07:30 libcap.so.1 -> libcap.so.1.10
-rw-r--r--  1 root root   10316 2007-07-31 19:20 libcap.so.1.10
lrwxrwxrwx  1 root root      17 2008-11-24 07:31 libcfont.so.0 -> libcfont.so.0.0.0
-rw-r--r--  1 root root   11512 2008-02-06 22:49 libcfont.so.0.0.0
-rw-r--r--  1 root root  181724 2008-09-12 14:32 libcidn-2.7.so
lrwxrwxrwx  1 root root      14 2008-11-24 07:31 libcidn.so.1 -> libcidn-2.7.so
lrwxrwxrwx  1 root root      17 2008-11-24 07:31 libcom_err.so.2 -> libcom_err.so.2.1
-rw-r--r--  1 root root    7444 2008-03-27 17:25 libcom_err.so.2.1
lrwxrwxrwx  1 root root      19 2008-11-24 07:31 libconsole.so.0 -> libconsole.so.0.0.0
-rw-r--r--  1 root root   73312 2008-02-06 22:49 libconsole.so.0.0.0
-rw-r--r--  1 root root   38300 2008-09-12 14:32 libcrypt-2.7.so
lrwxrwxrwx  1 root root      15 2008-11-24 07:31 libcrypt.so.1 -> libcrypt-2.7.so
lrwxrwxrwx  1 root root      11 2008-11-24 07:31 libc.so.6 -> libc-2.7.so
lrwxrwxrwx  1 root root      19 2008-11-24 07:29 libctutils.so.0 -> libctutils.so.0.0.0
-rw-r--r--  1 root root   17424 2008-02-06 22:49 libctutils.so.0.0.0
-rw-r--r--  1 root root   85108 2007-12-12 19:25 libdevmapper.so.1.02.1
-rw-r--r--  1 root root    9684 2008-09-12 14:32 libdl-2.7.so
lrwxrwxrwx  1 root root      12 2008-11-24 07:31 libdl.so.2 -> libdl-2.7.so
lrwxrwxrwx  1 root root      13 2008-11-24 07:30 libe2p.so.2 -> libe2p.so.2.3
-rw-r--r--  1 root root   20052 2008-03-27 17:25 libe2p.so.2.3
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libext2fs.so.2 -> libext2fs.so.2.4
-rw-r--r--  1 root root  142792 2008-03-27 17:25 libext2fs.so.2.4
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libfuse.so.2 -> libfuse.so.2.7.2
-rw-r--r--  1 root root  102816 2008-02-26 18:25 libfuse.so.2.7.2
-rw-r--r--  1 root root   42700 2008-10-10 19:36 libgcc_s.so.1
lrwxrwxrwx  1 root root      19 2008-11-24 07:31 libgcrypt.so.11 -> libgcrypt.so.11.2.3
-rw-r--r--  1 root root  310956 2007-12-07 11:34 libgcrypt.so.11.2.3
lrwxrwxrwx  1 root root      21 2008-11-24 07:29 libgpg-error.so.0 -> libgpg-error.so.0.3.0
-rw-r--r--  1 root root   11468 2007-11-16 00:56 libgpg-error.so.0.3.0
lrwxrwxrwx  1 root root      17 2008-11-24 07:30 libhistory.so.5 -> libhistory.so.5.2
-rw-r--r--  1 root root   27188 2007-10-02 14:35 libhistory.so.5.2
-rw-r--r--  1 root root   27444 2007-12-21 14:36 libiw.so.29
-rw-r--r--  1 root root    5644 2007-10-24 02:37 libkeyutils-1.2.so
lrwxrwxrwx  1 root root      18 2008-11-24 07:31 libkeyutils.so.1 -> libkeyutils-1.2.so
-rw-r--r--  1 root root  145232 2008-09-12 14:32 libm-2.7.so
-rw-r--r--  1 root root   13696 2008-09-12 14:32 libmemusage.so
lrwxrwxrwx  1 root root      11 2008-11-24 07:31 libm.so.6 -> libm-2.7.so
lrwxrwxrwx  1 root root      17 2008-11-24 07:29 libncurses.so.5 -> libncurses.so.5.6
-rw-r--r--  1 root root  190584 2008-02-23 23:38 libncurses.so.5.6
lrwxrwxrwx  1 root root      18 2008-11-24 07:31 libncursesw.so.5 -> libncursesw.so.5.6
-rw-r--r--  1 root root  236568 2008-02-23 23:38 libncursesw.so.5.6
-rw-r--r--  1 root root   79612 2008-09-12 14:32 libnsl-2.7.so
lrwxrwxrwx  1 root root      13 2008-11-24 07:30 libnsl.so.1 -> libnsl-2.7.so
-rw-r--r--  1 root root   26340 2008-09-12 14:32 libnss_compat-2.7.so
lrwxrwxrwx  1 root root      20 2008-11-24 07:30 libnss_compat.so.2 -> libnss_compat-2.7.so
-rw-r--r--  1 root root   17884 2008-09-12 14:32 libnss_dns-2.7.so
lrwxrwxrwx  1 root root      17 2008-11-24 07:31 libnss_dns.so.2 -> libnss_dns-2.7.so
-rw-r--r--  1 root root   38412 2008-09-12 14:32 libnss_files-2.7.so
lrwxrwxrwx  1 root root      19 2008-11-24 07:30 libnss_files.so.2 -> libnss_files-2.7.so
-rw-r--r--  1 root root   17900 2008-09-12 14:32 libnss_hesiod-2.7.so
lrwxrwxrwx  1 root root      20 2008-11-24 07:30 libnss_hesiod.so.2 -> libnss_hesiod-2.7.so
-rw-r--r--  1 root root    7552 2008-04-18 21:28 libnss_mdns4_minimal.so.2
-rw-r--r--  1 root root    8148 2008-04-18 21:28 libnss_mdns4.so.2
-rw-r--r--  1 root root    7616 2008-04-18 21:28 libnss_mdns6_minimal.so.2
-rw-r--r--  1 root root    8196 2008-04-18 21:28 libnss_mdns6.so.2
-rw-r--r--  1 root root    8172 2008-04-18 21:28 libnss_mdns_minimal.so.2
-rw-r--r--  1 root root    8580 2008-04-18 21:28 libnss_mdns.so.2
-rw-r--r--  1 root root   34352 2008-09-12 14:32 libnss_nis-2.7.so
-rw-r--r--  1 root root   42508 2008-09-12 14:32 libnss_nisplus-2.7.so
lrwxrwxrwx  1 root root      21 2008-11-24 07:31 libnss_nisplus.so.2 -> libnss_nisplus-2.7.so
lrwxrwxrwx  1 root root      17 2008-11-24 07:30 libnss_nis.so.2 -> libnss_nis-2.7.so
lrwxrwxrwx  1 root root      20 2008-11-24 07:30 libntfs-3g.so.23 -> libntfs-3g.so.23.0.0
-rw-r--r--  1 root root  182804 2008-05-30 16:49 libntfs-3g.so.23.0.0
lrwxrwxrwx  1 root root      17 2008-11-24 07:29 libpamc.so.0 -> libpamc.so.0.81.0
-rw-r--r--  1 root root    9028 2008-05-16 15:21 libpamc.so.0.81.0
lrwxrwxrwx  1 root root      21 2008-11-24 07:31 libpam_misc.so.0 -> libpam_misc.so.0.81.2
-rw-r--r--  1 root root    8520 2008-05-16 15:21 libpam_misc.so.0.81.2
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libpam.so.0 -> libpam.so.0.81.6
-rw-r--r--  1 root root   37956 2008-05-16 15:21 libpam.so.0.81.6
lrwxrwxrwx  1 root root      22 2008-11-24 07:31 libparted-1.7.so.1 -> libparted-1.7.so.1.0.0
-rw-r--r--  1 root root  388752 2008-05-30 14:20 libparted-1.7.so.1.0.0
-rw-r--r--  1 root root    5444 2008-09-12 14:32 libpcprofile.so
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libpopt.so.0 -> libpopt.so.0.0.0
-rw-r--r--  1 root root   27144 2007-03-07 21:46 libpopt.so.0.0.0
-rw-r--r--  1 root root   49096 2008-07-10 09:28 libproc-3.2.7.so
-rwxr-xr-x  1 root root  112174 2008-09-12 14:32 libpthread-2.7.so
lrwxrwxrwx  1 root root      17 2008-11-24 07:31 libpthread.so.0 -> libpthread-2.7.so
lrwxrwxrwx  1 root root      18 2008-11-24 07:29 libreadline.so.5 -> libreadline.so.5.2
-rw-r--r--  1 root root  196560 2007-10-02 14:35 libreadline.so.5.2
-rw-r--r--  1 root root   59216 2008-09-12 14:32 libresolv-2.7.so
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libresolv.so.2 -> libresolv-2.7.so
-rw-r--r--  1 root root   30624 2008-09-12 14:32 librt-2.7.so
lrwxrwxrwx  1 root root      12 2008-11-24 07:31 librt.so.1 -> librt-2.7.so
-rw-r--r--  1 root root   13696 2008-09-12 14:32 libSegFault.so
-rw-r--r--  1 root root   95948 2008-02-29 22:29 libselinux.so.1
-rw-r--r--  1 root root  207284 2008-03-01 05:21 libsepol.so.1
lrwxrwxrwx  1 root root      17 2008-11-24 07:31 libslang.so.2 -> libslang.so.2.1.3
-rw-r--r--  1 root root  686384 2007-11-28 13:54 libslang.so.2.1.3
lrwxrwxrwx  1 root root      12 2008-11-24 07:31 libss.so.2 -> libss.so.2.0
-rw-r--r--  1 root root   18648 2008-03-27 17:25 libss.so.2.0
lrwxrwxrwx  1 root root      17 2008-11-24 07:31 libsysfs.so.2 -> libsysfs.so.2.0.1
-rw-r--r--  1 root root   37784 2008-04-01 17:03 libsysfs.so.2.0.1
-rw-r--r--  1 root root   26284 2008-09-12 14:32 libthread_db-1.0.so
lrwxrwxrwx  1 root root      19 2008-11-24 07:30 libthread_db.so.1 -> libthread_db-1.0.so
lrwxrwxrwx  1 root root      13 2008-11-24 07:31 libtic.so.5 -> libtic.so.5.6
-rw-r--r--  1 root root   69952 2008-02-23 23:38 libtic.so.5.6
lrwxrwxrwx  1 root root      14 2008-11-24 07:31 libticw.so.5 -> libticw.so.5.6
-rw-r--r--  1 root root   69952 2008-02-23 23:38 libticw.so.5.6
lrwxrwxrwx  1 root root      20 2008-11-24 07:31 libulockmgr.so.1 -> libulockmgr.so.1.0.1
-rw-r--r--  1 root root    7836 2008-02-26 18:25 libulockmgr.so.1.0.1
lrwxrwxrwx  1 root root      19 2008-11-24 07:31 libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
-rw-r--r--  1 root root   29056 2007-11-23 09:47 libusb-0.1.so.4.4.4
-rw-r--r--  1 root root  443908 2008-03-31 10:42 libusplash.so.0
-rw-r--r--  1 root root    9696 2008-09-12 14:32 libutil-2.7.so
lrwxrwxrwx  1 root root      14 2008-11-24 07:31 libutil.so.1 -> libutil-2.7.so
lrwxrwxrwx  1 root root      14 2008-11-24 07:31 libuuid.so.1 -> libuuid.so.1.2
-rw-r--r--  1 root root   13188 2008-03-27 17:25 libuuid.so.1.2
lrwxrwxrwx  1 root root      22 2008-11-24 07:31 libvolume_id.so.0 -> libvolume_id.so.0.81.0
-rw-r--r--  1 root root   27864 2008-04-11 12:21 libvolume_id.so.0.81.0
lrwxrwxrwx  1 root root      16 2008-11-24 07:31 libwrap.so.0 -> libwrap.so.0.7.6
-rw-r--r--  1 root root   31304 2007-07-30 08:19 libwrap.so.0.7.6
-rw-r--r--  1 root root    7412 2008-04-03 01:04 libx86.so.1
drwxr-xr-x  4 root root    4096 2008-11-24 07:30 linux-restricted-modules
drwxr-xr-x  2 root root    4096 2008-11-24 07:29 linux-sound-base
drwxr-xr-x  2 root root    4096 2008-11-24 07:30 lsb
drwxr-xr-x  4 root root    4096 2008-11-24 07:30 modules
drwxr-xr-x  2 root root    4096 2008-11-24 07:30 security
drwxr-xr-x 15 root root    4096 2008-11-24 07:30 terminfo
drwxr-xr-x  3 root root    4096 2008-11-24 07:31 tls
drwxr-xr-x  3 root root    4096 2008-11-24 07:30 udev
ls: cannot open directory /mnt/sda8/lost+found: Permission denied

/mnt/sda8/media:
total 12
lrwxrwxrwx 1 root ubuntu    6 2008-11-24 07:31 cdrom -> cdrom0
drwxr-xr-x 2 root ubuntu 4096 2008-09-02 18:45 cdrom0
drwxr--r-- 2 root root   4096 2008-09-03 01:45 otherstuff
drwxr--r-- 2 root root   4096 2008-09-02 12:05 windows

/mnt/sda8/mnt:
total 0

/mnt/sda8/opt:
total 0

/mnt/sda8/proc:
total 0

/mnt/sda8/root:
total 0

/mnt/sda8/sbin:
total 6732
-rwxr-xr-x 1 root root     3056 2007-03-07 21:44 acpi_available
-rwxr-xr-x 1 root root     5553 2008-03-09 02:24 alsa
-rwxr-xr-x 1 root root    43204 2008-02-27 13:22 alsactl
-rwxr-xr-x 1 root root     3356 2007-03-07 21:44 apm_available
-rwxr-xr-x 1 root root   746440 2008-05-02 20:42 apparmor_parser
-rwxr-xr-x 1 root root    18164 2008-03-27 17:25 badblocks
-rwxr-xr-x 1 root root     8276 2008-03-27 17:25 blkid
-rwxr-xr-x 1 root root     9476 2008-04-29 11:57 blockdev
-rwxr-xr-x 1 root root    53864 2008-04-29 11:57 cfdisk
-rwxr-xr-x 1 root root     3600 2008-04-29 11:57 ctrlaltdel
-rwxr-xr-x 1 root root    67712 2008-03-27 17:25 debugfs
-rwxr-xr-x 1 root root   199164 2007-07-26 10:57 debugreiserfs
-rwxr-xr-x 1 root root    45216 2008-02-25 21:20 depmod
lrwxrwxrwx 1 root root        9 2008-11-24 07:32 dhclient -> dhclient3
-rwxr-xr-x 1 root root   352392 2008-04-02 13:38 dhclient3
-rwxr-xr-x 1 root root     8170 2008-04-02 13:38 dhclient-script
-rwxr-xr-x 1 root root    43508 2008-03-12 12:24 dosfsck
-rwxr-xr-x 1 root root    12140 2008-03-27 17:25 dumpe2fs
-rwxr-xr-x 1 root root   156076 2008-03-27 17:25 e2fsck
-rwxr-xr-x 1 root root    12332 2008-03-27 17:25 e2image
-rwxr-xr-x 1 root root    23840 2008-03-27 17:25 e2label
-rwxr-xr-x 1 root root    85064 2008-04-29 11:57 fdisk
-rwxr-xr-x 1 root root    23840 2008-03-27 17:25 findfs
-rwxr-xr-x 1 root root    20020 2008-03-27 17:25 fsck
-rwxr-xr-x 1 root root     7028 2008-04-29 11:57 fsck.cramfs
-rwxr-xr-x 1 root root   156076 2008-03-27 17:25 fsck.ext2
-rwxr-xr-x 1 root root   156076 2008-03-27 17:25 fsck.ext3
-rwxr-xr-x 1 root root    22288 2008-04-29 11:57 fsck.minix
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 fsck.msdos -> dosfsck
-rwxr-xr-x 1 root root      333 2008-04-19 05:05 fsck.nfs
-rwxr-xr-x 1 root root      112 2007-07-26 10:57 fsck.reiserfs
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 fsck.vfat -> dosfsck
-rwxr-xr-x 1 root root    15168 2008-04-29 11:57 getty
-rwxr-xr-x 1 root root      375 2008-04-10 13:03 grub-install
lrwxrwxrwx 1 root root        6 2008-11-24 07:32 halt -> reboot
-rwxr-xr-x 1 root root    69228 2008-03-28 22:26 hdparm
-rwxr-xr-x 1 root root    31652 2008-04-29 11:57 hwclock
-rwxr-xr-x 1 root root    61808 2007-12-13 10:51 ifconfig
-rwxr-xr-x 1 root root    27372 2007-09-20 00:25 ifdown
-rwxr-xr-x 1 root root    27372 2007-09-20 00:25 ifup
-rwxr-xr-x 1 root root    89604 2008-04-11 13:50 init
-rwxr-xr-x 1 root root    56484 2008-04-11 13:50 initctl
-rwxr-xr-x 1 root root     5740 2008-02-25 21:20 insmod
-rwxr-xr-x 1 root root     1542 2008-03-31 21:11 installkernel
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 ip -> /bin/ip
-rwxr-xr-x 1 root root    47448 2008-01-28 13:49 ip6tables
-rwxr-xr-x 1 root root    51680 2008-01-28 13:49 ip6tables-restore
-rwxr-xr-x 1 root root    51644 2008-01-28 13:49 ip6tables-save
-rwxr-xr-x 1 root root    10948 2007-12-13 10:51 ipmaddr
-rwxr-xr-x 1 root root    47480 2008-01-28 13:49 iptables
-rwxr-xr-x 1 root root    51712 2008-01-28 13:49 iptables-restore
-rwxr-xr-x 1 root root    49308 2008-01-28 13:49 iptables-save
-rwxr-xr-x 1 root root    14048 2008-01-28 13:49 iptables-xml
-rwxr-xr-x 1 root root    14944 2007-12-13 10:51 iptunnel
-rwxr-xr-x 1 root root     6012 2008-04-29 11:57 isosize
-rwxr-xr-x 1 root root    20596 2007-12-21 14:36 iwconfig
-rwxr-xr-x 1 root root    11784 2007-12-21 14:36 iwevent
-rwxr-xr-x 1 root root     7764 2007-12-21 14:36 iwgetid
-rwxr-xr-x 1 root root    26376 2007-12-21 14:36 iwlist
-rwxr-xr-x 1 root root     9164 2007-12-21 14:36 iwpriv
-rwxr-xr-x 1 root root     8420 2007-12-21 14:36 iwspy
-rwxr-xr-x 1 root root     6300 2008-02-06 22:49 kbdrate
-rwxr-xr-x 1 root root    10668 2008-04-19 05:05 killall5
-rwxr-xr-x 1 root root    23048 2007-11-23 09:06 klogd
-rwxr-xr-x 1 root root      465 2008-09-12 14:32 ldconfig
-rwxr-xr-x 1 root root   621960 2008-09-12 14:32 ldconfig.real
-rwxr-xr-x 1 root root      636 2007-12-07 21:23 loadndisdriver
-rwxr-xr-x 1 root root    15832 2007-12-07 21:23 loadndisdriver-1.9
-rwxr-xr-x 1 root root    34844 2008-04-11 13:50 logd
-rwxr-xr-x 1 root root     6176 2008-03-27 17:25 logsave
-rwxr-xr-x 1 root root    26296 2008-04-29 11:57 losetup
-rwxr-xr-x 1 root root     2356 2008-10-10 17:16 lrm-manager
-rwxr-xr-x 1 root root      877 2008-10-10 17:16 lrm-video
lrwxrwxrwx 1 root root       10 2008-11-24 07:32 lsmod -> /bin/lsmod
lrwxrwxrwx 1 root root        9 2008-11-24 07:32 lspcmcia -> pccardctl
-rwxr-xr-x 1 root root    52392 2007-11-29 23:05 MAKEDEV
-rwxr-xr-x 1 root root    11980 2007-12-13 10:51 mii-tool
-rwxr-xr-x 1 root root    23528 2008-03-12 12:24 mkdosfs
-rwxr-xr-x 1 root root    44124 2008-03-27 17:25 mke2fs
-rwxr-xr-x 1 root root     4904 2008-04-29 11:57 mkfs
-rwxr-xr-x 1 root root     8388 2008-04-29 11:57 mkfs.bfs
-rwxr-xr-x 1 root root    15172 2008-04-29 11:57 mkfs.cramfs
-rwxr-xr-x 1 root root    44124 2008-03-27 17:25 mkfs.ext2
-rwxr-xr-x 1 root root    44124 2008-03-27 17:25 mkfs.ext3
-rwxr-xr-x 1 root root    14624 2008-04-29 11:57 mkfs.minix
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 mkfs.msdos -> mkdosfs
-rwxr-xr-x 1 root root   146460 2007-07-26 10:57 mkfs.reiserfs
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 mkfs.vfat -> mkdosfs
-rwxr-xr-x 1 root root   146460 2007-07-26 10:57 mkreiserfs
-rwxr-xr-x 1 root root    14116 2008-04-29 11:57 mkswap
-rwxr-xr-x 1 root root    10872 2008-02-25 21:20 modinfo
-rwxr-xr-x 1 root root    26860 2008-02-25 21:20 modprobe
-rwxr-xr-x 1 root root     5732 2008-02-26 18:25 mount.fuse
lrwxrwxrwx 1 root root       12 2008-11-24 07:32 mount.ntfs -> /bin/ntfs-3g
lrwxrwxrwx 1 root root       12 2008-11-24 07:32 mount.ntfs-3g -> /bin/ntfs-3g
-rwxr-xr-x 1 root root     7800 2007-12-13 10:51 nameif
-rwxr-xr-x 1 root root     1697 2006-08-21 13:08 on_ac_power
-rwxr-xr-x 1 root root     7936 2008-05-16 15:21 pam_tally
-rwxr-xr-x 1 root root    59712 2008-05-30 14:20 parted
-rwxr-xr-x 1 root root     4668 2008-05-30 14:20 partprobe
-rwxr-xr-x 1 root root    11316 2007-10-23 17:03 pccardctl
-rwxr-xr-x 1 root root     2988 2008-04-29 11:57 pivot_root
-rwxr-xr-x 1 root root     4828 2007-12-13 10:51 plipconfig
lrwxrwxrwx 1 root root        6 2008-11-24 07:32 poweroff -> reboot
-rwxr-xr-x 1 root root    23896 2007-12-13 10:51 rarp
-rwxr-xr-x 1 root root     5704 2008-04-29 11:57 raw
-rwxr-xr-x 1 root root     8320 2008-04-21 22:54 readahead-list
-rwxr-xr-x 1 root root     9280 2008-04-21 22:54 readahead-watch
-rwxr-xr-x 1 root root    35372 2008-04-11 13:50 reboot
-rwxr-xr-x 1 root root   295512 2007-07-26 10:57 reiserfsck
-rwxr-xr-x 1 root root   146012 2007-07-26 10:57 reiserfstune
-rwxr-xr-x 1 root root    29232 2008-03-27 17:25 resize2fs
-rwxr-xr-x 1 root root   143996 2007-07-26 10:57 resize_reiserfs
-rwxr-xr-x 1 root root     7800 2008-02-25 21:20 rmmod
-rwxr-xr-x 1 root root    50196 2007-12-13 10:51 route
-rwxr-xr-x 1 root root    23356 2008-07-09 15:48 rtacct
-rwxr-xr-x 1 root root    22276 2008-07-09 15:48 rtmon
-rwxr-xr-x 1 root root    33052 2008-04-11 13:50 runlevel
-rwxr-xr-x 1 root root    52360 2008-04-29 11:57 sfdisk
-rwxr-xr-x 1 root root      875 2008-04-03 01:08 shadowconfig
-rwxr-xr-x 1 root root    44312 2008-04-11 13:50 shutdown
-rwxr-xr-x 1 root root    27932 2007-12-13 10:51 slattach
-rwxr-xr-x 1 root root    59288 2008-07-09 15:48 ss
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 start -> initctl
-rwxr-xr-x 1 root root    18948 2008-05-30 16:52 start-stop-daemon
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 status -> initctl
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 stop -> initctl
-rwxr-xr-x 1 root root    10068 2008-04-19 05:05 sulogin
lrwxrwxrwx 1 root root        6 2008-11-24 07:32 swapoff -> swapon
-rwxr-xr-x 1 root root    36124 2008-04-29 11:57 swapon
-rwxr-xr-x 1 root root     9220 2008-07-10 09:28 sysctl
-rwxr-xr-x 1 root root    32080 2007-11-23 09:06 syslogd
-rwxr-xr-x 1 root root   214920 2008-07-09 15:48 tc
-rwxr-xr-x 1 root root    38964 2008-04-11 13:50 telinit
-rwxr-xr-x 1 root root    23840 2008-03-27 17:25 tune2fs
-rwxr-xr-x 1 root root    75780 2008-04-11 12:21 udevadm
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 udevcontrol -> udevadm
-rwxr-xr-x 1 root root    67612 2008-04-11 12:21 udevd
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 udevsettle -> udevadm
lrwxrwxrwx 1 root root        7 2008-11-24 07:32 udevtrigger -> udevadm
lrwxrwxrwx 1 root root       20 2008-11-24 07:32 umount.hal -> /usr/sbin/umount.hal
-rwxr-sr-x 1 root shadow  19584 2008-05-16 15:21 unix_chkpwd
-rwxr-xr-x 1 root root      466 2008-04-10 13:03 update-grub
-rwxr-xr-x 1 root root      300 2008-02-25 21:20 update-modules
-rwxr-xr-x 1 root root     8492 2008-03-31 10:42 usplash
-rwxr-xr-x 1 root root     1046 2008-03-31 10:42 usplash_down
-rwxr-xr-x 1 root root     3700 2008-03-31 10:42 usplash_write
lrwxrwxrwx 1 root root       16 2008-11-24 07:32 vol_id -> /lib/udev/vol_id
-rwxr-xr-x 1 root root     1857 2008-03-12 21:28 wpa_action
-rwxr-xr-x 1 root root    30912 2008-03-12 21:28 wpa_cli
-rwxr-xr-x 1 root root   319812 2008-03-12 21:28 wpa_supplicant

/mnt/sda8/srv:
total 0

/mnt/sda8/sys:
total 0

/mnt/sda8/tmp:
total 8
drwx------ 2 1000 1000 4096 2008-11-24 06:59 gconfd-james
drwx------ 2 1000 1000 4096 2008-11-24 06:59 orbit-james
-rw------- 1 root root    0 2008-11-24 06:30 tmp.hyERow5177
-rw------- 1 root root    0 2008-11-24 06:59 tmp.xYluog6565

/mnt/sda8/usr:
total 148
drwxr-xr-x   2 root root 36864 2008-11-24 07:43 bin
drwxr-xr-x   2 root root  4096 2008-11-24 07:43 games
drwxr-xr-x  10 root root  4096 2008-11-24 07:34 include
drwxr-xr-x 165 root root 65536 2008-11-24 07:34 lib
drwxr-xr-x  10 root root  4096 2008-11-24 07:43 local
drwxr-xr-x   2 root root 12288 2008-11-24 07:42 sbin
drwxr-xr-x 259 root root 12288 2008-11-24 07:37 share
drwxr-xr-x   5 root root  4096 2008-11-24 07:42 src
drwxr-xr-x   2 root root  4096 2008-11-24 07:42 X11R6

/mnt/sda8/var:
total 52
drwxr-xr-x  2 root root  4096 2008-11-24 07:32 backups
drwxr-xr-x 17 root root  4096 2008-11-24 07:32 cache
drwxr-xr-x  2 root root  4096 2008-04-04 21:34 crash
drwxr-xr-x  2 root root  4096 2008-11-24 07:32 games
drwxr-xr-x 49 root root  4096 2008-11-24 07:31 lib
drwxrwsr-x  2 root staff 4096 2008-04-15 05:53 local
drwxrwxrwt  2 root root  4096 2008-04-15 05:53 lock
drwxr-xr-x 12 root root  4096 2008-11-24 07:32 log
drwxrwsr-x  2 root mail  4096 2008-07-02 10:47 mail
drwxr-xr-x  2 root root  4096 2008-07-02 10:47 opt
drwxr-xr-x 12 root root  4096 2008-11-24 07:32 run
drwxr-xr-x  7 root root  4096 2008-11-24 07:32 spool
drwxr-xr-x  3 root root  4096 2008-11-24 07:32 tmp

```
But I don't think that's all of the output code, because when I scrolled to the top, there I couldn't see the original prompt and command. 

And the output from cat /mnt/sda5/etc/fstab :

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=43c8fe04-2655-4538-b7bb-b68bd198f328 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=c8622e3d-5d9b-438f-b9d2-b19aed7e6f08 none swap sw 0 0
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/otherstuff ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda8 /home ext3 nodev,nosuid 0 2 

```

And finally the result of ls -l /mnt/sda5 /mnt/sda5/home
```
ls: cannot access /mnt/sda5/home: No such file or directory
/mnt/sda5:
total 104
drwxr-xr-x   2 root root    4096 2008-10-29 03:05 bin
drwxr-xr-x   3 root root    4096 2008-11-23 15:26 boot
lrwxrwxrwx   1 root ubuntu    11 2008-09-02 18:45 cdrom -> media/cdrom
drwxr-xr-x   4 root root    4096 2008-07-02 10:55 dev
drwxr-xr-x 131 root root   12288 2008-11-24 14:35 etc
drwxr-xr-x   3 root root    4096 2008-09-02 18:48 home_backup_old
drwxr-xr-x   2 root root    4096 2008-07-02 10:47 initrd
lrwxrwxrwx   1 root root      33 2008-10-21 07:03 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root ubuntu    33 2008-09-03 02:50 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  15 root root   12288 2008-10-29 03:05 lib
drwx------   2 root root   16384 2008-09-02 18:45 lost+found
drwxr-xr-x   5 root root    4096 2008-11-24 14:34 media
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 mnt
drwxr-xr-x   2 root root    4096 2008-07-02 10:47 opt
drwxr-xr-x   2 root root    4096 2008-04-15 05:53 proc
drwxr-xr-x  12 root root    4096 2008-11-23 15:15 root
drwxr-xr-x   2 root root    4096 2008-10-21 07:03 sbin
drwxr-xr-x   2 root root    4096 2008-07-02 10:47 srv
drwxr-xr-x   2 root root    4096 2008-04-19 05:05 sys
drwxrwxrwt   4 root root    4096 2008-11-24 14:35 tmp
drwxr-xr-x  11 root root    4096 2008-09-05 12:50 usr
drwxr-xr-x  15 root root    4096 2008-07-02 10:57 var
lrwxrwxrwx   1 root root      30 2008-10-21 07:03 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root ubuntu    30 2008-09-03 02:50 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic

```

OK. That's everything. Thanks for your help with this, I would really like to get to the bottom of this! I am now helping to maintain 5 Ubuntu/Xubuntu/Luxbuntu/Mint machines for friends and family (I am spreading the good word). This will help me help them too.

BTW - it's the middle of the night here, so you won't here again from me until tomorrow. 

Cheers,

James.

---

### Post by psusi on 2008-11-24
It looks like you copied the entire root filesystem to the new partition instead of just /home, so once you have the new partition mounted in /home, your home directory is in /home/home/james instead of /home/james.

---

### Post by caljohnsmith on 2008-11-24
I agree with psusi, it looks like you copied over your entire sda5 root file system to sda8, or at least most of it. :) But the other problem I see is that you don't have a /home folder in your sda5 partition since you moved the original /home to /home_backup_old; the /home folder must first exist for fstab to mount sda8 on /home. 

If I were in your shoes, I think I would make sure that /home_backup_old has your home directory and all your files, and only once you are positive of that, I would delete everything in sda8 and start fresh by doing the following from your Live CD (if any command returns some sort of error, please do not proceed with the rest of them):
```
sudo mkdir /mnt/sda5 /mnt/sda8
sudo mount /dev/sda5 /mnt/sda5
sudo mount /dev/sda8 /mnt/sda8
sudo rm -fr /mnt/sda8/*
sudo cp -ax /mnt/sda5/home_backup_old/* /mnt/sda8
sudo mkdir /mnt/sda5/home
```
I think "cp -ax" is a much simpler way of copying your files over while maintaining the permissions/ownership of the original files; you don't have to use the find command with cpio like the tutorial shows, although they should do the same thing I think. How about posting the output of all the above commands (just copy/paste your entire terminal session) just so I can verify that everything went OK; if you didn't get any errors though, reboot, and see if you can boot into Ubuntu OK. :)

---

### Post by Jimmy9pints on 2008-11-24
It's not going well already...
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda5 /mnt/sda8
mkdir: cannot create directory `/mnt/sda5': File exists
mkdir: cannot create directory `/mnt/sda8': File exists

```
I thought that's not an error message, those mnt files already exist because I ran that command before. But when I try to mount it I get this:```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 mnt/sda5
mount: mount point mnt/sda5 does not exist
```

I thought I was getting a grip on this...now I am feeling fairly clueless. Thanks for your ongoing help guys.

I think I better not go any further because of this error.

Cheers,

James.

---

### Post by caljohnsmith on 2008-11-24
> **Jimmy9pints said:**
> It's not going well already...
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda5 /mnt/sda8
mkdir: cannot create directory `/mnt/sda5': File exists
mkdir: cannot create directory `/mnt/sda8': File exists

```
I thought that's not an error message, those mnt files already exist because I ran that command before. But when I try to mount it I get this:```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 mnt/sda5
mount: mount point mnt/sda5 does not exist
```

I thought I was getting a grip on this...now I am feeling fairly clueless. Thanks for your ongoing help guys.

I think I better not go any further because of this error.

Cheers,

James.
It's always better to be safe rather than sorry, so I'm glad you stopped where you did; those first two warnings are OK, but you have a small typo in the mount command you ran:
```
sudo mount /dev/sda5 mnt/sda5
```
Note there needs to be a "/" in front of mnt so that it specifies the root directory. If you can, it would help if you can copy/paste the exact commands over so you don't have to worry about typos. Let me know how it goes. :)

---

### Post by Jimmy9pints on 2008-11-25
will do...here goes

---

### Post by Jimmy9pints on 2008-11-25
This is my whole terminal session:
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda5 /mnt/sda8
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt/sda8
ubuntu@ubuntu:~$ sudo rm -fr /mnt/sda8/*
ubuntu@ubuntu:~$ sudo cp -ax /mnt/sda5/home_backup_old/* /mnt/sda8
ubuntu@ubuntu:~$ sudo mkdir /home
mkdir: cannot create directory `/home': File exists
```

It was all going very smoothly until the last error. But I guess since we were trying to create something that already exists, that's not a big problem. 

I am going to try to reboot now to see what happens.

James.

---

### Post by Jimmy9pints on 2008-11-25
OK, upon reboot I get exactly the same error!

Any more ideas?

Cheers, James.

---

### Post by orodoni_le on 2008-11-25
I also try to move my /home to my WinXP documents partition, so I could share files from both OS (dualboot). I used this procedure to copy the files from the old /home to the NTFS partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Of course, I modify the mount commands with ntfs-3g option for the new /home partition. I also modified the /etc/fstab file with ntfs, leaving the other options unchanged. I received an error at login regarding $HOME/.dmrc, but I can get into my session and see the files inside /home. I even can save files inside the /home/USERNAME folder. I try to change the ownership of the new /home/USERNAME folders, but I can't. I with sudo nautilus, and changing the permissions with the interface, and with chown in recovery mode.

When I do
ls -l
I get that all files and foders inside /home/USERNAME are owned by root. The filenames are showed in blue letters, with a green background. I search in the forums, and get this page:

[http://ubuntuforums.org/showthread.php?t=736821](http://ubuntuforums.org/showthread.php?t=736821)

So, my files are OWR. I don't know what that means, or how to change it so the owner is USERNAME.

Sorry, I'm a newbie inside this forums. And I can't give you the exit of the ls command, because the problematic computer doesn't have Internet connection. Thanks in advance for your help

---

### Post by meindian523 on 2008-11-25
orodoni:
What does ```
sudo chown username:username *
``` in your /home/username directory give?

---

### Post by caljohnsmith on 2008-11-25
> **Jimmy9pints said:**
> OK, upon reboot I get exactly the same error!

Any more ideas?

Cheers, James.
I'm sorry, that was my mistake with that very last command to make a new /home directory (I just now corrected my previous post); you don't have to redo any of the previous commands though, just go ahead and do the following from your Live CD, and I think you should be all set:
```
sudo mount /dev/sda5 /mnt
sudo mkdir /mnt/home
```
Reboot, and let me know what happens. :)

---

### Post by caljohnsmith on 2008-11-25
> **orodoni_le said:**
> I also try to move my /home to my WinXP documents partition, so I could share files from both OS (dualboot). I used this procedure to copy the files from the old /home to the NTFS partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

As far as I know, trying to put your entire /home directory on an NTFS partition will unfortunately not work, because NTFS does not support file permissions nor ownership. If you want to keep your personal documents in Win XP, I would recommend keeping your /home directory in the main Ubuntu partition, and then you can use a symbolic link to link from your "My Documents" folder in Windows (or you can link directly to "My Pictures", "My Music", etc) to your Ubuntu home directory. If you want specific help with that, then please post:
```
sudo fdisk -lu
```
And identify your partitions, and also post your /etc/fstab. We can work from there if you want. :)

---

### Post by Jimmy9pints on 2008-11-25
> **caljohnsmith said:**
> I'm sorry, that was my mistake with that very last command to make a new /home directory (I just now corrected my previous post); you don't have to redo any of the previous commands though, just go ahead and do the following from your Live CD, and I think you should be all set:
```
sudo mount /dev/sda5 /mnt
sudo mkdir /mnt/home
```
Reboot, and let me know what happens. :)

We may have won! I am writing this after successfully logging in. 

But just using the GUI file browser to look around I click on the ~15GB partition (sda8 ) and go straight into /home/james ! Sweet! But then I go into the ~6GB partition (which is the main parition, sda5), i see the mount point is / and I see home_backup_old (what I expect) but I also see home. Inside that folder there is the same as what is on sda8. 

Is that meant to be like that?
How do I know that Ubuntu isn't just reading the home directory from sda5?

Thanks again,

James.

---

### Post by caljohnsmith on 2008-11-25
> **Jimmy9pints said:**
> We may have won! I am writing this after successfully logging in. 

But just using the GUI file browser to look around I click on the ~15GB partition (sda8) and go straight into /home/james ! Sweet! But then I go into the ~6GB partition (which is the main parition, sda5), i see the mount point is / and I see home_backup_old (what I expect) but I also see home. Inside that folder there is the same as what is on sda8. 

Is that meant to be like that?
How do I know that Ubuntu isn't just reading the home directory from sda5?

Thanks again,

James.
Yes, it's meant to be like that. :) What you did is mount the sda8 partition (your /home directory) on the /home directory in your main Ubuntu sda5 partition (by putting it in /etc/fstab); therefore, you can manually browse to the sda8 partition and see your home directory there, or you can just go into your /home directory in sda5--it's the same thing. Also, you can know that Ubuntu isn't just reading the home directory of sda5 by doing:
```
mount
```
And that will show that /dev/sda8 is mounted on /home. If you boot your Live CD again and mount your sda5 partition and look in the /home directoy:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt/home
```
You should see that sda5's /home is empty. Anyway, cheers and have fun with Ubuntu. :)

---

### Post by Jimmy9pints on 2008-11-25
You are right!
```
james@james-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda6 on /media/windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/otherstuff type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda8 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
```

It's ok right? 

Thank you so much!

By the way, now I have the home directory on a seperate partition I can easily do a clean install of intrepid, but I would like to ask if I can install other distros too. Besides Ubuntu and its derivatives I would like to try Puppy Linux, Dam Small Linux, OpenSuse and Gentoo.

I won't rush to try them all but I just want to know with the partitions arranged in such a way would it work out?

Cheers,

James

---

### Post by caljohnsmith on 2008-11-25
> **Jimmy9pints said:**
> 
It's ok right? 

Yes, looks just fine to me. :)
> **Jimmy9pints said:**
> 
By the way, now I have the home directory on a seperate partition I can easily do a clean install of intrepid, but I would like to ask if I can install other distros too. Besides Ubuntu and its derivatives I would like to try Puppy Linux, Dam Small Linux, OpenSuse and Gentoo.

I won't rush to try them all but I just want to know with the partitions arranged in such a way would it work out?

Yes, you could install a few other distros if you want, but you are limited by your 60 GB HDD. Are you planning on using the space from the NTFS sda6 partition? That could work. When you install the other distros though, keep in mind that if you don't change their defaults, they usually install their own boot loader to the MBR (Master Boot Record) of your HDD and take over the booting process. I would recommend letting Ubuntu stay in charge of the booting process, and then add the other distros to your Ubuntu menu.lst. To do that, when you install the other distros, let them install their own boot loader, but specify to have their boot loader installed to the boot sector of their own partition rather than the MBR. Then it is easy to add them to your Ubuntu menu.lst. 

For example, when you install Ubuntu, at the last stage if you click on the "advanced" button, you can tell the installer to install Grub to say /dev/sda5 (if sda5 is the partition you are installing Ubuntu to), and then Grub will be installed to the boot sector of sda5 rather than the MBR. So say if you install OpenSUSE to sda6, you can then boot it from your Ubuntu menu.lst with:
```
title OpenSUSE
configfile (hd0,5)/boot/grub/menu.lst
```
Note (hd0,5) is sda6. That's the general idea, but if you have more specific questions, let me know. :)

---

### Post by Jimmy9pints on 2008-11-25
Helpful and knowledgeable as always!

Yes, I'll get rid of that old windows partition in the near future and work from there. 

Thanks,

James.

---

